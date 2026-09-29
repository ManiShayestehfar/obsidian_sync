---
tags: [models]
---

# Small-world networks

A small-world property concerns short graph distances relative to network size. The Watts–Strogatz model additionally seeks substantial local clustering in a sparse network; short distance alone does not imply triangle closure.

> [!definition] Watts–Strogatz construction
> Put $N$ vertices on a ring, join each to its $Q$ nearest neighbours on each side, and independently select original edges for rewiring with probability $p$. Initially $k_i=2Q$ and $L=NQ$. Specify whether one endpoint or both are rewired, and how loops and duplicates are excluded. Standard rewiring preserves edge count, not each degree.

> [!theorem] Ring baseline
> For $Q\ge1$ and $N>3Q$, avoiding extra wrap-around triangles,
> $$C(0)=\frac{3(Q-1)}{2(2Q-1)}.$$
> The diameter is $\lceil\lfloor N/2\rfloor/Q\rceil$.

> [!proof]
> A vertex has $2Q$ neighbours. Their induced subgraph contains $3Q(Q-1)/2$ edges, counted by the two same-side cliques and eligible cross-side pairs. Dividing by $\binom{2Q}2$ gives clustering. Moving along the ring by at most $Q$ positions per step gives the distance and diameter formula.

The approximation $C(p)\approx C(0)(1-p)^3$ counts surviving original triangles, ignoring new triangles and changed local denominators. A small number of shortcuts can shorten many routes. The regime $pNQ\gg1$ and $p\ll1$ motivates a finite-size crossover, but does not prove logarithmic distance for every scaling $p=p(N)$.

> [!code] Sweep rewiring with an explicit distance convention
> ```python
> import networkx as nx
> import numpy as np
>
> N, Q = 200, 3
> rows = []
> for p in [0.0, 0.01, 0.05, 0.2, 1.0]:
>     for seed in range(5):
>         G = nx.watts_strogatz_graph(N, 2*Q, p, seed=seed)
>         H = G.subgraph(max(nx.connected_components(G), key=len))
>         rows.append((p, seed, nx.average_clustering(G),
>                      len(H)/N, nx.average_shortest_path_length(H)))
> print(np.asarray(rows))
> ```
> Check the retained component fraction before comparing distances. Conditioning on connected graphs would define a different experiment.

The lattice edge-swap tutorial is a distinct model: swaps preserve every degree, whereas WS usually does not. Report whether time counts attempted or successful rewiring steps; a normalisation such as $2t/L$ has meaning only after that choice.

## Kleinberg: finding a short route
Kleinberg separates **existence** of short routes from **decentralised navigability**. In a finite $d$-dimensional grid, retain local lattice links and add long-range contacts with destination probability proportional to $r^{-\alpha}$, where $r$ is lattice distance. A greedy router uses positions and the current vertex’s contacts rather than a global shortest-path computation.

In the standard two-dimensional model, $\alpha=2$ yields expected greedy delivery time $O((\log n)^2)$ for grid side length $n$; different exponents have poorer polynomial lower bounds under that model’s information assumptions. The matching exponent is dimension $d$ in the analogous formulation.

> [!warning] Local links and finite connectivity
> When the model retains all nearest-neighbour lattice links, that finite underlying grid is already connected: an $N\to\infty$ argument is unnecessary. In a directed construction with both local directions, it is strongly connected. If a parameter removes local links entirely, this reasoning no longer applies. Kleinberg’s local-range parameter must not be confused with WS’s rewiring probability.

[[Paths and components]] defines the distance conventions; [[Preferential attachment]] addresses a different phenomenon, broad degrees through growth.

> [!reference]- Sources
> Lecture Week 5 pp.1–6, including the supplied Kleinberg article; Jenny’s notes Week 5. Newman §12.11.8 and §18.3. Tutorial 5, WS and lattice-rewiring experiments.
