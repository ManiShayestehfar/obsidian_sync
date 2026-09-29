---
tags: [inference]
---

# Stochastic block models

> [!definition] Bernoulli SBM
> Assign each of $N$ vertices to a nonempty block $b_i\in\{0,\ldots,B-1\}$. Given this allocation and a symmetric matrix $p_{rs}\in[0,1]$, distinct dyads are independent:
> $$A_{ij}\mid b,p\sim\mathrm{Bernoulli}(p_{b_i b_j}),\qquad i<j.$$
> $B=1$ gives ER. Large diagonal and small off-diagonal probabilities describe assortative communities. With two groups, $p_{11}>p_{12}>p_{22}$ describes one core–periphery pattern. Zero diagonal block probabilities give a random bipartite graph.

Let $n_r$ be block size, $y_{rr}=\binom{n_r}2$ and $y_{rs}=n_rn_s$ for $r<s$. Let $l_{rs}$ count edges of each type, counting within-block edges once.

> [!theorem] Likelihood and fitted probabilities
> For one observed labelled graph,
> $$\ell(b,p)=\log P(A\mid b,p)=\sum_{r\le s}\left[l_{rs}\log p_{rs}+(y_{rs}-l_{rs})\log(1-p_{rs})\right].$$
> When $y_{rs}>0$, its blockwise MLE is $\widehat p_{rs}=l_{rs}/y_{rs}$. Values zero and one are valid boundary estimates. If $y_{rs}=0$, that parameter is unidentified.

> [!proof]
> There are $l$ edge factors and $y-l$ non-edge factors in a block pair. For $0<l<y$, differentiate: $l/p-(y-l)/(1-p)=0$ gives $p=l/y$; the second derivative is negative. For $l=0$ or $l=y$, monotonicity gives the boundary maximum. If $y=0$, the likelihood factor is one for every $p$. No binomial coefficient appears because the observation is a particular graph, not just its aggregate edge count.

Define the profile objective $F(b)=-\ell(b,\widehat p(b))$. With sizes three and two and edge counts $(l_{11},l_{12},l_{22})=(2,1,0)$, fitted probabilities are $(2/3,1/6,0)$ and $F\approx4.6129$.

## Python
> [!code] Fit any nonempty block allocation
> ```python
> import networkx as nx
> import numpy as np
>
> def fit_sbm(g, labels):
>     # labels is a dict keyed by actual vertex IDs, not array positions.
>     if g.is_directed() or g.is_multigraph() or nx.number_of_selfloops(g):
>         raise ValueError('Require a simple undirected loop-free graph')
>     if not len(g) or set(labels) != set(g):
>         raise ValueError('Provide one label per vertex in a nonempty graph')
>     groups = list(dict.fromkeys(labels[v] for v in g))
>     position = {label: r for r, label in enumerate(groups)}
>     b = {v: position[labels[v]] for v in g}
>     B = len(groups)
>     sizes = np.bincount(list(b.values()), minlength=B)
>     y = np.outer(sizes, sizes)
>     np.fill_diagonal(y, sizes * (sizes - 1) // 2)
>     ell = np.zeros((B, B), dtype=int)
>     for u, v in g.edges():
>         r, s = sorted((b[u], b[v]))
>         ell[r, s] += 1
>     P = np.full((B, B), np.nan)  # no-dyad parameters are unidentified
>     nll = 0.0
>     for r in range(B):
>         for s in range(r, B):
>             total, edges = int(y[r, s]), int(ell[r, s])
>             if total == 0:
>                 continue
>             p = edges / total
>             P[r, s] = P[s, r] = p
>             if edges:
>                 nll -= edges * np.log(p)
>             if edges < total:
>                 nll -= (total - edges) * np.log1p(-p)
>     return nll, P, sizes
>
> G = nx.karate_club_graph()
> labels = {v: G.nodes[v]['club'] for v in G}
> F, P, sizes = fit_sbm(G, labels)
> print(F, P, sizes)
> ```
> This handles singleton blocks and arbitrary vertex IDs. It also avoids the original notebook’s list/NumPy `.count` mismatch.

