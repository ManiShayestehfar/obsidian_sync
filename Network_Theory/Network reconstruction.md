---
tags: [inference]
---

# Network reconstruction

An observed network may omit links, and measurements of vertex activity may reveal no links directly. Reconstruction asks what structure is supported by those observations. We first study missing-link ranking; [[Reconstruction from node activity]] treats the second problem.

## Data, candidate pairs and scores

> [!definition] Link prediction
> Let $G_o=(V,E_o)$ be an observed subgraph of an unknown graph on a known vertex set. Rank the $\binom N2-|E_o|$ unobserved dyads for being missing edges. Future-link prediction is a related task with a different observation mechanism and temporal split.

Three approaches recur throughout the course: heuristic scores use graph statistics; representations place vertices in a feature space; generative inference assigns probabilities through a model. A ranking score need not be a calibrated edge probability.

For neighbours and degrees measured in the **training graph**, use:

| Score | Formula | Reason for a high score |
| --- | --- | --- |
| Common neighbours | $|\Gamma(i)\cap\Gamma(j)|$ | Triangle closure |
| Jaccard | $|\Gamma(i)\cap\Gamma(j)|/|\Gamma(i)\cup\Gamma(j)|$ | Large relative overlap |
| Resource allocation | $\sum_{v\in\Gamma(i)\cap\Gamma(j)}1/k_v$ | Common neighbours that are not hubs |
| Adamic–Adar | $\sum_{v\in\Gamma(i)\cap\Gamma(j)}1/\log k_v$ | A weaker penalty for common hubs |
| Preferential attachment | $k_i k_j$ | Popular endpoints |

Set an empty-union Jaccard score to zero by convention. In a simple loop-free graph a common neighbour of distinct vertices has degree at least two, so its Adamic–Adar logarithm is positive.

## Evaluate a ranking without leaking the test edges

> [!algorithm] The tutorial’s split protocol
> 1. Remove $\lfloor0.1L\rfloor$ true edges, preserving all vertices; these are the test positives.
> 2. Sample test negatives from non-edges of the **original** graph, so a removed edge cannot become a negative.
> 3. Compute every feature, embedding and fitted partition using the edge-deleted training graph only.
> 4. Evaluate the same candidate pairs for all methods and repeat seeded splits. Report mean and variability.
>
> A balanced positive/negative sample is convenient but is not required for ROC-AUC. Selecting a model or dimension and reporting performance on the same splits can be optimistic; use separate validation/test data for a final predictive claim.

> [!definition] ROC and AUC
> At a score threshold, $\mathrm{TPR}=\mathrm{TP}/(\mathrm{TP}+\mathrm{FN})$ and $\mathrm{FPR}=\mathrm{FP}/(\mathrm{FP}+\mathrm{TN})$. Varying the threshold traces a ROC curve. With the usual linear interpolation at ties,
> $$\mathrm{AUC}=\Pr(S_+>S_-)+\tfrac12\Pr(S_+=S_-).$$
> AUC measures ordering across classes; it does not measure probability calibration or precision among only the top-ranked candidates.

**Why ties count half.** A tied positive/negative pair has no ordering information. Randomly breaking the tie gives the positive precedence with probability $1/2$, producing the stated contribution. A constant-score model consequently has AUC exactly $1/2$ whenever both classes are present.

> [!code]- One matched evaluation split
> ```python
> import networkx as nx
> import numpy as np
> from sklearn.metrics import roc_auc_score
>
> G = nx.karate_club_graph()
> rng = np.random.default_rng(2025)
> edges, absent = list(G.edges()), list(nx.non_edges(G))
> m = max(1, int(0.1 * len(edges)))
> positive = [edges[i] for i in rng.choice(len(edges), m, replace=False)]
> negative = [absent[i] for i in rng.choice(len(absent), m, replace=False)]
> train = G.copy()
> train.remove_edges_from(positive)
> pairs = positive + negative
> y = np.r_[np.ones(m), np.zeros(m)]
> methods = {'Jaccard': nx.jaccard_coefficient,
>            'Adamic-Adar': nx.adamic_adar_index,
>            'Resource allocation': nx.resource_allocation_index,
>            'Preferential attachment': nx.preferential_attachment}
> auc = {name: roc_auc_score(y, [s for _, _, s in method(train, pairs)])
>        for name, method in methods.items()}
> print(auc)
> ```
> Repeat the split to compare methods; a ranking on one split can change substantially on another.

## Model-based and spectral predictions

For an SBM partition fitted on the training graph, candidate vertices in blocks $r,s$ receive the block-density score $\widehat p_{rs}=l_{rs}/y_{rs}$. With $B=1$, every candidate receives the same score: **AUC is $0.5$ because all positive/negative comparisons are tied**, not because the model predicts half the edges correctly.

![[Assets/tutorial-9-cell-27-plot-1.png|650]]
*Supplied Tutorial 9, cell 27: mean and SD over six matched splits of a planted three-block graph. The largest displayed mean is at $B=4$ (about $0.862$), not the planted $B=3$. The heuristic means in cell 12 are about $0.732$ or lower for this instance.*

This example shows that predictive performance need not identify the generating block count. The differences between nearby $B$ values overlap in the displayed variability; do not treat the maximum curve point as decisive model evidence.

Spectral prediction instead scores $-\|v_i-v_j\|^2$ using a Laplacian embedding of the training graph. The sign ensures nearby vertices rank higher. See [[Spectral graph theory]] for the full construction, dimension choice and treatment of disconnected training graphs.

For Bayesian reconstruction, integrate over parameter uncertainty and the observation mechanism. Sampling unconstrained graphs from a fitted model does not automatically condition them on the observed edges. Distinguish a fitted edge-density score from a posterior probability that an unobserved dyad is truly an edge.

## For revision

- State where positives and negatives come from and which graph supplies the features.
- Explain AUC in terms of positive/negative comparisons, including $B=1$ ties.
- Distinguish heuristic, spectral and probabilistic reconstruction. Revisit [[Stochastic block models]] for the fitted block densities.

> [!reference]- Sources
> Lecture Week 9 pp.1–10; Tutorial 9 §§1.1–1.4 and Ex.1.1–1.4. The numerical comparisons and figure are supplied notebook results, not newly rerun experiments. Jenny’s notes Week 9. Newman §7.6 and Chapter 9 give similarity/observation-error context; block inference is covered in §14.4.
