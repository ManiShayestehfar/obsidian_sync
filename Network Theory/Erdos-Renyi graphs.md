---
tags: [models]
---

# Erdos-Renyi graphs

> [!definition] Independent-edge model
> $G(N,q)$ is the simple labelled graph on $N$ vertices where each of the $Y=\binom N2$ dyads is an edge independently with probability $q$. A particular graph has probability
> $$P(G=g)=q^{L(g)}(1-q)^{Y-L(g)}.$$
> There is no binomial coefficient here; that coefficient belongs to the distribution of the edge count, not the probability of a particular graph.

> [!theorem] Edge and degree distributions
> $L\sim\mathrm{Binomial}(Y,q)$ and $K_i\sim\mathrm{Binomial}(N-1,q)$. Therefore
> $$\mathbb E[K_i]=(N-1)q,\qquad\operatorname{Var}(K_i)=(N-1)q(1-q).$$
> These follow by writing each quantity as a sum of independent edge indicators. Degrees of different vertices are not independent: they share an edge indicator.

The MLE of density is $\widehat q=L/Y$ for $N\ge2$. At fixed $q\in(0,1)$, mean degree grows with $N$ and relative degree variability tends to zero. In the sparse regime $q=c/(N-1)$ with fixed $c>0$, degree converges in distribution to Poisson$(c)$ and relative variability approaches $1/\sqrt c$. Finite-$N$ degrees remain binomial.

> [!proof] Poisson limit
> For each fixed integer $k\ge0$,
> $$\binom{N-1}{k}\left(\frac c{N-1}\right)^k\left(1-\frac c{N-1}\right)^{N-1-k}\longrightarrow e^{-c}\frac{c^k}{k!}.$$
> The first two factors approach $c^k/k!$, and the last approaches $e^{-c}$.

## Giant component
Early sparse-ER exploration is approximated by a Poisson branching process. Let $u$ be the extinction probability and $S=1-u$ the limiting giant fraction.

> [!theorem] Sparse-ER threshold
> For fixed $c$ in the large-$N$ limit,
> $$u=e^{c(u-1)},\qquad S=1-e^{-cS}.$$
> Choose the smallest solution for $u$, equivalently the largest for $S$. For $c\le1$, $S=0$; for $c>1$, a positive solution exists. This is a limit theorem for this ensemble, not an exact equation for each finite graph.

> [!proof] Branching derivation
> If a reached vertex has Poisson$(c)$ onward branches, extinction requires all of them to fail. Averaging $u^k$ gives $u=\sum_ke^{-c}c^ku^k/k!=e^{c(u-1)}$. For $f(S)=1-e^{-cS}-S$, $f(0)=0$, $f'(0)=c-1$ and $f''(S)<0$. Strict concavity gives no positive root for $c\le1$ and a unique one for $c>1$. Relating this branching approximation to finite-graph component sizes requires the sparse random-graph limit.

Near $c=1+\epsilon$, expansion gives $S\sim2\epsilon$ as $\epsilon\downarrow0$. At $c=2$, $S\approx0.7968$; at $c=3$, $S\approx0.9405$.

> [!warning] Giant does not mean connected
> A giant occupies a positive fraction; other components remain. Whole-graph connectivity instead appears around $q\sim\log N/N$. For fixed $c>1$ away from criticality, typical distances within the giant are logarithmic in $N$, with branching heuristic $\log N/\log c$. Do not apply it to unreachable pairs or the critical regime.

## Simulation lesson
Repeat model draws and inspect their distribution. At fixed density the model becomes dense; keeping $q=c/(N-1)$ instead holds expected degree fixed. Sparse ER has low clustering and does not generally reproduce empirical degree heterogeneity or triangle closure.

> [!code] Estimate finite-graph giant fractions
> ```python
> import networkx as nx
> import numpy as np
>
> N, c, runs = 500, 2.0, 40
> fractions = []
> for seed in range(runs):
>     G = nx.fast_gnp_random_graph(N, c/(N-1), seed=seed)
>     fractions.append(max(map(len, nx.connected_components(G))) / N)
> print(np.mean(fractions), np.std(fractions, ddof=1))
>
> S = 1.0  # starting at zero would remain at the trivial fixed point
> for _ in range(500):
>     S = -np.expm1(-c * S)
> print(S)
> ```

For degree-based generalisations, the relevant branching factor is excess degree; see [[Configuration model]].

> [!reference]- Sources
> Lecture Week 3; Jenny’s notes Week 3. Newman §§11.1–11.7. Tutorial 3, dense/sparse scaling, null comparisons and giant-component experiment.
