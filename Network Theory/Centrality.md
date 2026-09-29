---
tags: [foundations]
---

# Centrality

Centrality is a choice of what makes a vertex important. More contacts, shorter routes and influence from important neighbours answer different questions.

| Measure | Definition or mechanism | Interpretation |
| --- | --- | --- |
| Degree | $k_i$; often normalised by $N-1$ | Immediate contacts |
| Closeness | $(N-1)/\sum_{j\ne i}d(i,j)$ on a connected graph | Access by short routes |
| Harmonic | $\sum_{j\ne i}1/d(i,j)$, with $1/\infty=0$ | Distance-based score allowing disconnection |
| Betweenness | $\sum_{s<t; s,t\ne i}\sigma_{st}(i)/\sigma_{st}$ | Brokerage along shortest routes |
| Eigenvector | $Av=\rho(A)v$ for undirected $A$ | Importance inherited from neighbours |
| Katz | Baseline plus discounted walks | Prestige with an exogenous contribution |
| PageRank | Teleporting random-walk stationary law | Prestige diluted by sender’s out-degree |

Here $\sigma_{st}$ counts shortest paths and $\sigma_{st}(i)$ counts those passing internally through $i$. Unreachable pairs contribute zero to betweenness. Ordered versus unordered pairs, inclusion of endpoints and normalisation must be fixed before comparing values.

> [!theorem] Perron–Frobenius and its limit
> For a connected undirected graph with at least two vertices, $A$ has a positive eigenvector for its spectral radius $\rho$, unique up to positive scaling, and $\rho$ is a simple eigenvalue. Moreover $\min_i k_i\le\rho\le\max_i k_i$.
>
> Connectedness alone does not imply $|\lambda|<\rho$ for all other eigenvalues: connected bipartite graphs also have eigenvalue $-\rho$.

For symmetric $A$, expand $x_0=\sum_r a_rv_r$. Then $\rho^{-t}A^tx_0=\sum_r a_r(\lambda_r/\rho)^tv_r$. Convergence to the Perron direction requires a nonzero leading coefficient and strict spectral-modulus gap. A bipartite graph can cause oscillation; shifting to $A+I$ preserves eigenvectors and removes this obstruction for connected undirected graphs.

> [!definition] Katz and PageRank
> With $A_{ij}=1$ for $i\to j$, incoming Katz scores solve
> $$x=\beta\mathbf1+\alpha A^\top x=\beta(I-\alpha A^\top)^{-1}\mathbf1,$$
> where $\beta>0$ and $0\le\alpha<1/\rho(A)$ when $\rho(A)>0$. For a nilpotent adjacency matrix the walk series terminates instead.
>
> Let $P$ be the row-stochastic random-walk matrix; replace a dangling row by a probability vector $v^\top$. For $0<\alpha<1$ and strictly positive $v$,
> $$r=\alpha P^\top r+(1-\alpha)v,\qquad\mathbf1^\top r=1$$
> has a unique positive solution.

> [!proof] Walk and random-walk interpretations
> Under the Katz bound, $(I-\alpha A^\top)^{-1}=\sum_{t\ge0}\alpha^t(A^\top)^t$; multiplying by the all-ones vector counts discounted incoming walks. For PageRank, the full transition matrix $\alpha P+(1-\alpha)\mathbf1v^\top$ is positive and stochastic, hence irreducible and aperiodic with a unique stationary probability vector.

> [!code] Compare rankings on one graph
> ```python
> import networkx as nx
> import numpy as np
>
> G = nx.karate_club_graph()
> A = nx.to_numpy_array(G, weight=None)
> rho = np.linalg.eigvalsh(A)[-1]
> scores = {
>     'degree': nx.degree_centrality(G),
>     'closeness': nx.closeness_centrality(G),
>     'betweenness': nx.betweenness_centrality(G, weight=None),
>     'eigenvector': nx.eigenvector_centrality(G, weight=None, max_iter=1000),
>     'Katz': nx.katz_centrality(G, alpha=0.8/rho, beta=1.0,
>                               weight=None, max_iter=1000),
>     'PageRank': nx.pagerank(G, alpha=0.85, weight=None),
> }
> leaders = {name: sorted(values, key=values.get, reverse=True)[:3]
>            for name, values in scores.items()}
> print(leaders)
> ```

On a star, the hub maximises several scores, but its eigenvector-to-leaf ratio is $\sqrt{N-1}$ and its degree ratio is $N-1$. In a directed graph feeding a terminal cycle, eigenvector prestige can concentrate downstream; Katz and PageRank introduce baseline mass. Scores from different methods need not have comparable scales.

For disconnected graphs, NetworkX’s closeness includes a component-size correction; harmonic centrality is another explicit convention. [[Spectral graph theory]] connects these spectral ideas to connectivity and dynamics.

> [!reference]- Sources
> Lecture Week 2 pp.1–7; Jenny’s notes Week 2. Newman §7.1. Tutorial 2, centrality exercises. API: [NetworkX centrality](https://networkx.org/documentation/stable/reference/algorithms/centrality.html).
