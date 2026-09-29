---
tags: [inference]
---

# Community detection

Communities are groups with relatively dense internal connection patterns. Finding an attractive partition and demonstrating statistically meaningful group structure are different tasks. A core–periphery pattern need not be a set of assortative communities.

> [!definition] Cut size and modularity
> A two-way cut counts edges crossing between groups. Without size or balance constraints, minimising it admits the trivial one-group answer.
>
> For a simple undirected graph with $L>0$, modularity at resolution $\gamma>0$ is
> $$Q_\gamma(b)=\frac1{2L}\sum_{i,j}\left(A_{ij}-\gamma\frac{k_i k_j}{2L}\right)\mathbf1\{b_i=b_j\}.$$
> The degree-product term is a null expectation in this objective, not an exact simple-edge probability. Standard modularity uses $\gamma=1$.

> [!theorem] Blockwise modularity
> If $l_r$ counts internal edges and $K_r=\sum_{i:b_i=r}k_i$, then
> $$Q_\gamma=\sum_r\left[\frac{l_r}{L}-\gamma\left(\frac{K_r}{2L}\right)^2\right].$$

> [!proof]
> Within block $r$, summing adjacency counts each internal edge twice, whereas $\sum_{i,j\in r}k_ik_j=K_r^2$. Substitute and divide by $2L$. For $\gamma=1$, one group gives zero; singleton groups give $-\sum_i(k_i/2L)^2\le0$.

## Algorithms and their objectives

| Method | Operation | What to watch |
| --- | --- | --- |
| Kernighan–Lin | Swap vertices across a prescribed two-way split, retain the best cumulative improvement | Size constraints and implementation determine the problem/cost |
| Greedy modularity | Merge groups with greatest improvement, retaining the best partition | Local decisions can miss the optimum |
| Louvain | Improve modularity by vertex moves, then aggregate groups and repeat | Resolution, ordering and random seed matter |
| Girvan–Newman | Remove high **edge** betweenness links, recomputing scores | Removes edges, not high-betweenness vertices |
| Label propagation | Vertices adopt a frequent neighbouring label | Update order, ties and stopping rule matter |
| Infomap | Compress random-walk trajectories using a partition | A flow/compression objective rather than modularity |
| Spectral methods | Embed using informative matrix eigenvectors, then partition | Choice of matrix and eigengap matter |
| SBM inference | Fit a probabilistic block structure | Model assumptions and complexity control matter |

An exhaustive partition count does not itself prove an algorithmic lower bound. Claims such as “all greedy methods cost $O(N^2)$” or “checking all divisions is polynomial” require an actual implementation analysis; all possible bipartitions of one group are already exponentially numerous.

> [!code] Compare several partitioning rules
> ```python
> import networkx as nx
>
> G = nx.karate_club_graph()
> comm = nx.community
> partitions = {
>     'greedy modularity': list(comm.greedy_modularity_communities(G, weight=None)),
>     'Louvain': comm.louvain_communities(G, weight=None, seed=5441),
>     'label propagation': list(comm.asyn_lpa_communities(G, weight=None, seed=5441)),
>     'Kernighan-Lin': list(comm.kernighan_lin_bisection(G, weight=None, seed=5441)),
>     'Girvan-Newman first split': list(next(comm.girvan_newman(G))),
> }
> for name, groups in partitions.items():
>     print(name, len(groups), comm.modularity(G, groups, weight=None))
> ```
> The graph’s supplied edge weights are deliberately ignored. Similar modularity scores need not imply the same partition or objective.

> [!warning] Optimisation can find apparent structure in noise
> Even a random graph can have a partition with positive modularity after searching many possibilities. The null expectation for a fixed partition does not account for selection of the best one. Modularity also has a resolution scale and can merge smaller groups. A returned partition is therefore not a calibrated significance test.

Use [[Stochastic block models]] for a generative alternative, [[Statistical inference and model selection]] for complexity and evidence, and [[Spectral graph theory]] for the matrix foundations. Conclusions about a “best” method depend on whether the aim is prediction, compression, a balanced cut or recovery of a particular kind of structure.

> [!reference]- Sources
> Jenny’s notes Week 8; Lecture Week 7 for the block-model contrast. Newman §§14.1–14.6. [NetworkX community algorithms](https://networkx.org/documentation/stable/reference/algorithms/community.html), including the Girvan–Newman definition. Current-course lecture/tutorial coverage after Week 7 was not supplied.
