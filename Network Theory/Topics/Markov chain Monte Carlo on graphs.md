---
tags: [data5441, ch04, methods]
aliases: [MCMC, Graph sampling, Edge swap, Detailed balance, Burn-in]
---
# Markov chain Monte Carlo on graphs

> [!abstract] Summary
> When we cannot draw a constrained random graph directly, we run a Markov chain whose moves preserve the constraints (fixed $L$, fixed degrees, …). If the chain is irreducible and aperiodic and satisfies detailed balance for the target, long runs sample the target. Burn-in and correlations must be handled before averaging.
> Chapter: [[Ch04 Sampling random graphs]]

> [!definition] Markov chain, stationary distribution
> On a finite state space $\Omega$, a transition matrix $W(g\to h)\ge0$ satisfies $\sum_hW(g\to h)=1$. A probability $\pi$ is **stationary** if $\pi(h)=\sum_g\pi(g)W(g\to h)$ for all $h$.

> [!definition] Detailed balance
> $$\pi(g)\,W(g\to h)=\pi(h)\,W(h\to g)\qquad\forall g,h .$$

> [!theorem] Detailed balance ⇒ stationarity
> If $W$ satisfies detailed balance for $\pi$, then $\pi$ is stationary.

> [!proof]-
> $\sum_g\pi(g)W(g\to h)=\sum_g\pi(h)W(h\to g)=\pi(h)\sum_gW(h\to g)=\pi(h)$. $\square$

> [!theorem] Convergence (ergodic theorem, finite chains)
> If a finite chain is **irreducible** (every state can reach every other) and **aperiodic**, then it has a unique stationary $\pi$, and $\Pr(g_t=h)\to\pi(h)$ from every start. Time averages $\frac1T\sum_tf(g_t)\to\mathbb E_\pi f$.
> Detailed balance alone does not give irreducibility or aperiodicity.

## Moves on graph spaces

> [!algorithm] Moves and what they preserve
> | Move | Preserves | Target if always accepted |
> |---|---|---|
> | **Edge flip / toggle:** pick a pair $\{i,j\}$, toggle $A_{ij}$ | $N$ | uniform on $\Omega_N$ |
> | **Edge replacement:** remove a uniform existing link, add a uniform absent one | $N,L$ | uniform on $\Omega_{N,L}$ |
> | **Double-edge swap:** $\{a,b\},\{c,d\}\to\{a,d\},\{c,b\}$ (reject if it creates a loop or multi-link) | every $z_i$ | uniform on $\Omega_{\mathbf z}$ |
>
> These proposals are **symmetric**, $\Pi(g\to h)=\Pi(h\to g)$, so for a uniform target the acceptance probability is $1$ (rejected invalid swaps leave $g$ unchanged).

> [!proposition] Symmetry of edge replacement (Trial Exam 1, Q7c)
> Remove one of the $L$ present links uniformly, then add one of the $Y-L+1$ absent pairs of the intermediate graph uniformly. A specific move $g\to h$ has probability $\dfrac{1}{L(Y-L+1)}$, and the reverse move has the same probability, so the proposal is symmetric. Re-adding the removed link gives a valid self-transition, which also makes the chain aperiodic.

> [!remark] Count rejected steps
> A rejected or invalid proposal means the chain **stays** at $g$, and $g$ must be counted again. Retrying until a move succeeds, or recording only departures, changes the sampled distribution.
> Pure edge flipping alternates the parity of $L$ (period $2$); a holding probability removes this.

## Burn-in, correlations, uncertainty

> [!definition] Burn-in and correlation time
> **Burn-in** is the initial stretch discarded while the chain forgets its start ($g_0=g^*$, the observed network). Successive states are correlated. The integrated autocorrelation time $\tau=1+2\sum_{t\ge1}\rho(t)$ gives an effective sample size $R_{eff}\approx R/\tau$, and the standard error of a mean is $\approx s/\sqrt{R_{eff}}$.

> [!remark] Two different uncertainties
> - **Ensemble spread** (standard deviation $s$ across sampled graphs): compare the observed network with this.
> - **Standard error of the mean** $s/\sqrt{R_{eff}}$: the uncertainty in the estimated ensemble average.

> [!exam] Reading an MCMC trace (Trial Exam 1, Q3)
> The trace shows $C(g_t)$ under degree-preserving swaps, started at the observed $g^*$.
> - $C(g^*)$ is the value at $t=0$.
> - The long-time plateau is the null-model clustering.
> - As $t\to\infty$, a finite irreducible chain visits **every** state of $\Omega_{\mathbf z}$ with probability $1$. So any value attained by some graph in the space is eventually observed: e.g. $C(g_t)=C(g^*)$ occurs with probability $1$, while $C<0$ has probability $0$.


> [!code]- Degree-preserving null ensemble (tutorial 4)
> ```python
> H = G.copy()
> Cs = []
> for t in range(T):
>     nx.double_edge_swap(H, nswap=1, max_tries=100)   # keeps every degree
>     Cs.append(nx.transitivity(H))
> ```

> [!selftest]- Self-test
> 1. Which move preserves the degree sequence? — The double-edge swap.
> 2. Why must rejected moves be recorded? — Otherwise the sampled law is biased towards "easy-to-leave" states.
> 3. Does a flat trace prove mixing? — No; the chain may be trapped.

---
Related: [[Configuration model]] · [[Metropolis–Hastings]] · [[Random graph ensembles]]
