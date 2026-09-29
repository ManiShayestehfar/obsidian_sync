---
tags: [models]
---

# Configuration model

> [!definition] Uniform stub pairing
> Assign vertex $i$ exactly $k_i$ labelled half-edges, or stubs, and pair the $2L=\sum_i k_i$ stubs uniformly. The sum must be even. Pairing preserves all degrees when loops count twice, but may create loops and parallel edges.
>
> This multigraph model differs from the uniform distribution on **simple** graphs with the given labelled degree sequence. A simple realisation requires the sequence to be graphical; even total degree alone is insufficient.

> [!theorem] Expected edge multiplicity
> For distinct $i,j$,
> $$\mathbb E[M_{ij}]=\frac{k_i k_j}{2L-1}.$$
> Each of the $k_i$ stubs chooses a uniformly distributed partner among the other $2L-1$ stubs, of which $k_j$ belong to $j$. Sum the corresponding indicators. This is an expected multiplicity, not generally $\Pr(M_{ij}\ge1)$.

Erasing loops and merging repeated edges changes degrees. It cannot be used as an exact degree-preserving null. Rejection of the **entire** pairing until it is simple does yield a uniform simple graph: every simple graph with this labelled degree sequence corresponds to $\prod_i k_i!$ stub pairings. Acceptance may be prohibitively rare.

## Excess degree and branching
> [!definition] Excess-degree law
> Arriving along a uniform edge biases the reached degree to $kp_k/\langle k\rangle$. The number of remaining edges is $k-1$, with mean
> $$\kappa=\frac{\langle k(k-1)\rangle}{\langle k\rangle}=\frac{\langle k^2\rangle-\langle k\rangle}{\langle k\rangle}.$$
> Define $G_0(s)=\sum_kp_ks^k$ and $G_1(s)=G_0'(s)/G_0'(1)$ for positive mean degree.

In the uncorrelated locally tree-like branching approximation, solve
$$u=G_1(u),\qquad S=1-G_0(u),$$
using the smallest extinction root. The supercritical branching condition is $\kappa>1$, equivalently $\langle k^2\rangle/\langle k\rangle>2$. These equations describe the branching approximation; applying them as a graph-sequence limit requires convergence of the degree law and appropriate moment/maximal-degree control. Equality is a critical or degenerate boundary; a pure degree-two distribution needs special care.

> [!proof] Why the second moment enters
> An edge reaches degree $k$ with probability $kp_k/\langle k\rangle$ and then offers $k-1$ further branches. Averaging the offspring count gives $\kappa$. The offspring generating function is $G_1$, so independent branch extinction gives $u=G_1(u)$; an unconditioned root has law $p_k$, giving failure probability $G_0(u)$.

Poisson degrees have $\kappa=c$; $k$-regular degrees have $\kappa=k-1$. This explains why ER shell growth uses $c$, not $c-1$.

Under the uncorrelated sparse approximation with controlled moments,
$$C\approx\frac{(\langle k^2\rangle-\langle k\rangle)^2}{N\langle k\rangle^3}.$$
Heavy tails and simplicity constraints can invalidate this approximation. A formula exceeding one signals a failed regime, not clustering above one.

> [!code] Observe the effect of simplifying a pairing
> ```python
> import networkx as nx
>
> empirical = nx.karate_club_graph()
> k = [d for _, d in empirical.degree()]
> assert nx.is_graphical(k)
> raw = nx.configuration_model(k, seed=5441)
> erased = nx.Graph(raw)
> erased.remove_edges_from(nx.selfloop_edges(erased))
> assert [raw.degree(i) for i in range(len(k))] == k
> lost_edges = raw.number_of_edges() - erased.number_of_edges()
> print(lost_edges, [erased.degree(i) for i in range(len(k))] == k)
> ```

Use the single-attempt swaps in [[Monte Carlo sampling]] for simple fixed-degree sampling. The tutorial’s core lesson is to compare clustering beyond what the degree sequence explains, while recognising that the erased configuration model answers a different question. See [[Percolation and robustness]] for thinning this ensemble.

> [!reference]- Sources
> Lecture Week 4; Jenny’s notes Weeks 4, 10 and 13. Newman §§12.1–12.6 and 12.10. Tutorial 4, stub pairing versus simple fixed-degree rewiring.
