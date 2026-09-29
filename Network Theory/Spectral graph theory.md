---
tags: [foundations]
---

# Spectral graph theory

> [!definition] Graph Laplacian
> For a simple undirected graph, let $D=\operatorname{diag}(k_1,\ldots,k_N)$ and $\mathcal L=D-A$. The matrix $\mathcal L$ is symmetric and has zero row sums. We reserve $L$ for edge count to avoid ambiguity.

> [!theorem] Energy identity and components
> For $x\in\mathbb R^N$,
> $$x^\top\mathcal Lx=\sum_{\{i,j\}\in E}(x_i-x_j)^2\ge0.$$
> Thus all Laplacian eigenvalues are nonnegative. Its kernel consists exactly of vectors constant on each connected component, so its nullity equals the number of components.

> [!proof]
> Expand $x^\top Dx-x^\top Ax$. Every edge contributes $x_i^2+x_j^2-2x_ix_j$. The nonnegative sum vanishes exactly when adjacent vertices have equal values, hence when values are constant along every path. Component-indicator vectors form a basis of these vectors.

For a connected graph with $N\ge2$, write $0=\lambda_1<\lambda_2\le\cdots\le\lambda_N$. The second eigenvalue is the algebraic connectivity.

> [!theorem] Spectral relaxation of a cut
> For $x_i\in\{-1,1\}$, the cut size is $x^\top\mathcal Lx/4$. Relaxing a balanced partition to real $x$ with $x\perp\mathbf1$ and $\|x\|_2=1$ gives
> $$\min x^\top\mathcal Lx=\lambda_2.$$

> [!proof]
> Each crossing edge contributes $(1-(-1))^2=4$ and each internal edge zero. In an orthonormal eigenbasis, the relaxed energy is $\sum_{r\ge2}\lambda_r a_r^2$ with $\sum a_r^2=1$, minimised by an eigenvector for $\lambda_2$. Rounding its entries to a discrete split need not solve the original cut problem optimally.

For $B$ disconnected components, the first $B$ eigenvectors span the component-indicator subspace. Form an $N\times B$ matrix and cluster its **rows**, one row per vertex. If links weakly join components and the relevant eigenspace remains separated, a similar embedding may expose groups. Individual eigenvectors inside a repeated eigenspace can rotate substantially; stability concerns the subspace, not a preferred basis. Adding edges changes both off-diagonal adjacency entries and the diagonal degrees.

> [!code] Laplacian spectrum and a two-way relaxation
> ```python
> import networkx as nx
> import numpy as np
>
> G = nx.barbell_graph(5, 1)
> nodes = list(G)
> A = nx.to_numpy_array(G, nodelist=nodes, weight=None)
> Lap = np.diag(A.sum(axis=1)) - A
> values, vectors = np.linalg.eigh(Lap)
> fiedler = vectors[:, 1]
> order = np.argsort(fiedler)
> left = {nodes[i] for i in order[:len(nodes)//2]}
> right = set(nodes) - left
> assert np.allclose(Lap @ np.ones(len(nodes)), 0)
> print(values[:3], left, right)
> ```
> This dense example is for small graphs; large sparse graphs need sparse eigensolvers. Median/order rounding is a heuristic and imposes a roughly balanced split.

A normalised alternative is $\mathcal L_{sym}=I-D^{-1/2}AD^{-1/2}$ when all degrees are positive. For isolates, declare a convention separately. Its eigenvectors and objective differ from those of $D-A$.

The adjacency spectrum underlies [[Centrality]]. Laplacian modes govern diffusion and synchronisation in [[Synchronisation and stability]].

> [!reference]- Sources
> Jenny’s notes Weeks 8 and 12, with corrected eigenspace/row interpretation. Newman §6.14, §14.5 (spectral methods), and §17.4. Proofs and the small numerical example are explanatory additions.