> [!algorithm] Greedy search and Metropolis moves
> Greedy search evaluates all allowed one-vertex moves, makes a best strict improvement and stops when none exists. Enforce nonempty groups if $B$ is fixed; use multiple starts and handle ties explicitly.
>
> For symmetric random reassignment proposals, sampling $\pi_\beta(b)\propto e^{-\beta F(b)}$ uses $a=\min(1,e^{-\beta\Delta F})$. At $\beta=1$ this samples a profile-likelihood target, not automatically a Bayesian posterior. As $\beta\to\infty$, worsening moves are rejected but ties remain accepted. Increasing $\beta$ is simulated annealing; a finite schedule gives no global-optimality guarantee.

> [!code] Fixed-B optimisation and sampling
> ```python
> # Requires fit_sbm from the preceding code box.
>
> def greedy_sbm(g, initial):
>     b = dict(initial)
>     groups = list(dict.fromkeys(b.values()))
>     score = fit_sbm(g, b)[0]
>     while True:
>         best, best_score = None, score
>         for v in g:
>             if sum(x == b[v] for x in b.values()) == 1:
>                 continue
>             for r in groups:
>                 if r == b[v]:
>                     continue
>                 candidate = dict(b)
>                 candidate[v] = r
>                 value = fit_sbm(g, candidate)[0]
>                 if value < best_score - 1e-12:
>                     best, best_score = candidate, value
>         if best is None:
>             return b, score
>         b, score = best, best_score
>
> def sample_allocations(g, initial, steps=500, beta=1.0, seed=13):
>     if beta < 0:
>         raise ValueError('beta must be nonnegative')
>     rng = np.random.default_rng(seed)
>     b, vertices = dict(initial), list(g)
>     groups = list(dict.fromkeys(b.values()))
>     score = fit_sbm(g, b)[0]
>     history = []
>     for _ in range(steps):
>         if len(groups) > 1 and rng.random() < 0.5:
>             v = vertices[rng.integers(len(vertices))]
>             if sum(x == b[v] for x in b.values()) > 1:
>                 choices = [r for r in groups if r != b[v]]
>                 candidate = dict(b)
>                 candidate[v] = choices[rng.integers(len(choices))]
>                 value = fit_sbm(g, candidate)[0]
>                 delta = value - score
>                 if delta <= 0 or rng.random() < np.exp(-beta*delta):
>                     b, score = candidate, value
>         history.append((dict(b), score))
>     return history
>
> best_labels, best_F = greedy_sbm(G, labels)
> history = sample_allocations(G, labels)
> print(best_F, min(value for _, value in history))
> ```
> This greedy version breaks ties by iteration order. The sampler retains rejected states and adds holding. At $B=N$ the single-node nonempty-group move is frozen; do not claim it explores all labelled allocations.

## Interpreting inferred groups
An ordinary SBM may prefer a hub/non-hub split over a known social division because vertices within a block share an expected connectivity pattern. A degree-corrected Poisson SBM instead uses intensities $\theta_i\theta_j\omega_{b_i b_j}$, with identifiability constraints. Intensities are expected multiplicities, not unrestricted Bernoulli probabilities.

Compare allocations up to label permutation. For binary assignments the minimum Hamming mismatch is $\min(d,N-d)$; a contingency table helps for larger $B$. Generate the tutorial’s planted example with `nx.stochastic_block_model([20, 50], [[0.15, 0.01], [0.01, 0.20]], seed=13)`: the old cell used 5441 despite asking for 13.

The best-partition objective and selection of $B$ are addressed in [[Statistical inference and model selection]].

> [!reference]- Sources
> Lecture Week 7; Jenny’s notes Week 7. Newman §12.11.6 and §14.4 (including distinct Poisson/degree-corrected formulations). Tutorial 7, fixed partitions, greedy moves, barriers, MCMC and planted blocks. [NetworkX SBM generator](https://networkx.org/documentation/stable/reference/generated/networkx.generators.community.stochastic_block_model.html).
