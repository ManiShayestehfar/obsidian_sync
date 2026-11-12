---
tags: [data5441, ch09, inference]
aliases: [Network reconstruction, Missing links, AUC, ROC, Common neighbours, Jaccard]
---
# Link prediction

> [!abstract] Summary
> An observed graph $g_o$ contains **some**, but not necessarily all, links of a true graph $g$. **Link prediction** ranks the currently absent pairs by how likely they are to be missing edges. Week 9 compares three approaches: **heuristic** (hand-designed scores from network features), **inferential** (fit a generative model, especially an SBM), and **embedding-based** (place nodes in a low-dimensional space using the Laplacian). Evaluate each on **held-out original links**, using ROC–AUC and no information leakage.
> Chapter: [[Ch09 Network reconstruction]] · Sources: DATA5441 **Week 9**, lecture pp. 113–122; Tutorial 9, §1.

## 1. Problem and the three approaches

> [!definition] Link prediction from partial network observation
> Let $g=(V,E)$ be the (unknown) true graph and $g_o=(V,E_o)$ its observed subgraph, where $E_o\subseteq E$. On $N$ nodes, $Y=\binom N2$ pairs are possible, and $L_o=|E_o|$ are already observed.
>
> **Task:** give each currently unobserved pair $\{i,j\}\notin E_o$ a score $s_{ij}$ and **rank** the $Y-L_o$ candidates. A higher score indicates a more plausible missing link; it **need not** be a probability.

| Approach | Main question | Input used | Output |
|---|---|---|---|
| **Heuristic** | “What simple pattern makes two nodes likely to link?” | Neighbours, degrees in $g_o$ | Hand-designed score $s_{ij}$ |
| **Inferential** | “What generative graph model could have produced $g_o$?” | Fitted model parameters/blocks | Predicted link probability (or model-averaged score) |
| **Embedding-based** | “Where do nodes sit in a low-dimensional geometric representation?” | Spectral eigenvectors of $g_o$ | Similarity/distance score |

**Distinguish this problem from §2 of Tutorial 9:** in [[Reconstruction from node activity]], **edges are hidden altogether** and the data are *node-state observations*, not a partially observed edge list.

![[Assets/w9-three-approaches.png|760]]

## 2. Heuristic link-prediction scores

Let $\Gamma(i)=\{k:A_{ik}=1\}$ be the neighbours of $i$ in the **observed/training graph**, and let $z_i=|\Gamma(i)|$.

| Method | Score $s_{ij}$ | What it assumes |
|---|---|---|
| **Common neighbours** | $|\Gamma(i)\cap\Gamma(j)|$ | Many shared friends suggest triangle closure |
| **Jaccard** | $\dfrac{|\Gamma(i)\cap\Gamma(j)|}{|\Gamma(i)\cup\Gamma(j)|}$ | Normalised overlap; penalises large neighbourhoods |
| **Resource allocation** | $\displaystyle\sum_{k\in\Gamma(i)\cap\Gamma(j)}\frac1{z_k}$ | A low-degree common neighbour is more informative |
| **Adamic–Adar** | $\displaystyle\sum_{k\in\Gamma(i)\cap\Gamma(j)}\frac1{\ln z_k}$ | Similar, but a milder penalty for common hubs |
| **Preferential attachment** | $z_iz_j$ | Large-degree nodes are more likely to connect |

> [!example] Read the scores rather than memorising names
> Suppose $i$ has 5 neighbours, $j$ has 4, and they share 2. Then
> $$s_{\rm CN}=2,\qquad s_{\rm Jaccard}=\frac{2}{5+4-2}=\frac27,\qquad s_{\rm PA}=5\cdot4=20.$$
> For common neighbours $k$ of degrees $2$ and $10$, resource allocation is $\tfrac12+\tfrac1{10}=0.6$. Shared *hubs* contribute less. All methods return **scores**, not automatically probabilities.

> [!remark] When heuristics work poorly
> Shared-neighbour methods rely on **local clustering/triangle closure**; they struggle when informative connections are long-range or across disassortative groups. Preferential attachment responds to **degree**, not shared-neighbour structure. Neither method infers blocks or learns a network-wide geometry.

