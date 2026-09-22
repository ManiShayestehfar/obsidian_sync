---
type: study-note
tags: [DATA5441]
---

# MCMC and detailed balance

[[00_HOME]]

Sources: Weeks 4, 6 and 7; Tutorials 4 and 6.

A Markov chain samples states in a specified support. For a finite chain, irreducibility plus aperiodicity gives convergence to its unique stationary law. Detailed balance is a convenient sufficient condition for that law:
$$\pi(g)W(g,h)=\pi(h)W(h,g).$$
Summing over $g$ gives stationarity because $\sum_gW(h,g)=1$. Stationarity alone does not ensure convergence from every start.

With proposal $Q(h\mid g)$, use
$$a(g,h)=\min\left(1,\frac{\pi(h)Q(g\mid h)}{\pi(g)Q(h\mid g)}\right).$$
For symmetric proposals, only the target ratio remains. If $\pi\propto e^{-F}$, acceptance is $\min(1,e^{-\Delta F})$; for an ERGM with positive exponent $\pi\propto e^{\beta x}$, it is $\min(1,e^{\beta\Delta x})$. The signs come from the target, not from a memorised universal rule.

**Three graph moves:**

1. Choose a dyad and reset it to Bernoulli$(1/2)$: uniform simple graphs with fixed $N$.
2. Remove a uniformly selected existing edge, then add a uniformly selected current non-edge: uniform fixed $N,L$. Re-adding the removed edge supplies a self-loop in graph space.
3. Propose a symmetric exchange of two edges’ endpoints; reject loops and duplicates: degree-preserving simple-graph sampling, subject to connectivity of the move space and aperiodicity.

Pure edge flipping has period two because edge-count parity changes every step. Laziness (holding with positive probability) repairs periodicity without changing a stationary law.

**Why retain rejections?** If $e(g)$ is the probability of leaving $g$, the chain observed only at actual departures has stationary mass proportional to $\pi(g)e(g)$, under usual jump-chain assumptions. It underrepresents sticky states. Sampling only successful swaps can therefore change the target. NetworkX’s `double_edge_swap` counts successful swaps; do not assume its successful-swap kernel is the symmetric one-attempt kernel used in a Metropolis derivation. See the official [API description](https://networkx.org/documentation/stable/reference/algorithms/generated/networkx.algorithms.swap.double_edge_swap.html).

**Numerical implementation:** evaluate log ratios. Accept when $\log U<\min(0,\log R)$, avoiding overflow. Treat zero target density and impossible reverse proposals explicitly.
