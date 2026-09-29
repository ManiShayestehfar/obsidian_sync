---
tags: [methods]
---

# Monte Carlo sampling

MCMC constructs correlated states whose long-run distribution is a chosen target. It can sample graphs, real numbers or block allocations; the state space must be specified each time.

> [!definition] Transition and stationarity
> On a finite state space $\Omega$, a transition kernel $W(g,h)\ge0$ satisfies $\sum_hW(g,h)=1$. A probability law $\pi$ is stationary if $\pi(h)=\sum_g\pi(g)W(g,h)$. **Detailed balance** requires
> $$\pi(g)W(g,h)=\pi(h)W(h,g).$$

> [!theorem] Finite-chain convergence
> An irreducible, aperiodic finite chain converges from every initial state to its unique stationary distribution. Detailed balance is sufficient for stationarity, but not necessary. Reachability alone is not aperiodicity.

> [!proof] Stationarity from detailed balance
> Sum over $g$: $\sum_g\pi(g)W(g,h)=\pi(h)\sum_gW(h,g)=\pi(h)$. This proves stationarity, not by itself irreducibility or convergence.

Conditioning by rejection can be correct but impractical. Uniform all-graph sampling gives $L\sim\mathrm{Binomial}(Y,1/2)$, so retaining only a prescribed sparse edge count is a rare event. Moves designed to remain within the constrained state space avoid repeatedly generating inadmissible graphs.

## Metropolis–Hastings
Propose $h$ from $Q(h\mid g)$ and accept with
$$a(g,h)=\min\!\left(1,\frac{\pi(h)Q(g\mid h)}{\pi(g)Q(h\mid g)}\right).$$
Stay at $g$ on rejection. For positive denominators, the accepted probability flow is the minimum of the forward and reverse proposed flows, proving detailed balance. Handle zero target mass explicitly; initialise in the support. Symmetric proposals cancel $Q$, and a common target normaliser cancels as well.

| Target and move | Invariant | Important detail |
| --- | --- | --- |
| Reset a uniform dyad to fair Bernoulli | Vertex set | Uniform all-graph target; self-transitions allowed |
| Remove a uniform edge, add a uniform current non-edge | Vertex set and $L$ | Removed edge may be re-added |
| One symmetric double-edge swap attempt | Every degree | Reject loops and repeated edges without retrying |
| One-vertex block reassignment | Fixed data graph; group count if enforced | Reject moves emptying a required group |

Pure edge **flipping** has period two because it alternates edge-count parity. A holding probability removes this obstruction. Degree-preserving does not mean connectivity-preserving.

> [!warning] Count rejected attempts
> The departure-only jump chain generally has stationary mass proportional to $\pi(g)e(g)$, where $e(g)$ is the probability of leaving $g$. It underrepresents sticky states. A routine that retries until a successful swap is not automatically the symmetric one-attempt proposal used in an MH proof.

