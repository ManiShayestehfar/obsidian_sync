---
tags: [models]
---

# Maximum entropy and ERGMs

Hard constraints restrict which graphs are allowed. Moment constraints instead restrict expectations over a distribution. An ERGM needs both a graph support and specified statistics.

> [!definition] Maximum-entropy problem
> On a finite labelled graph space $\Omega$, choose $p_g\ge0$ to maximise
> $$H(p)=-\sum_gp_g\log p_g$$
> subject to $\sum_gp_g=1$ and $\sum_gp_gx_a(g)=x_a^*$ for $a=1,\ldots,m$, using $0\log0=0$. This uses counting measure on the stated graph space; another base measure changes the problem.

> [!theorem] Exponential-family form
> For an interior feasible solution, the maximum-entropy law has form
> $$p_\beta(g)=\frac{e^{\beta\cdot x(g)}}{Z(\beta)},\qquad Z(\beta)=\sum_{h\in\Omega}e^{\beta\cdot x(h)}.$$
> Choose $\beta$ to match the expected statistics. The maximising distribution is unique by strict concavity; redundant statistics may make its parameters non-unique. Boundary constraints may require infinite-parameter limits or a smaller support.

> [!proof]
> Differentiate $-\sum_gp_g\log p_g+\alpha(\sum_gp_g-1)+\sum_a\beta_a(\sum_gp_gx_a(g)-x_a^*)$ with respect to $p_g$. The stationary condition gives $\log p_g=\alpha-1+\beta\cdot x(g)$. Normalisation supplies $Z$. Concavity makes an interior stationary solution the maximum. A negative-exponent convention merely changes the parameter signs.

> [!theorem] Derivatives and moment fitting
> $$\nabla\log Z=\mathbb E_\beta[x],\qquad\nabla^2\log Z=\operatorname{Cov}_\beta(x).$$
> For one observed graph, $\ell(\beta)=\beta\cdot x(g^*)-\log Z(\beta)$ has score $x(g^*)-\mathbb E_\beta[x]$. Thus interior maximum-likelihood fitting solves moment matching. These identities follow by differentiating finite sums.

With the single statistic $L$ on all simple graphs, $Z=(1+e^\beta)^Y$ and $q=e^\beta/(1+e^\beta)$: this is ER. If $L$ is fixed by the support, adding $\beta L$ changes no relative weights and cannot fit a new feature.

## Clustering beyond degrees
On the simple fixed-degree space, take $p_\beta(g)\propto e^{\beta C(g)}$. A symmetric swap proposal has acceptance $\min(1,e^{\beta\Delta C})$. The partition function cancels for graph moves at fixed $\beta$, but not for comparing different $\beta$ values.

Use the `metropolis` and `swap_proposal` definitions from [[Monte Carlo sampling#Python]] before the following snippet.

> [!code] Estimate the moment curve
> ```python
> import networkx as nx
> import numpy as np
>
> G = nx.karate_club_graph()
> observed_C = nx.transitivity(G)
> curve = []
> for j, beta in enumerate([0.0, 5.0, 10.0, 20.0]):
>     draws, trace = metropolis(
>         G, swap_proposal, lambda h: beta * nx.transitivity(h),
>         steps=2000, burn=500, lag=20, seed=5441+j)
>     c = np.array([nx.transitivity(h) for h in draws])
>     curve.append((beta, c.mean(), c.std(ddof=1)))
> print('Observed clustering:', observed_C)
> print(curve)
> ```
> These short runs demonstrate the computation, not a validated fit. Lengthen runs and compare starts; refine the grid where mean clustering matches the observation, then estimate uncertainty at the fitted parameter.

The exact one-statistic curve is nondecreasing because $d\mathbb E_\beta[C]/d\beta=\operatorname{Var}_\beta(C)\ge0$. A noisy non-monotone estimate can signal Monte Carlo error or poor mixing. Fitted samples need not each have exactly the observed clustering.

The tutorial’s targets proportional to $C$ and $C^{10}$ are different from $e^{\beta C}$. They assign zero mass to zero-clustering graphs. None samples scalar clustering values uniformly: the number of graphs with each value matters. Ten disjoint $K_5$ graphs demonstrate that degree four and clustering one are possible on 50 vertices when disconnection is allowed.

After fitting degrees and expected clustering, compare the empirical **maximum** betweenness with maxima computed separately in each sampled graph. This tests a new statistic under the fitted ensemble; it does not establish a causal explanation for individual behaviour.

> [!reference]- Sources
> Lecture Week 6; Jenny’s notes Week 6. Tutorials 6, graph weighting and November 17 example; Tutorials 3–4, null comparisons. Newman Chapters 11–12 provide ensemble context; the maximum-entropy/MH derivation follows the lecture.
