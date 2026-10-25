---
tags: [dynamics]
---

# Percolation and robustness

Robustness asks how much function remains after vertices or links fail. Connectivity provides a first measure of function: a surviving path permits communication, while fragmentation can isolate many vertices before every edge disappears. The model must distinguish random failure from deliberate attack.

## Retention, removal and the observable

> [!definition] Site and bond percolation
> In **bond percolation**, each edge is retained independently with probability $p$; in **site percolation**, each vertex is retained independently with probability $p$, together with edges between surviving vertices. Write $q=1-p$ for removal probability. Here $p$ is not the ER graph-generation probability.
>
> For an original graph of size $N_0$, define $K_1=|C_1|/N_0$, where $C_1$ is the largest surviving component. Under site removal, deleted vertices remain in the denominator. Its diameter measures routes within $C_1$, not within the entire disconnected graph.

Couple different retention values using the same uniform random number per edge or vertex. Keeping an item when its mark exceeds $q$ produces nested surviving graphs. Largest-component **size** then cannot increase with removal; largest-component **diameter** can increase, decrease or jump as the dominant component changes.

## Lattices: geometry matters

![[Assets/tutorial-10-cell-06-plot-1.png|850]]
*Supplied Tutorial 10, cell 6: four-neighbour square-lattice **site** percolation. White sites are absent; colours distinguish occupied clusters, with a crossing cluster shown in black when present.*

| Infinite lattice | Site retention threshold $p_c$ | Bond retention threshold $p_c$ |
| --- | --- | --- |
| Line | $1$ | $1$ |
| Square, four neighbours | $\approx0.592746$ | $1/2$ |
| Triangular | $1/2$ | $2\sin(\pi/18)\approx0.347296$ |
| $k$-regular tree, $k\ge2$ | $1/(k-1)$ | $1/(k-1)$ |

These are infinite-model values. Finite crossing probabilities vary smoothly with $p$ and have sampling error. The eight-neighbour square lattice contains all four-neighbour links, so adding diagonals cannot make percolation harder. Tutorial 10 estimates its site threshold by the finite-size crossing-probability midpoint, finding values near $0.4072$ for its larger grids. A fine parameter grid alone does not establish a matching number of statistically reliable digits.

> [!example]- Estimating a lattice threshold from finite crossings
> ![[Assets/tutorial-10-cell-11-plot-2.png|720]]
> Supplied Tutorial 10, cell 11: crossing frequencies for eight-neighbour grids of increasing side length. The 50% crossing point is a finite-size estimator. Finite sampling and finite-size bias remain even when the parameter grid is fine.

> [!theorem] Existence and rooted survival are different probabilities
> For independent percolation on a countable locally finite graph, existence of **some** infinite open component is unchanged by modifying finitely many occupations. It is a tail event, so Kolmogorov’s zero–one law gives probability zero or one.
>
> The probability that a **specified vertex** lies in an infinite component can instead be strictly between zero and one. A finite-box crossing probability is another distinct quantity.

**Reason.** Removing finitely many vertices or edges from an infinite locally finite connected component leaves finitely many pieces, at least one infinite. Adding finitely many occupations cannot combine finitely many finite pieces into an infinite one. Thus existence is a tail event. The rooted event need not be invariant under a finite change at the root. $\square$

## Branching and the random-graph threshold

Let $p_k$ denote the **original degree distribution**, with positive mean, and let
$$\kappa=\frac{\langle k(k-1)\rangle}{\langle k\rangle}.$$
For an uncorrelated locally tree-like configuration-model limit, following an edge reaches $k$ with probability $kp_k/\langle k\rangle$ and leaves $k-1$ onward opportunities.

> [!theorem] Uniform-failure threshold in the branching model
> The surviving exploration process is supercritical when $p\kappa>1$. If $\kappa>1$,
> $$p_c=\frac{\langle k\rangle}{\langle k^2\rangle-\langle k\rangle},\qquad q_c=1-p_c.$$
> This threshold applies to independent site or bond retention in that asymptotic setting. Finite graphs have rounded transitions; arbitrary clustered or correlated graphs need not follow this moment formula. Equality is the critical/degenerate boundary, not the strict supercritical regime.

**Proof.** A uniform arrival has mean excess degree $\kappa$. Keeping each outward connection, or its destination vertex, independently with probability $p$ gives offspring mean $p\kappa$. The branching process survives with positive probability in the nondegenerate supercritical case. Equivalently, under bond thinning,
$$K'\mid K\sim\mathrm{Binomial}(K,p),\quad\mathbb E[K']=p\mathbb E[K],\quad\mathbb E[K'(K'-1)]=p^2\mathbb E[K(K-1)],$$
so the new excess mean is $p\kappa$ for $p>0$. $\square$

