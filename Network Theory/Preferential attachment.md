---
tags: [models]
---

# Preferential attachment

> [!definition] Barabási–Albert growth
> Start from a seed graph. At each step add one vertex and $m\ge1$ links to old vertices, favouring targets proportionally to their current degree. Specify the seed and how distinct targets are selected when requiring a simple graph. Then
> $$N(t)=N_0+t,\quad L(t)=L_0+mt,\quad\langle k\rangle\to2m.$$
> A connected seed remains connected if every arriving vertex receives a link. An isolated seed vertex with zero attachment weight is a separate concern.

> [!derivation] Continuum exponent
> At large times the total degree is approximately $2mt$, so the mean-growth approximation for a vertex born at $t_i$ is
> $$\frac{dk_i}{dt}\approx\frac{mk_i}{2mt}=\frac{k_i}{2t},\qquad k_i(t_i)=m.$$
> Integration gives $k_i(t)\approx m\sqrt{t/t_i}$. Approximating arrival times as uniform on $(0,t)$ yields
> $$\Pr(K\ge k)\approx\Pr\!\left(t_i\le\frac{m^2t}{k^2}\right)\approx\frac{m^2}{k^2},$$
> so the continuous density is $-\frac{d}{dk}\Pr(K\ge k)\approx2m^2k^{-3}$. The survival derivative needs a minus sign. Individual degrees fluctuate; this is not an exact trajectory or exact small-degree distribution.

The standard rate-equation solution has limiting degree proportions
$$p_k=\frac{2m(m+1)}{k(k+1)(k+2)},\qquad k\ge m,$$
with the same exponent three. The seed and finite-time process still affect a finite network.

## What the mechanism explains
Growth plus cumulative advantage produces broad degrees and an early-arrival advantage in expectation. It does not prove that every old vertex outranks every young one. Basic BA fixes the exponent, and clustering does not generally remain positive as the graph grows. For $m=1$ with a tree seed, the graph is a tree and clustering is exactly zero.

Extensions change the attachment kernel, incorporate ageing or fitness, copy neighbours, or close triangles. Their effects depend on the chosen rule; a power law alone does not identify preferential attachment as the generating process.

> [!code] Compare with density-matched ER
> ```python
> import networkx as nx
> import numpy as np
>
> N, m = 500, 2
> ba = nx.barabasi_albert_graph(N, m, seed=5441)
> q = 2 * ba.number_of_edges() / (N * (N - 1))
> er = nx.gnp_random_graph(N, q, seed=5441)
>
> def degree_summary(g):
>     d = np.array([k for _, k in g.degree()], dtype=float)
>     return {'mean': d.mean(), 'sd': d.std(ddof=0),
>             'relative_sd': d.std(ddof=0)/d.mean(),
>             'transitivity': nx.transitivity(g)}
>
> print(degree_summary(ba), degree_summary(er))
> ```

Choosing $m\approx\langle k\rangle/2$ only approximately matches a target graph, since $m$ is integer and seed edges matter. Matching ER to a realised BA graph uses the realised $L$ as above. Repeat independent realisations before attributing a difference to a model rather than sampling variation.

The political-blog tutorial compares empirical, Poisson, ER and BA degrees after making the data simple and undirected. That transformation and the model fit are part of the interpretation. Use [[Power laws]] for tail diagnostics and [[Small-world networks]] when the main target is clustering plus short routes.

> [!reference]- Sources
> Lecture Week 5 pp.10–12; Jenny’s notes Week 5. Newman §§13.1–13.4 (including the standard degree-distribution derivation). Tutorial 5, BA/ER and political-blog comparisons.