## 3. Inferential link prediction: fit a random-graph model

> [!definition] Model-based inference
> Specify a generative family $P(g\mid\theta)$, **fit $\theta$ from $g_o$**, and use the fitted model to predict the probability that a candidate edge exists. Examples include ER models, [[Stochastic block models|SBMs]], and more general ERGMs. This models *how graph links arise*, rather than relying on an ad hoc local score.

> [!algorithm] SBM link prediction (Tutorial 9)
> 1. Choose a number of blocks $B$.
> 2. **Infer** a partition $\hat{\mathbf b}$ from the **training graph only** (e.g. greedy fitted-SBM likelihood search from Week 7).
> 3. For each block pair $r,s$, count training edges $l_{rs}$ and possible edges $y_{rs}$; fit $\hat p_{rs}=l_{rs}/y_{rs}$.
> 4. Give a candidate pair $(i,j)$ the score
>    $$\boxed{s_{ij}=\hat p_{\hat b_i\hat b_j}.}$$
> 5. Rank all candidates; repeat the **whole fitting procedure** for each train/test split and each trial $B$.
>
> **Why it works:** two nodes can have **no common neighbours** and still score highly if their inferred blocks have high mutual link probability. The method captures **meso-scale structure**.

> [!exam] Why exactly $\mathrm{AUC}=0.5$ for SBM with $B=1$?
> With only one block, $\hat p_{11}=L_o/\binom N2$ is the **same for every candidate**. AUC compares one held-out link to one genuine non-link. They *always tie*, so
> $$\mathrm{AUC}=\Pr(s_+>s_-)+\tfrac12\Pr(s_+=s_-)=0+\tfrac12\cdot1=\boxed{0.5}.$$
> This remains true regardless of the fitted edge probability: **constant scores cannot rank links**.

> [!remark] A fitted SBM and a posterior average are not the same
> Tutorial 9 uses **plug-in probabilities** $\hat p_{\hat b_i\hat b_j}$ from a single fitted partition. A fuller inferential method could average link predictions across uncertain partitions and model parameters, but that is **not** what the provided exercise computes.

## 4. Embedding: Laplacian spectral link prediction

> [!definition] Low-dimensional node representation
> Form the Laplacian $\mathcal L=D-A$ of $g_o$ and compute its smallest eigenvectors. For a **connected** training graph, discard the constant eigenvector $u_1$ and give node $i$ coordinates
> $$v_i=(u_2(i),\ldots,u_{d+1}(i))\in\mathbb R^d.$$
> Nodes joined within dense or nearly disconnected groups tend to be **nearby** in this embedding. Score an absent pair by
> $$\boxed{s_{ij}=-\|v_i-v_j\|^2.}$$
> Higher score (less negative) $\Longleftrightarrow$ smaller distance $\Longleftrightarrow$ predicted link is more likely.

> [!algorithm] Spectral prediction procedure (Tutorial 9)
> 1. Remove the held-out edges. Compute $\mathcal L$ **on $g_o$, not on $g$**.
> 2. Compute the ordered Laplacian eigenpairs. For a connected graph, ignore $u_1$; choose $d$ non-trivial directions.
> 3. Embed each node as a **row of eigenvector coordinates** and compute the negative squared distance for each test pair.
> 4. Compute AUC and repeat across splits; assess $d\in\{1,2,3,4,5\}$ separately.
>
> **Disconnected graph subtlety:** the *actual* Tutorial 9 implementation includes **all zero-eigenvalue modes** (component information) and then the first $d$ **positive** modes. Thus the displayed simple formula is for connected training graphs. See [[Spectral graph theory]].

> [!remark] Three parameters that mean different things
> $B$ in an SBM = **number of blocks**. $d$ in a spectral embedding = **number of retained eigenvector directions**. Neither is an edge probability. An ideal $B$-component graph has $B-1$ non-constant component directions, explaining the useful heuristic $d=B-1$ in such cases.

## 5. Evaluation: ROC and AUC without leakage

