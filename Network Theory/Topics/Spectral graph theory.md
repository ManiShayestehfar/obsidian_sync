---
tags: [data5441, ch08, foundations]
aliases: [Laplacian, Laplace matrix, Spectral clustering, Fiedler vector, Eigengap]
---
# Spectral graph theory

> [!abstract] Summary
> Spectral methods replace a difficult discrete partitioning problem with one involving **eigenvectors of a graph matrix**. For the Laplacian $\mathcal L=D-A$, small eigenvalues correspond to directions that vary little across edges. Zero eigenvalues count connected components; the next eigenvectors reveal **almost-disconnected communities**. In Week 9, the same idea becomes a **low-dimensional embedding** for link prediction.
> Chapter: [[Ch08 Community detection]] · Sources: DATA5441 **Week 8**, lecture pp. 109–111; **Week 9**, p. 118; Tutorials 8–9.

## 1. The graph Laplacian and its meaning

> [!definition] Laplace matrix *(formula sheet)*
> For a simple undirected graph, with adjacency matrix $A$ and $z_i=\sum_j A_{ij}$,
> $$\boxed{\mathcal L=D-A,\qquad D=\operatorname{diag}(z_1,\ldots,z_N).}$$
> Since $\mathcal L$ is symmetric, it has orthonormal eigenvectors $u_1,\ldots,u_N$ and real eigenvalues $0=\lambda_1\le\lambda_2\le\cdots\le\lambda_N$. We use $\mathcal L$ for the **matrix** and $L$ for the **number of links**.

> [!theorem] Laplacian energy and connected components
> For $x\in\mathbb R^N$,
> $$\boxed{x^{\mathsf T}\mathcal Lx=\sum_{\{i,j\}\in E}(x_i-x_j)^2\ge0.}$$
> Therefore $\mathcal L$ is **positive semidefinite**. Moreover,
> $$\boxed{\dim\ker\mathcal L=\text{number of connected components}.}$$
> If the graph is connected, $\lambda_1=0$ is simple and $u_1=\mathbf1/\sqrt N$.

> [!proof]- Why both claims hold
> Using $\sum_i z_ix_i^2=\sum_{\{i,j\}\in E}(x_i^2+x_j^2)$ and $x^{\mathsf T}Ax=2\sum_{\{i,j\}\in E}x_ix_j$, subtraction gives the sum of squares. Energy zero means $x_i=x_j$ for **every edge**, hence $x$ is constant on each component. Independent component-indicator vectors form a basis of the kernel.

**Interpretation:** Think of $x_i$ as a number or coordinate attached to node $i$. The energy is small when **linked nodes have similar coordinates**. That is why the smallest eigenvectors capture large-scale groups.

## 2. From minimising a cut to an eigenvector

> [!proposition] Spectral relaxation of a bisection
> Represent a bisection by $x_i=+1$ on one side and $x_i=-1$ on the other. Every crossing edge contributes $(+1-(-1))^2=4$, so
> $$\boxed{R=\frac14 x^{\mathsf T}\mathcal Lx.}$$
> For a **balanced** bisection, $x^{\mathsf T}\mathbf1=0$. Instead of searching discrete $\{\pm1\}$ assignments, allow real vectors with $x\perp\mathbf1$ and $\|x\|=1$. Rayleigh–Ritz gives
> $$\min_{x\perp\mathbf1,\ \|x\|=1}x^{\mathsf T}\mathcal Lx=\lambda_2.$$
> A minimiser is a **Fiedler vector** $u_2$. Splitting nodes by its sign is a **heuristic** approximation to a graph bisection; the exact cut problem remains discrete.

> [!remark] Why the second eigenvector, not the first?
> For a connected graph, $u_1$ is **constant** and cannot separate nodes. The first non-constant eigenvector $u_2$ is the smoothest non-trivial direction. Small $\lambda_2$ indicates weak connectivity **between** some regions; if $\lambda_2=0$, the graph is disconnected.

## 3. Spectral community detection: several groups

