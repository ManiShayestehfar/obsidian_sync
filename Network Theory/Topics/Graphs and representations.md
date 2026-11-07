---
tags: [data5441, ch01, foundations]
aliases: [Graph, Adjacency matrix, Degree, Degree distribution, Sparse and dense]
---
# Graphs and representations

> [!abstract] Summary
> A network is a set of nodes plus a set of links, encoded by an adjacency matrix. Degree, the degree distribution and its moments are the first statistics to compute. The sparse/dense distinction is used everywhere afterwards.
> Chapter: [[Ch01 Networks and high dimensions]]

## Basic objects

> [!definition] Network (graph)
> A network $g=(\mathcal N,\mathcal L)$ consists of a set $\mathcal N=\{n_1,\dots,n_N\}$ of $N$ **nodes** (vertices) and a set $\mathcal L=\{l_1,\dots,l_L\}$ of $L$ **links** (edges), each joining a pair of nodes.
> - **Undirected:** links are unordered pairs $\{i,j\}$. **Directed:** links are ordered pairs $i\to j$.
> - **Simple:** no self-loops and no repeated links. **Multigraph:** repeated links allowed.
> - **Weighted:** each link carries a weight $w_{ij}$.
> - **Bipartite:** two node types; links only join nodes of different types.

> [!definition] Adjacency matrix
> For a simple undirected graph, $A\in\{0,1\}^{N\times N}$ with $A_{ij}=1$ iff $\{i,j\}\in\mathcal L$. Then $A=A^\top$ and $A_{ii}=0$.
> For a directed graph we use $A_{ij}=1$ iff $i\to j$ (some texts transpose this; always state the convention).

> [!definition] Maximum number of links
> For $N$ labelled nodes the number of possible undirected links (node pairs, dyads) is
> $$Y=\binom N2=\frac{N(N-1)}2 .$$
> For directed links without self-loops it is $N(N-1)$.

## Degree

> [!definition] Degree, neighbours
> The **neighbours** of $i$ are $\Gamma(i)=\{j:A_{ij}=1\}$. The **degree** is
> $$z_i=|\Gamma(i)|=\sum_{j}A_{ij}.$$
> In a directed graph, $z_i^{out}=\sum_jA_{ij}$ (row sum) and $z_i^{in}=\sum_jA_{ji}$ (column sum).

> [!theorem] Handshaking lemma
> For an undirected graph, $\displaystyle\sum_{i=1}^N z_i=2L$, hence $\langle z\rangle=2L/N$. The number of odd-degree nodes is even.

> [!proof]-
> Each link $\{i,j\}$ contributes $1$ to $z_i$ and $1$ to $z_j$, so it contributes exactly $2$ to $\sum_i z_i$. Summing over the $L$ links gives $2L$. Since $\sum_i z_i$ is even, the number of odd terms in it must be even. $\square$

> [!definition] Degree distribution and moments
> Let $N_z$ be the number of nodes of degree $z$. Then
> $$P(z)=\frac{N_z}{N}=\frac1N\sum_{i=1}^N\delta_{z,z_i},\qquad \langle z^n\rangle=\sum_z z^nP(z)=\frac1N\sum_{i=1}^N z_i^n,\qquad \sigma_z=\sqrt{\langle z^2\rangle-\langle z\rangle^2}.$$
> The **relative degree variability** $\sigma_z/\langle z\rangle$ measures degree heterogeneity. It is $0$ for a regular graph, $\approx1/\sqrt{\langle z\rangle}$ for a Poisson (ER) graph, and large for heavy-tailed graphs.

> [!definition] Sparse and dense
> For a sequence of graphs with $N\to\infty$:
> - **sparse** if $\langle z\rangle$ stays bounded, i.e. $L=O(N)$, so the density $L/Y\to0$;
> - **dense** if $\langle z\rangle\propto N$, i.e. $L\propto N^2$ and the density $L/Y$ stays positive.
>
> Most real networks are sparse.

## Representations

| Representation | Memory | Good for |
|---|---|---|
| Adjacency matrix | $O(N^2)$ | linear algebra, $O(1)$ link lookup |
| Adjacency list | $O(N+L)$ | traversal of sparse graphs |
| Edge list | $O(L)$ | storage and loading files |

> [!remark] Common pitfalls
> - An edge list does not record isolated nodes.
> - `nx.Graph` merges repeated edges and reverse pairs. Converting directed or weighted data to a simple graph is a modelling choice.
> - In a weighted graph, the **strength** $s_i=\sum_jw_{ij}$ is different from the degree.

> [!example] Bipartite projection
> An author–article network is bipartite. Its **author projection** joins two authors if they share an article. An article with $k$ authors becomes a $k$-clique. Projection therefore creates triangles and loses the information about which collaborations happened together.

![[graph-and-matrix.png|650]]

> [!code]- NetworkX: build and inspect
> ```python
> import networkx as nx
> G = nx.read_edgelist("edges.txt", nodetype=int)    # or nx.from_pandas_edgelist(df, "source", "target")
> G.remove_edges_from(nx.selfloop_edges(G))          # make it simple
> N, L = G.number_of_nodes(), G.number_of_edges()
> z = [d for _, d in G.degree()]
> mean_z = 2 * L / N
> ```

> [!selftest]- Self-test
> 1. A graph has $N=200$ and $L=1000$. What are $\langle z\rangle$ and the density? — $\langle z\rangle=2L/N=10$; density $=L/Y=1000/19900=10/199$.
> 2. What is $\sigma_z/\langle z\rangle$ for a $z$-regular graph? — $0$.
> 3. Why can an author projection have high clustering even if authorship is "random"? — Each multi-author paper becomes a clique.

---
Related: [[Paths and components]] · [[Clustering]] · [[Erdos-Renyi graphs]]
