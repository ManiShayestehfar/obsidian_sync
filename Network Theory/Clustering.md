---
tags: [foundations]
---

# Clustering

Clustering measures triangle closure. It is distinct from grouping vertices into communities.

> [!definition] Local clustering and transitivity
> Let $T_i$ be the number of triangles containing $i$ and $T$ the total number. For $k_i\ge2$,
> $$C_i=\frac{T_i}{\binom{k_i}2}.$$
> Set $C_i=0$ for lower degrees when taking the all-vertex mean $\bar C=N^{-1}\sum_iC_i$.
>
> A **wedge** is an unordered pair of neighbours with its central vertex specified. Global transitivity is
> $$C_{net}=\frac{3T}{\sum_i\binom{k_i}2}.$$
> If there are no wedges the ratio is undefined; returning zero is a software convention.

> [!theorem] Triangle counts and weighted averages
> For a simple undirected graph,
> $$T=\frac{\operatorname{tr}(A^3)}6,\qquad T_i=\frac{(A^3)_{ii}}2,\qquad C_{net}=\frac{\sum_i\binom{k_i}2C_i}{\sum_i\binom{k_i}2}.$$

> [!proof]
> A length-three closed walk in a loop-free simple graph traverses a triangle. Each triangle has three possible starting vertices and two orientations; fixing its starting vertex leaves two orientations. Also $\sum_iT_i=3T$. Substitution gives the wedge-weighted average. Hence transitivity and the uniform vertex average generally differ.

> [!example] A hub with two triangles
> Join a hub to five leaves, then add two disjoint leaf–leaf edges. Degrees are $(5,2,2,2,2,1)$ and local coefficients $(1/5,1,1,1,1,0)$. Thus $\bar C=7/10$, whereas $C_{net}=6/(10+4)=3/7$.

> [!code] Compute both definitions
> ```python
> import networkx as nx
>
> G = nx.Graph([(0, i) for i in range(1, 6)] + [(1, 2), (3, 4)])
> local = nx.clustering(G, weight=None)
> mean_local = nx.average_clustering(G, weight=None, count_zeros=True)
> transitivity = nx.transitivity(G)
> triangles = sum(nx.triangles(G).values()) // 3
> print(local, mean_local, transitivity, triangles)
> ```

## Lessons from lattices and random graphs
In the diagonal square lattice of [[Paths and components]], corner, non-corner boundary and interior local clustering are respectively $1$, $3/5$ and $3/7$. Therefore
$$\bar C=\frac{4+4(M-2)(3/5)+(M-2)^2(3/7)}{M^2}.$$
For $M=3$, $\bar C=239/315$ but transitivity is $3/5$. An axis-only square lattice has no triangles.

In $G(N,q)$, conditional on a vertex’s neighbour set of size at least two, every possible link within that set is independently present with probability $q$. Hence $\mathbb E[C_i\mid k_i\ge2]=q$, while the all-vertex convention gives $\mathbb E[\bar C]=q\Pr(k_i\ge2)$.

> [!warning] A ratio of expectations is not an expected ratio
> The SBM tutorial’s closed-wedge calculation computes $\mathbb E[3T]/\mathbb E[W]$, where $W=\sum_i\binom{k_i}2$. This need not equal $\mathbb E[3T/W]$. It approximates expected transitivity when the denominator is sufficiently concentrated. To estimate expected transitivity directly, compute it separately in each simulated graph and average those values.

The relevant null question is whether observed clustering exceeds what degrees or density explain; see [[Configuration model]] and [[Maximum entropy and ERGMs]].

> [!reference]- Sources
> Lecture Week 1, clustering pages; Weeks 3–6, model comparisons. Jenny’s notes Weeks 1, 3–6. Newman §7.3, §11.4 and §12.3. Tutorials 1–6; Tutorial 7 cell 22 (ratio caveat).