> [!definition] Eigengap
> If a graph has exactly $B$ disconnected components, then $\lambda_1=\cdots=\lambda_B=0$ and $\lambda_{B+1}>0$. If the components are joined by **few weak links**, the first $B$ eigenvalues become small and often remain separated from the rest by a **gap** $\lambda_{B+1}-\lambda_B$. This suggests $B$ groups, but the gap is a **heuristic**, not a theorem that the planted value must be recovered.

> [!algorithm] Laplacian spectral clustering (Tutorial 8)
> 1. Compute the *smallest* eigenpairs $(\lambda_k,u_k)$ of $\mathcal L=D-A$.
> 2. Look for a large eigengap and select a tentative number of groups $B$.
> 3. Form $U=[u_1\;u_2\;\cdots\;u_B]\in\mathbb R^{N\times B}$.
> 4. Regard the **$i$th row** $U_{i,:}$ as coordinates of node $i$ in $\mathbb R^B$.
> 5. Cluster these $N$ points into $B$ groups (e.g. **$k$-means**); map the cluster labels back to the nodes.
>
> In the exactly disconnected case, rows corresponding to nodes within the same component coincide (for any orthonormal basis of the nullspace). A small number of bridges perturbs these ideal clusters.

![[Assets/w8-spectral-embedding.png|720]]

> [!remark] Things that can mislead you
> - **Columns** of $U$ are eigenvectors; **rows** are the embedded nodes.
> - Eigenvector **signs** are arbitrary, as are rotations within a repeated eigenspace; the relative geometry, not axis orientation, matters.
> - Large degree heterogeneity may favour a **normalised Laplacian**, but the course's main derivations use $D-A$.
> - Spectral clustering outputs a **partition**; it does not assign a probability to each edge by itself.

## 4. The Week 9 connection: spectral *link prediction*

> [!definition] Laplacian spectral embedding score
> To predict missing links, compute the Laplacian **from the training graph**. For a connected graph, discard the constant eigenvector and choose $d$ non-trivial directions:
> $$v_i=(u_2(i),\ldots,u_{d+1}(i))\in\mathbb R^d.$$
> Nearby embedded nodes are expected to connect; give the unobserved pair $(i,j)$ the **ranking score**
> $$\boxed{s_{ij}=-\|v_i-v_j\|^2.}$$
> The minus sign ensures that **shorter distance gives higher score**. This is a score for ranking, **not a calibrated probability**.

> [!remark] $B$ versus $d$, and disconnected training graphs
> - **Community detection:** $B$ is the requested number of groups, and the course uses the first $B$ eigenvectors.
> - **Link prediction:** $d$ is the number of informative **positive-eigenvalue directions** retained. For $B$ ideal disconnected groups, there are $B-1$ non-constant group directions relative to the global constant.
> - A training graph may become disconnected when test links are removed. **Tutorial 9 explicitly retains *all* zero modes**, then adds the first $d$ positive modes. This avoids arbitrarily discarding component information; the simple $u_2,\ldots,u_{d+1}$ expression assumes connectivity.
> - Choose $d$ based on validation performance; increasing $d$ does not necessarily improve AUC.

> [!code]- Minimal spectral clustering (Tutorial 8)
> ```python
> import numpy as np
> from sklearn.cluster import KMeans
> Lap = nx.laplacian_matrix(G, weight=None).toarray()
> eigenvalues, U = np.linalg.eigh(Lap)       # ascending eigenvalues
> B = 3                                       # chosen from eigengap
> labels = KMeans(n_clusters=B, n_init=10,
>                 random_state=13).fit_predict(U[:, :B])
> ```

> [!selftest]- Self-test
> 1. **Why $\mathcal L\succeq0$?** — Its quadratic form is a sum of squared edge differences.
> 2. **Spectrum $0,0,0,0.4,2.1,\ldots$?** — Three connected components.
> 3. **What does a large gap after $\lambda_B$ suggest?** — About $B$ weakly connected groups.
> 4. **Why negate the embedding distance for link prediction?** — AUC expects larger scores for more likely links.

---
Related: [[Community detection]] · [[Link prediction]] · [[Stochastic block models]] · [[Centrality]] · [[Synchronisation and stability]]
