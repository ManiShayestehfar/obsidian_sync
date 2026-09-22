---
type: study-note
tags: [DATA5441]
---

# Centrality and Perron-Frobenius

[[00_HOME]]

Sources: Week 2; Newman §7.1. Centrality is a modelling choice about what “important” means.

| Measure | Mechanism | Main caveat |
| --- | --- | --- |
| Degree | Many immediate contacts | Ignores their quality and global position |
| Eigenvector | Links to other important vertices | Reducibility, direction and periodicity matter |
| Katz | Sum of discounted walks plus a baseline | Discount must satisfy a spectral bound |
| PageRank | Random walk with teleportation | Outgoing normalisation and dangling nodes matter |
| Closeness | Small total distance | Disconnected-graph convention matters |
| Betweenness | Fraction of shortest paths passing through a vertex | Assumes shortest-path routing |

For undirected $A$, eigenvector centrality solves $Av=\lambda_1v$. For a connected graph, Perron–Frobenius gives a positive eigenvector for the spectral radius, unique up to scale. It does **not** imply $|\lambda_2|<\lambda_1$ for every connected graph: a bipartite graph also has eigenvalue $-\lambda_1$. Plain power iteration can oscillate. Adding a positive diagonal shift preserves eigenvectors and can resolve this periodicity.

Katz centrality with baseline $\mathbf1$ is
$$x=\mathbf1+\alpha Ax=(I-\alpha A)^{-1}\mathbf1=\sum_{r=0}^{\infty}\alpha^rA^r\mathbf1,$$
for $0\le\alpha<1/\rho(A)$. The inverse is essential. A finite walk sum approximates this only when its omitted tail is small.

For directed incoming prestige, replace $A$ by $A^\top$. For PageRank let $P$ be a row-stochastic transition matrix, with dangling rows replaced by a chosen distribution. Then
$$r=\alpha P^\top r+(1-\alpha)v,\quad \mathbf1^\top r=1,$$
where $v$ is the teleportation distribution and $0<\alpha<1$. Uniform positive teleportation ensures a unique positive stationary distribution.

For a connected graph, one closeness convention is $(N-1)/\sum_{j\ne i}d(i,j)$. Harmonic centrality sums $1/d(i,j)$, taking unreachable contributions as zero. Betweenness sums $\sigma_{st}(i)/\sigma_{st}$ over pairs; check ordered versus unordered pairs and normalisation before comparing results.

**Interpretation exercise:** in a star, the centre has maximal degree, closeness and betweenness. Its eigenvector entry relative to a leaf is $\sqrt{N-1}$; its degree ratio is $N-1$. Centralities need not be numerically proportional even when they rank vertices identically.
