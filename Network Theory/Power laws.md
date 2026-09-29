---
tags: [models]
---

# Power laws

> [!definition] Degree tail and survival tail
> A degree distribution has a power-law tail if $p_k\sim Ak^{-\gamma}$ as $k\to\infty$, with $A>0$ and $\gamma>1$. Its survival function satisfies
> $$\Pr(K\ge k)\asymp k^{1-\gamma}.$$
> Thus histogram and survival-plot slopes are respectively $-\gamma$ and $-(\gamma-1)$. A broad tail need not be a power law.

> [!theorem] Moment criterion
> For an infinite distribution with this tail and $r\ge0$, $\mathbb E[K^r]$ is finite precisely when $\gamma>r+1$. A truncated moment grows logarithmically at equality and as $k_{max}^{r+1-\gamma}$ when $\gamma<r+1$.

> [!proof]
> Compare the tail sum $\sum_k k^rp_k$ to $\int k^{r-\gamma}\,dk$. The integral converges at infinity exactly when $r-\gamma<-1$. Equality gives the logarithm. Contributions from finitely many small degrees do not alter convergence.

For $2<\gamma\le3$, the ideal distribution has finite mean and infinite second moment. Every finite graph has finite empirical moments because $k_i\le N-1$. “Diverging variance” describes a limit of models or samples.

> [!theorem] Natural sample-maximum scale
> For independent degrees with $\Pr(K\ge k)\asymp k^{1-\gamma}$, the scale at which order one observation exceeds $k$ solves
> $$N\Pr(K\ge k_{max})\asymp1,\qquad k_{max}\asymp N^{1/(\gamma-1)}.$$
> This specifies a typical extreme-value scale, not deterministic convergence of the maximum divided by that scale.

The lecture’s condition $p(k_{max})\sim1/N$ uses mass at one degree instead of exceedance probability and gives the wrong exponent. For $\gamma=2.5$, the natural scale is $N^{2/3}$ and the second moment truncated there scales as $N^{1/3}$.

Graph degrees are dependent. For sparse simple uncorrelated approximations, requiring $k_i k_j/(2L)$ to remain small motivates a structural scale near $\sqrt N$ at bounded mean degree. A natural cutoff exceeding it signals potential degree correlations or repeated-edge effects; it does not prohibit a simple graph from containing a larger hub.

> [!code] Plot an empirical survival distribution
> ```python
> import networkx as nx
> import numpy as np
> import matplotlib.pyplot as plt
>
> G = nx.barabasi_albert_graph(1000, 2, seed=5441)
> deg = np.array([d for _, d in G.degree()])
> k = np.arange(1, deg.max() + 1)
> survival = np.array([(deg >= value).mean() for value in k])
> fig, ax = plt.subplots()
> ax.loglog(k, survival, '.')
> ax.set(xlabel='Degree k', ylabel='P(K >= k)')
> plt.close(fig)
> ```
> This plot describes the data; it is not a statistical power-law test. Report the tail range and compare plausible alternative distributions before making a fitting claim.

[[Preferential attachment]] gives one mechanism for exponent three. [[Configuration model]] and [[Percolation and robustness]] show why the second moment affects branching and resilience.

> [!reference]- Sources
> Lecture Week 5 pp.7–9 and 11; Jenny’s notes Weeks 5, 10. Newman §10.4, especially printed pp.327–328, and §12.8. Tutorial 5, empirical/Poisson/BA degree comparisons.
