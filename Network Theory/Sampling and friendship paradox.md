---
tags: [foundations]
---

# Sampling and friendship paradox

Sampling changes the distribution of what is observed. Specify both the state space and selection mechanism before interpreting an average.

> [!theorem] Unbiased sampling averages
> If each observation $X_s$ has marginal law $p$, then $\widehat\mu=R^{-1}\sum_{s=1}^R f(X_s)$ satisfies $\mathbb E[\widehat\mu]=\sum_xp(x)f(x)$, assuming integrability. Independence is unnecessary for unbiasedness; it matters for variance and convergence.

> [!proof]
> Apply linearity of expectation to the finite sum. Correlations contribute to $\operatorname{Var}(\widehat\mu)$ through covariance terms, but not to its expectation.

## Two different ways to sample a neighbour
Let $p_k$ be the degree distribution of a fixed undirected graph with $L>0$.

> [!theorem] Uniform edge endpoints
> Selecting one of the $2L$ oriented edge endpoints uniformly gives
> $$\Pr(K=k)=\frac{kp_k}{\langle k\rangle},\qquad\mathbb E[K]=\frac{\langle k^2\rangle}{\langle k\rangle}=\langle k\rangle+\frac{\operatorname{Var}(k)}{\langle k\rangle}.$$
> Thus this mean is at least the mean degree of a uniform vertex; equality holds exactly when the graph is regular.

> [!proof]
> Vertex $i$ occurs at $k_i$ endpoints, so its selection probability is $k_i/(2L)$. Sum its degree against these probabilities and use $\sum_i k_i=2L$.

The tutorials also choose a **uniform vertex, then one of its neighbours uniformly**. With no isolated vertices,
$$\Pr(J=j)=\frac1N\sum_{i\sim j}\frac1{k_i},\qquad\mathbb E[k_J]=\frac1N\sum_{\{i,j\}\in E}\left(\frac{k_i}{k_j}+\frac{k_j}{k_i}\right)\ge\frac{2L}{N}.$$
The inequality follows from $a/b+b/a\ge2$. This law is generally different from endpoint sampling. On a star the two means are respectively $N/2$ and $[(N-1)^2+1]/N$.

> [!code] Keep the sampling protocols separate
> ```python
> import networkx as nx
> import numpy as np
>
> G = nx.star_graph(5)
> rng = np.random.default_rng(5441)
> nodes, edges = list(G), list(G.edges())
> R = 5000
> vertex_sample, endpoint_sample, neighbour_sample = [], [], []
> for _ in range(R):
>     u = nodes[rng.integers(len(nodes))]
>     vertex_sample.append(G.degree(u))
>     a, b = edges[rng.integers(len(edges))]
>     endpoint_sample.append(G.degree((a, b)[rng.integers(2)]))
>     neighbours = list(G.neighbors(u))  # this example has no isolates
>     v = neighbours[rng.integers(len(neighbours))]
>     neighbour_sample.append(G.degree(v))
> print(*(np.mean(x) for x in
>         (vertex_sample, endpoint_sample, neighbour_sample)))
> ```

## Observing networks
Vertex sampling, edge sampling, random walks and snowball sampling expose different parts of a network. Independent vertex retention with probability $s$ keeps each original edge with probability $s^2$, so expected retained edges are $s^2L$. Sparse induced samples can therefore be nearly empty.

A simple random walk on a finite connected undirected graph has stationary mass $k_i/(2L)$, by detailed balance across every edge. Periodicity may prevent convergence without a holding probability; see [[Monte Carlo sampling]]. Snowball exploration repeatedly adds neighbours and favours reachable, well-connected regions. Its growth is not universally $\langle k\rangle^t$ because of backtracking, overlap and degree heterogeneity.

Averaging successive running means does not recover the final sample mean. Sampling without replacement also requires sample size at most the population size. If isolated vertices occur, define what a failed neighbour query does; rejecting them changes the initial sampling law. None of the friendship inequalities says every individual has fewer friends than each of their friends.

> [!reference]- Sources
> Lecture Week 2 pp.8–13; Jenny’s notes Week 2. Newman §4.7 and §12.2. Tutorial 1, node/neighbour sampling and running-average examples.
