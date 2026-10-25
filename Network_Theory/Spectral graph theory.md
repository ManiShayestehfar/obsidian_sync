---
tags: [foundations]
---

# Spectral graph theory

Connectivity is encoded in a matrix: disconnected pieces give independent constant modes, and weak links between them create slowly varying modes. This connects graph partitioning, low-dimensional representations and diffusion. The important object is often an eigenspace rather than a particular choice of eigenvectors.

## The Laplacian and its energy

> [!definition] Graph Laplacian
> For a simple undirected graph, $D=\operatorname{diag}(k_1,\ldots,k_N)$ and $\mathcal L=D-A$. Its eigenvalues can be ordered as $0=\lambda_1\le\cdots\le\lambda_N$. Here $L$ denotes edge count; $\mathcal L$ denotes the matrix.

> [!theorem] Energy identity and components
> For every $x\in\mathbb R^N$,
> $$x^\top\mathcal Lx=\sum_{\{i,j\}\in E}(x_i-x_j)^2\ge0.$$
> The kernel consists of vectors constant on each connected component. Its dimension is therefore the number of components.

**Proof.** Expand $x^\top Dx-x^\top Ax$ and group by edge. Every term is a square, so the sum vanishes exactly when adjacent values agree. Equality propagates along paths; component-indicator vectors form a basis of the kernel. Symmetry and this nonnegative quadratic form give real nonnegative eigenvalues. $\square$

On a connected graph, $u_1=N^{-1/2}\mathbf1$ spans the kernel. For a binary cut encoded by $x_i\in\{-1,1\}$, the cut size is $x^\top\mathcal Lx/4$. Relaxing to real $x\perp\mathbf1$ with $\|x\|=1$ minimises this energy at $\lambda_2$: in an orthonormal eigenbasis the objective is $\sum_{r\ge2}\lambda_r a_r^2$. Rounding the minimiser is a heuristic for the original discrete problem.

## From components to communities

For $B$ disconnected components, their indicator vectors span the first $B$ modes. If weak links join those pieces, their low-dimensional subspace may remain distinguishable from higher modes when an eigengap persists. Adding an edge changes the diagonal degrees and off-diagonal matrix entries together.

> [!algorithm] Laplacian spectral clustering
> 1. Choose a candidate $B$, informed by gaps $\Delta_k=\lambda_{k+1}-\lambda_k$ among the small eigenvalues.
> 2. Put the first $B$ eigenvectors into the columns of $U\in\mathbb R^{N\times B}$.
> 3. Interpret **row $i$** as the coordinates of vertex $i$ and cluster the rows into $B$ groups, for example with $k$-means.
> 4. Compare the resulting partition with the intended objective or planted groups.
>
> An eigengap is a diagnostic, not a proof that statistically meaningful communities exist. An eigenbasis inside a repeated eigenspace can rotate; including the whole eigenspace makes Euclidean distances invariant to that rotation.

![[Assets/tutorial-8-cell-67-plot-1.png|800]]
*Supplied Tutorial 8, cell 67: a conspicuous gap after the third mode motivates three groups for this particular planted SBM.*

> [!code]- A complete small-graph clustering example
> ```python
> import networkx as nx
> import numpy as np
> from sklearn.cluster import KMeans
>
> G = nx.stochastic_block_model(
>     [20, 40, 20], [[0.2, .01, .01], [.01, .15, .01], [.01, .01, .5]], seed=13)
> nodes = list(G)
> A = nx.to_numpy_array(G, nodelist=nodes, weight=None)
> Lap = np.diag(A.sum(axis=1)) - A
> eigenvalues, U = np.linalg.eigh(Lap)
> B = 3
> labels = KMeans(n_clusters=B, n_init=10, random_state=13).fit_predict(U[:, :B])
> partition = [{nodes[i] for i in range(len(nodes)) if labels[i] == r}
>              for r in range(B)]
> assert nx.community.is_partition(G, partition)
> ```
> Dense matrices are appropriate for this small illustration; use sparse eigensolvers for large networks. Changing to a normalised Laplacian changes the geometry and objective. Declare an isolated-vertex convention if using degree inverses.

## Spectral link prediction is a different use of the embedding

For a connected **training graph**, discard its constant direction and use $v_i=(u_2(i),\ldots,u_{d+1}(i))$. Score a candidate link by
$$s_{ij}=-\|v_i-v_j\|^2,$$
so closer vertices receive larger scores. This performs ranking rather than clustering into a prescribed $B$. Recompute the embedding after removing test edges; otherwise information leaks into the prediction.

The notebook also handles disconnected training graphs by including **all zero modes**, followed by $d$ positive modes. With component-indicator coordinates, vertices in different components receive a squared-distance contribution $1/|C_a|+1/|C_b|$. Including the entire nullspace makes this contribution basis-independent. This is an explicit extension of the connected-graph definition, not the same as discarding one arbitrary zero eigenvector.

> [!code]- Link scores with an explicit nullspace convention
> ```python
> import networkx as nx
> import numpy as np
>
> def laplacian_scores(g, pairs, d=2):
>     nodes = list(g)
>     index = {v: i for i, v in enumerate(nodes)}
>     A = nx.to_numpy_array(g, nodelist=nodes, weight=None)
>     values, U = np.linalg.eigh(np.diag(A.sum(axis=1)) - A)
>     tol = len(nodes) * np.finfo(float).eps * max(1.0, values[-1])
>     positive = U[:, values > tol]
>     if not 1 <= d <= positive.shape[1]:
>         raise ValueError('Require at least d positive eigenvalue directions')
>     embedding = np.column_stack((U[:, values <= tol], positive[:, :d]))
>     return np.array([-np.sum((embedding[index[u]] - embedding[index[v]])**2)
>                      for u, v in pairs])
> ```
> If the chosen cutoff splits a repeated positive eigenspace, the partial embedding can depend on the selected basis; a clear gap or inclusion of the whole tied subspace avoids this ambiguity.

![[Assets/tutorial-9-cell-34-plot-1.png|650]]
*Supplied Tutorial 9, cell 34: mean AUC and SD across its Karate splits. One positive direction gives the highest displayed mean; this is not a universal optimum for other graphs or splits.*

## For revision

- Prove the energy identity and the relation between zero modes and components.
- Distinguish $B$ eigenvectors for clustering from $d$ positive directions for link prediction.
- Explain the eigengap, row-versus-column convention and disconnected-graph handling. Connections: [[Community detection]], [[Network reconstruction]] and [[Synchronisation and stability]].

> [!reference]- Sources
> Lecture Week 8 pp.9–11; Lecture Week 9 p.6. Tutorial 8 §4 and Ex.4.1–4.2; Tutorial 9 §1.4 and Ex.1.4, especially cell 30’s nullspace convention. Jenny’s notes Weeks 8, 12. Newman §§6.14, 14.5 and 17.4. Figures retain supplied outputs.
