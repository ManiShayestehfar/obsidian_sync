---
tags: [data5441, ch02, foundations]
aliases: [Centrality measures, Betweenness, Eigenvector centrality, PageRank, Katz]
---
# Centrality

> [!abstract] Summary
> "Importance" has several meanings, and each centrality encodes one mechanism: many contacts (degree), short routes (closeness), brokerage (betweenness), or importance inherited from important neighbours (eigenvector, Katz, PageRank). Choose the measure that matches the question.
> Chapter: [[Ch02 Centrality measures]]

## Local and path-based measures

> [!definition] Degree centrality
> The degree $z_i$, often normalised as $z_i/(N-1)$. It identifies nodes with the most direct contacts ("students with the most friends").

> [!definition] Closeness and harmonic centrality
> On a connected graph, closeness is $c_i=\dfrac{N-1}{\sum_{j\ne i}d_{ij}}$. Harmonic centrality, $h_i=\sum_{j\ne i}1/d_{ij}$ with $1/\infty=0$, also works on disconnected graphs.

> [!definition] Betweenness centrality
> Let $\sigma_{st}$ be the number of shortest paths from $s$ to $t$, and $\sigma_{st}(i)$ the number of those that pass through $i$ as an internal node. Then
> $$b_i=\sum_{s<t,\ s,t\ne i}\frac{\sigma_{st}(i)}{\sigma_{st}},\qquad \tilde b_i=\frac{b_i}{\binom{N-1}{2}}\in[0,1].$$
> It identifies **brokers or bridges**, e.g. students who connect different school years.

> [!example] Trial Exam 2, Q1(i)
> Node $5$ is the only route between a group of $4$ nodes and a group of $5$ nodes. All $4\times5=20$ shortest paths between the groups pass through it, so $b_5=20$. With $N=10$, $\tilde b_5=20/\binom92=20/36=5/9$.

![[centrality-comparison.png|650]]

## Spectral (recursive) measures

> [!definition] Eigenvector centrality *(formula sheet)*
> Iterate $x_i(t+1)=\sum_jA_{ij}x_j(t)$ and normalise at each step. The limit satisfies $Ax=\lambda_1x$ with $\lambda_1$ the largest eigenvalue: a node is important if its neighbours are important.

> [!theorem] Perron–Frobenius (undirected, connected)
> If $A$ is the adjacency matrix of a connected undirected graph with $N\ge2$, then:
> 1. its largest eigenvalue $\lambda_1=\rho(A)$ is simple;
> 2. $\lambda_1$ has an eigenvector with all entries strictly positive, unique up to scaling;
> 3. $\min_iz_i\le\lambda_1\le\max_iz_i$.

> [!proposition] Convergence of power iteration
> Write $x(0)=\sum_r a_rv_r$ in an orthonormal eigenbasis of the symmetric $A$. Then
> $$\frac{A^tx(0)}{\lambda_1^t}=a_1v_1+\sum_{r\ge2}a_r\Big(\frac{\lambda_r}{\lambda_1}\Big)^tv_r .$$
> This converges to the Perron direction iff $a_1\ne0$ and $|\lambda_r|<\lambda_1$ for all $r\ge2$.
> **Obstruction:** a connected **bipartite** graph has eigenvalue $-\lambda_1$, so the iteration oscillates. Iterating with $A+I$ instead fixes this, because it keeps the eigenvectors and shifts every eigenvalue by $+1$.

> [!definition] Katz centrality
> Add a baseline $\beta>0$: $x=\alpha A^\top x+\beta\mathbf 1$, so $x=\beta(I-\alpha A^\top)^{-1}\mathbf1=\beta\sum_{t\ge0}\alpha^t(A^\top)^t\mathbf1$.
> The series converges iff $0\le\alpha<1/\lambda_1$. Then $x_i$ counts incoming walks of every length, discounted by $\alpha^{\text{length}}$.

> [!definition] PageRank *(formula sheet form)*
> $$x_i(t+1)=\alpha\sum_jA_{ij}\frac{x_j(t)}{z_j^{out}}+\beta ,$$
> where the sum runs over the nodes $j$ linking to $i$ (index convention of the formula sheet). Each node splits its score equally among its out-links, so a link from a node with many out-links is worth less. The constant $\beta$ is the teleportation/baseline term. For $0<\alpha<1$ and $\beta>0$ there is a unique positive fixed point. A random walker that follows a uniformly chosen out-link with probability $\alpha$ and teleports otherwise has this fixed point (normalised) as its stationary distribution.

> [!remark] Why baselines matter in directed graphs
> Plain eigenvector centrality can give zero score to every node outside a strongly connected "sink". Katz and PageRank give every node baseline mass $\beta$. Nodes with zero out-degree ("dangling" nodes) need a convention in PageRank.

> [!example] Star graph
> On a star with $N$ nodes, the hub maximises degree, closeness, betweenness and eigenvector centrality. Its eigenvector-centrality ratio to a leaf is $\sqrt{N-1}$, whereas its degree ratio is $N-1$. Centralities from different measures are not on comparable scales.

> [!code]- NetworkX (tutorial 2)
> ```python
> nx.degree_centrality(G); nx.closeness_centrality(G)
> nx.betweenness_centrality(G)                 # normalised by default
> nx.eigenvector_centrality(G); nx.katz_centrality_numpy(G, alpha=0.1)
> nx.pagerank(G, alpha=0.85)
> ```

> [!selftest]- Self-test
> 1. Which centrality identifies bridges between communities? — Betweenness.
> 2. What is the condition on $\alpha$ for Katz centrality? — $\alpha<1/\lambda_1$.
> 3. Why can power iteration fail on a bipartite graph? — Because $-\lambda_1$ is also an eigenvalue, the iterates oscillate.

---
Related: [[Graphs and representations]] · [[Paths and components]] · [[Spectral graph theory]]