> [!algorithm] Fair train/test protocol (Tutorial 9)
> 1. Begin with the original graph $g$ (known **only for benchmarking**). Randomly remove approximately **10% of its edges**. These are **positive test pairs**; the remainder form $g_o$.
> 2. Sample an equal number of **negative test pairs** from the **non-edges of the original graph** (not merely non-edges of $g_o$, which include the removed positives).
> 3. For each method, **recompute all features, partitions, parameters and embeddings from $g_o$ alone**.
> 4. Score the same held-out positive and negative pairs; compute ROC–AUC.
> 5. Repeat over several seeded splits, reporting **mean and standard deviation**. Use matched splits for method comparisons; ideally tune $B$ and $d$ with *separate* validation data.

> [!definition] ROC and AUC *(critical for the exam)*
> A threshold on a ranking score gives predictions of “link” versus “non-link”. Then
> $$\mathrm{TPR}=\frac{TP}{TP+FN},\qquad \mathrm{FPR}=\frac{FP}{FP+TN}.$$
> The ROC curve plots $\mathrm{TPR}$ against $\mathrm{FPR}$ across thresholds; its area is AUC. Equivalently,
> $$\boxed{\mathrm{AUC}=\Pr(s_+>s_-)+\frac12\Pr(s_+=s_-).}$$
> - **AUC $=1$:** every test link is ranked ahead of every non-link.
> - **AUC $=0.5$:** no ranking discrimination (e.g. constant scores; the random baseline).
> - AUC assesses **ranking**, not probability calibration, precision among the top few links, or causal reconstruction.

![[Assets/w9-roc-explained.png|680]]

## 6. What the tutorial actually finds

> [!exam] Synthetic three-block SBM: **best $B$ need not equal planted $B$**
> Tutorial 9 uses block sizes $(20,40,20)$ and
> $$P=\begin{pmatrix}0.20&0.01&0.01\\0.01&0.15&0.01\\0.01&0.01&0.50\end{pmatrix}.$$
> Over six matched splits, the recorded mean AUCs are: **heuristics** Jaccard $0.732$, Adamic–Adar $0.726$, resource allocation $0.720$, preferential attachment $0.559$; **SBM** $B=1$: $0.500$, $B=3$: $0.851$, $B=4$: $0.862$; **spectral $d=2$**: $0.848$. The highest *mean* among the tested SBM values is **$B=4$**, despite planted $B=3$; its advantage over $B=3$ is small relative to split variability. **Prediction quality does not certify the true generative partition.**

![[Assets/w9-sbm-auc.png|690]]

> [!remark] Karate Club spectral results
> The supplied Tutorial 9 reports **mean AUC $0.629$, SD $0.228$** for $d=2$ over six edge-removal splits of Karate Club. This is far more variable than the same spectral method on the synthetic SBM (**$0.848\pm0.054$**). A larger $d$ is not automatically better; choose using held-out evidence, not the true graph used in training.

> [!code]- Minimal score/evaluation calls (Tutorial 9)
> ```python
> # Input G_train and candidate test_pairs=(u,v); both known at scoring time.
> jaccard_scores = [s for _, _, s in nx.jaccard_coefficient(G_train, test_pairs)]
> ra_scores = [s for _, _, s in nx.resource_allocation_index(G_train, test_pairs)]
> aa_scores = [s for _, _, s in nx.adamic_adar_index(G_train, test_pairs)]
> pa_scores = [s for _, _, s in nx.preferential_attachment(G_train, test_pairs)]
> from sklearn.metrics import roc_auc_score
> auc = roc_auc_score(y_true, jaccard_scores)  # y_true: 1 removed edge, 0 true non-edge
> ```

> [!selftest]- Self-test
> 1. **Heuristic vs inferential vs embedding?** — Hand-built structural score vs generative model probability vs low-dimensional node similarity.
> 2. **Why $B=1$ gives AUC $0.5$?** — All candidate edges receive equal scores; all positive-negative comparisons tie.
> 3. **Why negatives from original graph?** — Non-edges of the training graph contain held-out *true links*.
> 4. **Why can $B=4$ beat the planted $B=3$ for AUC?** — AUC measures finite-sample prediction under an imperfect fitting procedure, not recovery of the true model.

---
Related: [[Reconstruction from node activity]] · [[Stochastic block models]] · [[Spectral graph theory]] · [[Community detection]]
