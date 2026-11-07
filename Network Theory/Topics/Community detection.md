---
tags: [data5441, ch08, inference]
aliases: [Modularity, Louvain, Kernighan–Lin, Graph partitioning, Girvan–Newman]
---
# Community detection

> [!abstract] Summary
> Communities are groups with more internal links than expected. Methods differ in their objective: a balanced cut (Kernighan–Lin), modularity (greedy, Louvain), a generative fit (SBM) or a spectral relaxation. Heuristics find good partitions, not proven optima. Modularity even finds "communities" in ER graphs.
> Chapter: [[Ch08 Community detection]]

## Graph partitioning

> [!definition] Partition and cut size
> A partition $\{V_1,\dots,V_B\}$ is a set of non-empty, disjoint node sets covering all nodes. For $B=2$, the **cut size** $R$ is the number of links between $V_1$ and $V_2$. Minimising $R$ without size constraints is trivial: put all nodes in one group, so $R=0$. Partitioning therefore fixes the group sizes.

> [!algorithm] Kernighan–Lin bisection
> 1. Start from a bisection with the prescribed sizes $n_1,n_2$.
> 2. Repeatedly swap the unlocked pair $(a\in V_1,b\in V_2)$ that most reduces the cut, even if the change is negative, then lock both nodes.
> 3. After all nodes are locked, keep the best intermediate state of the pass.
> 4. Repeat passes until no improvement.
>
> It keeps the group sizes fixed. It neither maximises modularity nor chooses $B$.

## Modularity

> [!definition] Modularity *(formula sheet)*
> $$Q=\frac1{2L}\sum_{i,j}\Big(A_{ij}-\frac{z_iz_j}{2L}\Big)\delta_{b_i,b_j}.$$
> $Q$ is (fraction of links inside groups) minus (the expected fraction under the degree-preserving null, $z_iz_j/2L$); see [[Configuration model]].

> [!theorem] Group form and merge gain
> Let $l_r$ be the number of links inside group $r$ and $K_r=\sum_{i\in r}z_i$. Then
> $$Q=\sum_r\Big[\frac{l_r}{L}-\Big(\frac{K_r}{2L}\Big)^2\Big],\qquad \Delta Q_{r\cup s}=\frac{l_{rs}}{L}-\frac{K_rK_s}{2L^2},$$
> where $l_{rs}$ is the number of links between groups $r$ and $s$.

> [!proof]-
> $\sum_{i,j\in r}A_{ij}=2l_r$ and $\sum_{i,j\in r}z_iz_j=K_r^2$; divide by $2L$.
> Merging $r$ and $s$ adds $l_{rs}$ internal links, and $(K_r+K_s)^2-K_r^2-K_s^2=2K_rK_s$. $\square$

> [!proposition] Reference values
> - One group: $Q=0$, since $l=L$ and $K=2L$.
> - All singletons: $Q=-\sum_i(z_i/2L)^2<0$.
> - Always $Q<1$.

> [!algorithm] Modularity heuristics
> - **Greedy agglomerative:** start from $N$ singletons, merge the pair with the largest $\Delta Q$, continue to one group, and keep the best $Q$ along the path. It is bottom-up and cannot undo merges.
> - **Greedy divisive:** start from one group and split with Kernighan–Lin bisections, keeping the split with the best $Q$. It is top-down and cannot undo splits.
> - **Louvain:** move single nodes to the neighbouring group with the best $\Delta Q$, then aggregate groups into super-nodes, and repeat. It is fast and multilevel.
> - **Other approaches:** centrality-based (Girvan–Newman removes the highest-betweenness **link** repeatedly); dynamical (label propagation, random walks such as Infomap); spectral (see [[Spectral graph theory]]); inferential (SBM, see [[Stochastic block models]]).

![[tutorial-8-cell-44-plot-1.png|550]]

> [!exam] Interpreting modularity results
> **Trial 1, Q8:** different greedy methods reach different optima (e.g. $B=3$, $Q\approx0.41$–$0.435$ on Karate Club). They are **path-dependent heuristics**: early merges or splits restrict later options, and each method visits different partitions. The highest point found is the best **visited**, not a proof of the global maximum.
> **Trial 2, Q8:** Louvain on an ER graph ($N=1000$, $\langle z\rangle=4$) returns $44$ groups with $Q=0.523$.
> - The ER graph has **no** planted structure, but finite random graphs have density fluctuations. Searching an enormous space of partitions exploits them and finds high $Q$.
> - The single group has $Q=0$; it is not returned because a higher-$Q$ partition exists.
>
> Lesson: high $Q$ is not evidence of real communities without a null comparison.

> [!remark] Comparing partitions
> Labels are arbitrary. For two binary labellings differing at $d$ nodes, the mismatch is $\min(d,N-d)$. For more groups use a contingency table.
> In the tutorial's 5-block SBM with $p_{rr}=0.2-q$ and $p_{rs}=q$, the structure is assortative for $q<0.1$ and ER at $q=0.1$. For $q>0.1$ it is disassortative, and modularity still returns assortative groups because that is what it optimises.

> [!code]- NetworkX communities (tutorial 8)
> ```python
> from networkx.algorithms import community
> V1, V2 = community.kernighan_lin_bisection(G, seed=13)
> parts = community.greedy_modularity_communities(G)
> parts = community.louvain_communities(G, seed=13)
> community.modularity(G, parts)
> ```

> [!selftest]- Self-test
> 1. Derive $\Delta Q$ for merging two groups.
> 2. Why can modularity find communities in ER graphs? — Optimisation over many partitions picks up random fluctuations.
> 3. Which methods can do community detection: spectral, WS model, Jaccard, SBM, threshold model? — Spectral and SBM.

---
Related: [[Spectral graph theory]] · [[Stochastic block models]] · [[Configuration model]] · [[Centrality]]
