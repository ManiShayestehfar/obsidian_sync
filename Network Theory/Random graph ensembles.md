---
tags: [models]
---

# Random graph ensembles

> [!definition] An ensemble
> A random-graph model is a state space $\Omega$ together with probabilities $p(g)\ge0$ summing to one. Specify whether states are labelled graphs, isomorphism classes, multigraphs or simple graphs. Uniformity depends on this choice.

For a fixed labelled vertex set there are $Y=\binom N2$ independent binary edge choices, hence $2^Y$ simple undirected graphs. Exactly $L$ edges can be placed in $\binom YL$ ways.

| Ensemble | Fixed | How probability is assigned |
| --- | --- | --- |
| All simple graphs, uniform | $N$ | $2^{-Y}$ per graph; edges Bernoulli$(1/2)$ |
| $G(N,q)$ | $N,q$ | Independent Bernoulli$(q)$ dyads |
| $G(N,L)$ | $N,L$ | Uniform among graphs with exactly $L$ edges |
| Simple fixed-degree | Each labelled degree $k_i$ | Uniform over admissible wirings |
| Stub configuration | Stub counts $k_i$ | Uniform pairings; defects allowed |
| ERGM | Support and sufficient statistics | Exponential weights |
| SBM | Blocks and connection probabilities | Independent edges conditional on blocks |

The simple constrained spaces satisfy $\Omega_{\mathbf k}\subseteq\Omega_L\subseteq\Omega_N$. Adding constraints changes the null question: is a pattern unusual given size, given density, or given every degree?

> [!theorem] Conditioning ER on edge count
> For $0<q<1$, conditioning $G(N,q)$ on $L(g)=\ell$ gives the uniform $G(N,\ell)$ law.

> [!proof]
> Every graph with $\ell$ edges has the same probability $q^\ell(1-q)^{Y-\ell}$. Dividing by $\binom Y\ell q^\ell(1-q)^{Y-\ell}$ gives $1/\binom Y\ell$.

Uniform all-graph sampling produces $L\sim\mathrm{Binomial}(Y,1/2)$ with standard deviation $\sqrt Y/2$. Thus density fluctuations are order $Y^{-1/2}$: uniform graph sampling overwhelmingly produces dense graphs near density one half, despite allowing sparse graphs.

> [!theorem] Large-deviation form
> For fixed $0<a<1$ along values with $aY$ integer, Stirling’s formula gives
> $$\log\Pr(L=aY)=-YI(a)+O(\log Y),\qquad I(a)=a\log(2a)+(1-a)\log(2(1-a)).$$
> $I(a)\ge0$ with equality only at $a=1/2$. This makes the concentration more precise than saying every graph has about half the possible edges.

> [!code] Match density in expectation or exactly
> ```python
> import networkx as nx
>
> G = nx.karate_club_graph()
> N, L = len(G), G.number_of_edges()
> q = 2 * L / (N * (N - 1))
> expected_count_model = nx.gnp_random_graph(N, q, seed=5441)
> fixed_count_model = nx.gnm_random_graph(N, L, seed=5441)
> assert fixed_count_model.number_of_edges() == L
> ```

Matching one statistic is not evidence that the model explains all structure. Compare another statistic with the **ensemble distribution**, not just the uncertainty in its estimated mean. Graph draws from a fitted density model do not have to reproduce $L$ exactly; draws from a fixed-degree model must reproduce every $k_i$ exactly.

[[Erdos-Renyi graphs]], [[Configuration model]], [[Small-world networks]] and [[Preferential attachment]] address different structural mechanisms. [[Monte Carlo sampling]] explains how to sample when independent direct generation is unavailable.

> [!reference]- Sources
> Lectures Weeks 3–4 and 6; Jenny’s notes Weeks 3–4. Newman Chapters 11–12. Tutorials 3–4, comparison of constrained null models.