## Python
> [!code] Symmetric proposals and log-space Metropolis
> ```python
> import networkx as nx
> import numpy as np
>
> def resample_dyad(g, rng):
>     h = g.copy()
>     if len(h) < 2:
>         return h
>     vertices = list(h)
>     i, j = rng.choice(len(vertices), size=2, replace=False)
>     u, v = vertices[i], vertices[j]
>     if rng.integers(2):
>         h.add_edge(u, v)
>     elif h.has_edge(u, v):
>         h.remove_edge(u, v)
>     return h
>
> def replace_edge(g, rng):
>     h = g.copy()
>     edges = list(h.edges())
>     if not edges:
>         return h
>     h.remove_edge(*edges[rng.integers(len(edges))])
>     absent = list(nx.non_edges(h))
>     h.add_edge(*absent[rng.integers(len(absent))])
>     return h
>
> def swap_proposal(g, rng):
>     h = g.copy()
>     edges = list(g.edges())
>     if len(edges) < 2:
>         return h
>     a, b = rng.choice(len(edges), size=2, replace=False)
>     u, v = edges[a]
>     x, y = edges[b]
>     if rng.integers(2):
>         x, y = y, x
>     if len({u, v, x, y}) < 4:
>         return h
>     if g.has_edge(u, x) or g.has_edge(v, y):
>         return h
>     h.remove_edges_from([(u, v), (x, y)])
>     h.add_edges_from([(u, x), (v, y)])
>     return h
>
> def metropolis(g0, proposal, log_target, steps=2000,
>                burn=500, lag=10, seed=5441):
>     if not (0 <= burn < steps) or lag < 1:
>         raise ValueError('Require 0 <= burn < steps and lag >= 1')
>     rng = np.random.default_rng(seed)
>     g = g0.copy()
>     logp = float(log_target(g))
>     if not np.isfinite(logp):
>         raise ValueError('Initial state must have finite log density')
>     samples, trace = [], []
>     for t in range(1, steps + 1):
>         # Explicit laziness preserves the target and removes periodicity.
>         if rng.random() < 0.5:
>             h = proposal(g, rng)
>             logh = float(log_target(h))
>             if np.isnan(logh) or np.isposinf(logh):
>                 raise ValueError('Invalid log density')
>             if logh >= logp or rng.random() < np.exp(logh - logp):
>                 g, logp = h, logh
>         trace.append(nx.transitivity(g))
>         if t > burn and (t - burn) % lag == 0:
>             samples.append(g.copy())  # retain repeated states
>     return samples, np.asarray(trace)
>
> G = nx.karate_club_graph()
> samples, trace = metropolis(G, swap_proposal, lambda h: 0.0)
> assert all(dict(h.degree()) == dict(G.degree()) for h in samples)
> ```
> For simple undirected graphs, each swap chooses an unordered edge pair uniformly and one of its two cross-matchings with probability $1/2$. A valid move and its reverse have equal proposal probability. The code favours clarity over speed: copying graphs and enumerating edges/non-edges is expensive.

## Burn-in and uncertainty
Burn-in removes initial transients; lag is the number of attempted updates between stored observations. A knee in a plot does not certify mixing. Different observables may have different correlation times, and a flat trace can indicate entrapment.

For independent samples $X_1,\ldots,X_R$, ensemble standard deviation $s$ measures variability across graphs; standard error $s/\sqrt R$ measures uncertainty in the estimated mean. Compare one empirical graph to the former distribution. For correlated stationary samples,
$$\tau_{int}=1+2\sum_{t\ge1}\rho(t),\qquad R_{eff}\approx R/\tau_{int},\qquad \mathrm{SE}(\bar X)\approx s/\sqrt{R_{eff}},$$
when the covariance sum and asymptotic approximation are valid. Estimate correlations or use batch means and multiple starts. Thinning does not fix a biased start. Discard by **simulation time**, not by a row number that ignores measurement spacing.

The interval tutorial illustrates the same ideas: a symmetric wrapped proposal of width $0.01$ can have high acceptance and slow movement. Targets $2x$ and $3x$ on $[0,1]$ normalise to the same law with mean $2/3$; $x^2$ normalises to $3x^2$ and has mean $3/4$.

> [!code] A wrapped interval proposal
> ```python
> import numpy as np
>
> def sample_interval(power=1, width=0.01, steps=10000, seed=5441):
>     # Density proportional to x**power on (0,1); power >= 0.
>     if power < 0 or not 0 < width <= 1 or steps < 1:
>         raise ValueError('Invalid power, width or number of steps')
>     rng = np.random.default_rng(seed)
>     x = 0.5
>     samples = []
>     for _ in range(steps):
>         y = (x + rng.uniform(-width, width)) % 1.0
>         if y > 0:
>             log_ratio = power * (np.log(y) - np.log(x))
>             if log_ratio >= 0 or rng.random() < np.exp(log_ratio):
>                 x = y
>         samples.append(x)
>     return np.asarray(samples)
>
> interval_draws = sample_interval()
> ```
> Wrapping retains a symmetric proposal; clipping to the endpoints would alter it. Rejections remain in the returned sequence. A narrow proposal can require much longer runs than this demonstration; the exact mean is $(a+1)/(a+2)$ for power $a$.

Use this machinery for [[Maximum entropy and ERGMs]] or allocation-space inference in [[Stochastic block models]].

> [!reference]- Sources
> Lectures Weeks 4, 6 and 7; Jenny’s notes Weeks 4, 6–7. Tutorials 4 and 6 (including the single-attempt correction), and Tutorial 7. [NetworkX successful-swap API](https://networkx.org/documentation/stable/reference/algorithms/generated/networkx.algorithms.swap.double_edge_swap.html). Convergence and uncertainty formulas are explanatory mathematical additions.
