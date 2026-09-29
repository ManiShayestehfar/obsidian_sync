---
tags: [inference]
---

# Network reconstruction

Reconstruction infers missing structure from incomplete edges or vertex activity. It requires an observation model: an unobserved dyad is not automatically a true non-edge.

> [!definition] Link-prediction problem
> Given observed graph $G_o$ on a known vertex set, score candidate dyads absent from $G_o$ for being missing or future edges. Missing-edge recovery and future-link prediction are different tasks; their validation splits must reflect that distinction.

For distinct vertices $i,j$, use degrees and neighbour sets in the **training** graph:

| Score | Formula | Mechanism |
| --- | --- | --- |
| Common neighbours | $|\Gamma(i)\cap\Gamma(j)|$ | Triangle closure |
| Jaccard | $|\Gamma(i)\cap\Gamma(j)|/|\Gamma(i)\cup\Gamma(j)|$ | Normalised overlap |
| Resource allocation | $\sum_{v\in\Gamma(i)\cap\Gamma(j)}1/k_v$ | Strong penalty for common hubs |
| Adamic–Adar | $\sum_{v\in\Gamma(i)\cap\Gamma(j)}1/\log k_v$ | Weaker common-hub penalty |
| Preferential attachment | $k_i k_j$ | Endpoint popularity |

Use zero for Jaccard with empty union. In a simple loop-free graph, a common neighbour of distinct vertices has degree at least two, so the Adamic–Adar denominator is positive. These scores are generally rankings, not calibrated probabilities.

> [!algorithm] Evaluate without leakage
> Remove a chosen set of edges, retaining all vertices. Fit or score using only the remaining graph. Compare removed edges (positives) with known absent dyads (negatives). Repeat splits. For time prediction, split by time instead. If choosing hyperparameters such as block count by predictive performance, use a separate validation split before the final test.

ROC uses $\mathrm{TPR}=\mathrm{TP}/(\mathrm{TP}+\mathrm{FN})$ and $\mathrm{FPR}=\mathrm{FP}/(\mathrm{FP}+\mathrm{TN})$. AUC is the probability a random positive outranks a random negative, with half credit for ties. Random independent rankings have expected AUC $1/2$. State the negative-sampling scheme, and consider precision when true positives are rare.

> [!code] Hold out edges and compute Jaccard AUC
> ```python
> import networkx as nx
> import numpy as np
>
> G = nx.karate_club_graph()
> rng = np.random.default_rng(5441)
> edges = list(G.edges())
> indices = rng.choice(len(edges), size=8, replace=False)
> positive = [edges[i] for i in indices]
> negative = list(nx.non_edges(G))  # absent in the full evaluation graph
> train = G.copy()
> train.remove_edges_from(positive)
>
> def scores(pairs):
>     return np.array([s for _, _, s in nx.jaccard_coefficient(train, pairs)])
>
> pos, neg = scores(positive), scores(negative)
> auc = ((pos[:, None] > neg).mean()
>        + 0.5 * (pos[:, None] == neg).mean())
> print(auc)
> # Alternative generators on the same training graph:
> ra = list(nx.resource_allocation_index(train, positive))
> aa = list(nx.adamic_adar_index(train, positive))
> pa = list(nx.preferential_attachment(train, positive))
> ```
> This toy calculation uses all absent dyads; its pairwise AUC matrix is unsuitable for very large graphs. The full graph is used only to construct evaluation labels, not to compute predictor features.

## Generative reconstruction
An SBM supplies block-based edge probabilities, and an ERGM supplies a graph distribution. A posterior predictive edge probability averages over fitted uncertainty. Conditioning on the observed edges and their missingness mechanism is necessary for actual reconstruction; unconstrained draws from a fitted model do not automatically preserve the observations.

For activity data, correlations or mutual information can suggest candidate links but also reflect common causes and indirect paths. Similar activity is not by itself direct interaction.

> [!definition] Ising likelihood and its normaliser
> For binary states $s_i\in\{-1,1\}$ and energy $E_g(s)$, let $p(s\mid g)=e^{-E_g(s)}/Z(g)$ with $Z(g)=\sum_s e^{-E_g(s)}$. Under independent configurations $s^{(1)},\ldots,s^{(T)}$,
> $$-\log p(D\mid g)=\sum_{t=1}^T E_g(s^{(t)})+T\log Z(g).$$
> Because $Z$ generally depends on the graph, minimising observed energy alone is not maximum-likelihood graph reconstruction. Time-correlated observations require a different likelihood or a justified approximation.

See [[Statistical inference and model selection]] for posterior integration and [[Community detection]] for the distinction between recovering links and inferring groups.

> [!reference]- Sources
> Jenny’s notes Week 9, with corrected likelihood normalisation and validation interpretation. Newman §7.6 for similarity and Chapter 9 for observation error; these are context, not a claim that the book derives every reconstruction method here. [NetworkX link-prediction definitions](https://networkx.org/documentation/stable/_modules/networkx/algorithms/link_prediction.html). Current-course lecture/tutorial coverage after Week 7 was not supplied.
