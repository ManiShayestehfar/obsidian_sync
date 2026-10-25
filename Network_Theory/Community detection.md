---
tags: [inference]
---

# Community detection

A graph may contain groups whose vertices interact mainly with one another. The task is to turn that visual impression into an explicit objective, then distinguish a useful partition from a pattern produced by chance. The definition of “best” depends on the question: a balanced cut, high modularity and a good generative fit solve different problems.

## Partitions and balanced cuts

> [!definition] Community partition
> A partition $\mathcal P=\{V_1,\ldots,V_B\}$ consists of nonempty, pairwise disjoint subsets whose union is $V$. A community is an **assortative** group: within-group connection is stronger than an appropriate between-group or null-model baseline. An arbitrary partition need not have this property.
>
> For $B=2$, the cut size counts edges crossing from $V_1$ to $V_2$. Without size constraints, putting every vertex in one group makes the cut zero.

If $|V_1|=n_1$ is prescribed, there are $\binom N{n_1}$ labelled choices; when $n_1=N/2$, exchanging the two sides identifies pairs of choices. Large search spaces motivate approximation, but counting them alone is not a complexity-theoretic impossibility proof.

> [!algorithm] Kernighan–Lin: optimise a prescribed bisection
> 1. Start with two groups of the required sizes.
> 2. Choose an unlocked pair of vertices in opposite groups whose exchange gives the best cut improvement, allowing a temporary worsening.
> 3. Exchange and lock them; repeat until a pass is complete.
> 4. Retain the prefix of exchanges with the greatest cumulative improvement, if it improves the initial cut.
> 5. Repeat passes until no improvement occurs.
>
> Group sizes remain fixed. This method neither maximises modularity nor infers $B$. A claimed runtime depends on the implementation, not merely the algorithm’s name.

For an exchange of $a,b$, a useful gain expression is $D_a+D_b-2A_{ab}$, where $D_v$ is external minus internal degree before the exchange. The subtraction corrects the edge between the swapped vertices.

## Modularity: excess internal connection

> [!definition] Modularity
> For an unweighted undirected graph with $L>0$,
> $$Q_\gamma(b)=\frac1{2L}\sum_{ij}\left(A_{ij}-\gamma\frac{k_i k_j}{2L}\right)\mathbf1\{b_i=b_j\}.$$
> The resolution parameter is usually $\gamma=1$. The degree-product term is the objective’s null expectation, not an exact simple-edge probability.

> [!theorem] Blockwise formula and merge gain
> Let $l_r$ count internal edges and $K_r=\sum_{i\in V_r}k_i$. Then
> $$Q_\gamma=\sum_r\left[\frac{l_r}{L}-\gamma\left(\frac{K_r}{2L}\right)^2\right].$$
> If $l_{rs}$ edges join distinct groups $r,s$, merging them changes the objective by
> $$\Delta Q_\gamma=\frac{l_{rs}}L-\gamma\frac{K_rK_s}{2L^2}.$$

**Proof.** Summing adjacency within a block counts its edges twice, while the degree-product sum is $K_r^2$. For a merge, internal edges increase by $l_{rs}$ and the squared-degree term increases by $2K_rK_s$. Substitute. $\square$

At $\gamma=1$, a single group gives $Q=0$; singleton groups give $Q=-\sum_i(k_i/2L)^2<0$. Intermediate partitions can improve the score, but positive modularity is not guaranteed for every graph.

> [!algorithm] Greedy agglomeration
> Start with $N$ singleton groups. At each step choose the merge producing the largest $Q$ and retain that partition. To reproduce the tutorial’s entire curve, continue to one group **even when all remaining merges reduce $Q$**, then select the best partition along the path. Stopping at the first local optimum answers a different computational task.

![[Assets/tutorial-8-cell-44-plot-1.png|720]]
*Supplied Tutorial 8, cell 44: modularity along one greedy merge path for Karate Club. Its best point occurs at three groups. This is a heuristic path, not an exhaustive optimum over all partitions.*

## Other objectives and methods

| Method | Main operation | Interpretation |
| --- | --- | --- |
| Louvain | Vertex moves, then aggregation into supervertices | Multilevel modularity optimisation |
| Girvan–Newman | Repeatedly remove high **edge** betweenness links | Divisive hierarchy; recompute scores after cuts |
| Label propagation | Adopt a prevalent neighbouring label | Dynamical local grouping; ties/order matter |
| Infomap | Compress random-walk trajectories | Flow-based partitioning |
| Spectral clustering | Embed vertices using selected eigenvectors | A matrix relaxation; see [[Spectral graph theory]] |
| SBM inference | Fit a probabilistic block structure | Can describe assortative, disassortative and core–periphery structure |

> [!code]- Compare objectives on an unweighted graph
> ```python
> import networkx as nx
> G = nx.karate_club_graph()
> C = nx.community
> partitions = {
>     'Kernighan-Lin': list(C.kernighan_lin_bisection(G, weight=None, seed=13)),
>     'greedy': list(C.greedy_modularity_communities(G, weight=None)),
>     'Louvain': C.louvain_communities(G, weight=None, seed=13),
>     'label propagation': list(C.asyn_lpa_communities(G, weight=None, seed=13)),
> }
> for name, groups in partitions.items():
>     assert C.is_partition(G, groups)
>     print(name, len(groups), C.modularity(G, groups, weight=None))
> ```
> `weight=None` matters: NetworkX’s Karate graph carries interaction weights. Fix the convention before comparing algorithms or notebook outputs.

## What the tutorial experiments teach

A binary partition is unchanged by exchanging its two labels. If two label vectors differ at $d$ vertices, the minimum number of reassignments is $\min(d,N-d)$. For more groups, match labels through a contingency table rather than comparing colours directly.

ER graphs can return multiple communities and positive optimised modularity even though their generating law has no planted blocks. Optimisation searches many fluctuations. Trends in returned $B$ versus $N$ are experimental observations, not universal laws for those algorithms.

The five-block experiment sets $n_r=50$, $p_{rr}=0.2-q$ and $p_{rs}=q$ for $r\ne s$. It is assortative for $q<0.1$, homogeneous ER at $q=0.1$, and disassortative for $q>0.1$. Its expected degree is $49(0.2-q)+200q=9.8+151q$, so the sweep changes density as well as block contrast. At $q=0.15$, a modularity method can return an assortative partition even though the planted blocks are disassortative: it is optimising a different structure.

## For revision

- Separate fixed-size bisection, modularity optimisation and probabilistic inference.
- Derive the blockwise modularity formula and explain the all-in-one and singleton cases.
- Explain why finding a partition does not establish statistically significant communities. Use [[Stochastic block models]] and [[Statistical inference and model selection]] for the generative comparison.

> [!reference]- Sources
> Lecture Week 8 pp.1–8, 12; Tutorial 8 §§1–3, especially Ex.2.1–2.2 and 3.1–3.2. Jenny’s notes Week 8. Newman (2018), §§14.1–14.6. The merge-gain identity is derived above. Notebook plots are supplied outputs, not newly reproduced experiments.
