---
tags: [data5441, ch09, inference]
aliases: [Network reconstruction, Missing links, AUC, ROC, Common neighbours, Jaccard]
---
# Link prediction

> [!abstract] Summary
> Given an incomplete network, rank the unobserved pairs by how likely they are to be missing links. There are three families: heuristic scores, model-based inference (SBM), and embeddings (spectral). Methods are compared by AUC on held-out links, computed without leaking the test links.
> Chapter: [[Ch09 Network reconstruction]]

> [!definition] Link-prediction problem
> We observe $g_o\subseteq g$ on the known node set. Assign a score to each of the $Y-L_o$ non-observed pairs. A high score means "likely a missing link". A score ranks pairs; it need not be a calibrated probability.

## Heuristic scores
Neighbourhoods and degrees are measured in the training graph.

| Score | $s_{ij}$ | Idea |
|---|---|---|
| Common neighbours | $\lvert\Gamma(i)\cap\Gamma(j)\rvert$ | triangle closure |
| Jaccard | $\dfrac{\lvert\Gamma(i)\cap\Gamma(j)\rvert}{\lvert\Gamma(i)\cup\Gamma(j)\rvert}$ | relative overlap |
| Resource allocation | $\sum_{v\in\Gamma(i)\cap\Gamma(j)}1/z_v$ | penalise shared hubs |
| Adamic–Adar | $\sum_{v\in\Gamma(i)\cap\Gamma(j)}1/\ln z_v$ | milder hub penalty |
| Preferential attachment | $z_iz_j$ | hubs link to hubs |

## Inferential and embedding methods

> [!definition] SBM score
> Fit an SBM to the training graph and score $(i,j)$ by $\hat p_{b_ib_j}=l_{rs}/y_{rs}$; see [[Stochastic block models]].
> With $B=1$ every pair gets the same score, so $\mathrm{AUC}=0.5$ exactly: all comparisons are ties.

> [!definition] Laplacian-embedding score
> $s_{ij}=-\|v_i-v_j\|^2$ with $v_i$ the $d$-dimensional Laplacian embedding; see [[Spectral graph theory]].

## Evaluation

> [!algorithm] Train/test protocol (tutorial 9)
> 1. Remove a random $10\%$ of the links: these are the test **positives**. Keep all nodes.
> 2. Sample test **negatives** from the non-links of the **original** graph.
> 3. Compute every score from the training graph only (no leakage).
> 4. Use the same splits for all methods, and repeat over seeds (report mean ± sd).

> [!definition] ROC curve and AUC
> At a threshold, $\mathrm{TPR}=\dfrac{TP}{TP+FN}$ and $\mathrm{FPR}=\dfrac{FP}{FP+TN}$. Varying the threshold traces the ROC curve.
> $$\mathrm{AUC}=\Pr(s_+>s_-)+\tfrac12\Pr(s_+=s_-),$$
> where $s_+$ and $s_-$ are the scores of a random positive and a random negative.
> - $1$: perfect ranking.
> - $0.5$: random or constant scores.

> [!proof]- Why ties count ½
> A tied positive–negative pair carries no ordering information. Breaking the tie at random puts the positive first with probability $1/2$.

> [!remark] Lessons from tutorial 9
> On a planted $3$-block SBM, the best AUC occurred at $B=4$, not $B=3$. Predictive performance need not identify the true model, and nearby $B$ values overlap within their error bars. Choosing $B$ or $d$ on the same splits used for reporting is optimistic.

> [!code]- NetworkX heuristics
> ```python
> nx.jaccard_coefficient(G_train, pairs); nx.adamic_adar_index(G_train, pairs)
> nx.resource_allocation_index(G_train, pairs); nx.preferential_attachment(G_train, pairs)
> from sklearn.metrics import roc_auc_score; roc_auc_score(y_true, scores)
> ```

> [!selftest]- Self-test
> 1. Which can be used for link prediction: Laplacian spectral methods, WS, Jaccard, SBM, threshold model? — Spectral, Jaccard and SBM.
> 2. What AUC does a constant score give? — $0.5$.
> 3. Name one source of leakage. — Computing features on the full graph.

---
Related: [[Reconstruction from node activity]] · [[Stochastic block models]] · [[Spectral graph theory]]
