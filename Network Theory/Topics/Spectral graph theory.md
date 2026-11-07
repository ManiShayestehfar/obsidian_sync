---
tags: [data5441, ch08, foundations]
aliases: [Laplacian, Laplace matrix, Spectral clustering, Fiedler vector, Eigengap]
---
# Spectral graph theory

> [!abstract] Summary
> The Laplacian $\mathbf L=D-A$ is positive semi-definite. Its zero eigenvalues count components, and its small eigenvalues reveal nearly disconnected groups. Spectral clustering embeds nodes using the first eigenvectors and then clusters them. The same embedding scores missing links.
> Chapter: [[Ch08 Community detection]]

> [!definition] Laplace matrix *(formula sheet)*
> $$\mathbf L=D-A,\qquad \mathbf L_{ij}=z_i\delta_{ij}-A_{ij},\qquad D=\operatorname{diag}(z_1,\dots,z_N).$$
> Its eigenvalues are ordered $0=\lambda_1\le\lambda_2\le\dots\le\lambda_N$. Do not confuse $\mathbf L$ with the number of links $L$.

> [!definition] Spectral method
> Any clustering method based on the eigenvalues and eigenvectors of a matrix representing the graph (here $\mathbf L$).

> [!theorem] Quadratic form and number of components
> For all $x\in\mathbb R^N$,
> $$x^\top\mathbf Lx=\sum_{\{i,j\}\in\mathcal L}(x_i-x_j)^2\ \ge0 .$$
> Hence $\mathbf L$ is positive semi-definite. Its kernel is spanned by the component indicator vectors, so
> $$\#\{r:\lambda_r=0\}=\text{number of connected components}.$$

> [!proof]-
> $x^\top Dx=\sum_iz_ix_i^2=\sum_{\{i,j\}\in\mathcal L}(x_i^2+x_j^2)$ and $x^\top Ax=2\sum_{\{i,j\}\in\mathcal L}x_ix_j$. Subtracting gives the sum of squares.
> $x^\top\mathbf Lx=0$ iff $x_i=x_j$ on every link, i.e. iff $x$ is constant on each component. The component indicators are linearly independent and span this set, so the dimension of the kernel equals the number of components. $\mathbf L$ is symmetric, so its eigenvalues are real, and they are non-negative by the inequality. $\square$

> [!proposition] Cut size and the Fiedler vector
> Encode a bisection by $x_i=\pm1$. Then $R=\tfrac14x^\top\mathbf Lx$.
> Relaxing to real $x\perp\mathbf1$ with $\|x\|=1$, the minimum of $x^\top\mathbf Lx$ is $\lambda_2$, attained at the eigenvector $u_2$ (Fiedler vector). Splitting by the sign of $u_2$ is a heuristic bisection. A small $\lambda_2$ means a nearly disconnected graph.

> [!algorithm] Spectral clustering
> 1. Compute the smallest eigenvalues of $\mathbf L$. Choose $B$ at a large **eigengap** $\lambda_{B+1}-\lambda_B$.
> 2. Form $U\in\mathbb R^{N\times B}$ from the first $B$ eigenvectors.
> 3. Treat **row $i$** of $U$ as coordinates of node $i$, and cluster the rows (e.g. $k$-means).
>
> Intuition: with $B$ disconnected groups, the first $B$ eigenvectors are group indicators (rows are identical within a group). Weak links between groups perturb this only slightly.

![[tutorial-8-cell-67-plot-1.png|600]]

> [!definition] Spectral link prediction (embedding)
> On the training graph, embed node $i$ as $v_i=(u_2(i),\dots,u_{d+1}(i))$ and score a pair by $s_{ij}=-\|v_i-v_j\|^2$, so nearby nodes are likely linked. Recompute the embedding after removing the test links, to avoid leakage. See [[Link prediction]].

> [!code]- NumPy (tutorials 8–9)
> ```python
> Lap = nx.laplacian_matrix(G).toarray()
> lam, U = np.linalg.eigh(Lap)                 # ascending eigenvalues
> from sklearn.cluster import KMeans
> labels = KMeans(B, n_init=10, random_state=13).fit_predict(U[:, :B])
> ```

> [!selftest]- Self-test
> 1. Prove $x^\top\mathbf Lx=\sum_{\text{links}}(x_i-x_j)^2$.
> 2. A graph has spectrum $0,0,0,0.4,2.1,\dots$. How many components does it have? — $3$.
> 3. Can spectral methods be used for link prediction? — Yes, via the embedding.

---
Related: [[Community detection]] · [[Link prediction]] · [[Centrality]] · [[Synchronisation and stability]]