With $G_0,G_1$ from [[Configuration model]], branch failure satisfies $u=1-p+pG_1(u)$. The giant fraction is $1-G_0(u)$ for bond percolation and $p[1-G_0(u)]$ for site percolation relative to original size.

### The regular-tree example

On an infinite $k$-regular tree, $u=1-p+pu^{k-1}$ and the root’s bond-survival probability is $1-u^k$. For $k=3$, the physical nontrivial root is $u=(1-p)/p$ when $p>1/2$. This root quantity differs from the two-branch survival expression in the lecture’s intermediate calculation. A finite depth-five tree has many leaves and is not a finite regular graph with the same boundary-free statistics.

### Worked thresholds from the tutorial

| Original model | Branching prediction for failure threshold |
| --- | --- |
| Sparse ER mean degree $c$ | $q_c=1-1/c$ for $c>1$; $0.75$ at $c=4$, $5/6$ at $c=6$ |
| $k$-regular random graph | $q_c=1-1/(k-1)$; $0.75$ at $k=5$ |
| Half degree 4, half degree $k$ | $q_c=1-(4+k)/(12+k^2-k)$ |
| Suitable finite-mean heavy-tailed sequence with $\langle k^2\rangle\to\infty$ | $p_c\to0$, or $q_c\to1$, within the approximation’s regime |

For the two-point law, $\langle K\rangle=(4+k)/2$ and $\langle K(K-1)\rangle=(12+k^2-k)/2$. At $k=2,4,8,16$, the predicted $q_c$ values are approximately $0.5714,0.6667,0.8235,0.9206$. Graph generation must also respect graphicality and even total degree. Erasing configuration-model defects changes the intended distribution.

A zero limiting retention threshold does not imply a large surviving fraction for every small $p$, nor immunity of a finite graph to failures. BA’s growing second moment motivates the tutorial comparison, but BA structure is not automatically identical to an uncorrelated configuration ensemble.

## Simulating failures and attacks

> [!code]- Nested bond failures with fixed normalisation
> ```python
> import networkx as nx
> import numpy as np
>
> G = nx.random_regular_graph(5, 200, seed=5441)
> rng = np.random.default_rng(5441)
> edges = list(G.edges())
> marks = rng.random(len(edges))
> curve = []
> for q in np.linspace(0, 1, 21):
>     H = nx.empty_graph(list(G))
>     H.add_edges_from(edge for edge, mark in zip(edges, marks) if mark >= q)
>     C = max(nx.connected_components(H), key=len, default=set())
>     diameter = nx.diameter(H.subgraph(C)) if C else np.nan
>     curve.append((q, len(C)/len(G), diameter))
> ```
> Repeat both original-graph generation and failure marks to estimate an ensemble mean and spread. Site failures delete vertices and incident edges; keep the same original-size denominator.

For degree-dependent site retention $\phi_k$, the locally tree-like branching factor becomes
$$R_\phi=\frac{\sum_k k(k-1)p_k\phi_k}{\langle k\rangle}.$$
Removing hubs changes this expression differently from uniform failure. A **static degree attack** ranks original degrees once; an **adaptive attack** reranks as the graph changes. Tutorial 10 uses the static version and removes $\lfloor qN_0\rfloor$ vertices, with random tie-breaking.

![[Assets/tutorial-10-cell-58-plot-1.png|850]]
*Supplied Tutorial 10, cell 58: static attacks on ER and BA examples at two mean degrees. BA breaks apart earlier in this experiment. The diameter peak is a finite-size indicator, not an exact critical-point theorem.*

An empty surviving graph has undefined diameter. The notebook’s final `np.argmax` summary can select the NaN endpoint and incorrectly print a peak at $q=1$; exclude non-finite values or use a suitable finite mask before interpreting a peak.

## For revision

- Keep retention $p$, failure $q$, original size and remaining size distinct.
- Derive $p\kappa=1$ and the two-point threshold; state its locally tree-like assumptions.
- Explain why site and bond models can share a threshold but have different giant fractions, and why random-failure robustness does not imply attack robustness.

> [!reference]- Sources
> Lecture Week 10 pp.1–16, including the lattice table on p.8 and attack examples on pp.14–16. Tutorial 10 §§1–3 and Ex.1.1–3.1. Jenny’s notes Weeks 10, 13. Newman (2018), §§15.1–15.3. Supplied notebook figures are retained; no large failure sweep was rerun. The zero–one discussion clarifies the distinction made in Lecture p.4.
