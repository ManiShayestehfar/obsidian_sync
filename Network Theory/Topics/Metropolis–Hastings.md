---
tags: [data5441, ch06, methods]
aliases: [Metropolis-Hastings, Metropolis algorithm, Acceptance probability, Importance sampling]
---
# Metropolis–Hastings

> [!abstract] Summary
> To sample from any target $p(g)$, known only up to normalisation, propose $g\to g'$ with $\Pi$ and accept with the MH probability. Detailed balance then holds for $p$. For symmetric proposals only the target ratio matters, and $Z$ cancels.
> Chapter: [[Ch06 ERGMs and Metropolis–Hastings]]

> [!definition] Metropolis–Hastings algorithm
> Given the current state $g$:
> 1. propose $g'$ with probability $\Pi(g\to g')$;
> 2. accept with probability
> $$A(g\to g')=\min\left\{1,\ \frac{p(g')\,\Pi(g'\to g)}{p(g)\,\Pi(g\to g')}\right\};$$
> 3. otherwise stay at $g$, and record $g$ again.
>
> For a **symmetric** proposal ($\Pi(g\to g')=\Pi(g'\to g)$) this is the **Metropolis** rule $A=\min\{1,p(g')/p(g)\}$.

> [!theorem] MH satisfies detailed balance
> For $g\ne g'$ with $p(g),p(g')>0$, the chain $W(g\to g')=\Pi(g\to g')A(g\to g')$ satisfies $p(g)W(g\to g')=p(g')W(g'\to g)$. So $p$ is stationary, and it is the limiting law if the chain is irreducible and aperiodic.

> [!proof]-
> $p(g)\Pi(g\to g')A(g\to g')=\min\{p(g)\Pi(g\to g'),\ p(g')\Pi(g'\to g)\}$. This expression is symmetric in $g$ and $g'$, so it equals $p(g')\Pi(g'\to g)A(g'\to g)$. Then apply [[Markov chain Monte Carlo on graphs#Detailed balance]]. $\square$

> [!remark] Why it is practical
> Only ratios $p(g')/p(g)$ appear, so the normalisation $Z=\sum_gp(g)$, which is intractable for graphs, cancels. Work with $\log p$ to avoid overflow.

> [!example] Tutorial 6: sampling $p(x)=2x$ on $[0,1]$
> Propose $x'=x+\varepsilon$ with $\varepsilon\sim U(-\delta,\delta)$, wrapped modulo $1$ (symmetric). Accept with $\min\{1,x'/x\}$.
> - Small $\delta$ gives high acceptance but slow exploration.
> - Large $\delta$ gives low acceptance.
> - High acceptance alone does **not** imply good mixing.
>
> Targets $\propto x$ and $\propto3x$ give the same normalised law $2x$ (mean $2/3$). A target $\propto x^2$ normalises to $3x^2$ (mean $3/4$).

> [!exam] Acceptance probabilities for graph targets
> **Symmetric single-pair toggle on $\Omega_N$ (Trial 2, Q2f):**
> - $p_1$ uniform: $A=1$.
> - $p_2\propto L^2$: $A=\min\{1,[L(g')/L(g)]^2\}$ for $L(g)>0$.
> - $p_3\propto e^{\beta L}$: $A=\min\{1,e^{\beta[L(g')-L(g)]}\}$.
>
> **Edge replacement on $\Omega_{N,L}$ with $p_\beta\propto e^{\beta T(g)}$ (Trial 1, Q7d):** $A=\min\{1,e^{\beta[T(g')-T(g)]}\}$.

> [!code]- Metropolis step in log-space (tutorial 6)
> ```python
> def metropolis_step(g, logp, propose, rng):
>     g2 = propose(g, rng)                 # symmetric proposal
>     if np.log(rng.random()) < logp(g2) - logp(g):
>         return g2
>     return g                             # rejected: stay (and record g again)
> ```

> [!selftest]- Self-test
> 1. Why does $Z$ not need to be computed? — It cancels in the ratio.
> 2. What is the acceptance for $p\propto e^{\beta x(g)}$ with a symmetric proposal? — $\min\{1,e^{\beta\Delta x}\}$.

---
Related: [[Markov chain Monte Carlo on graphs]] · [[Maximum entropy and ERGMs]] · [[Stochastic block models]] · [[Reconstruction from node activity]]
