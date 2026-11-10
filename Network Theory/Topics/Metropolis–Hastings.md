---
tags: [data5441, ch06, methods]
aliases: [Metropolis-Hastings, Metropolis algorithm, Acceptance probability, Importance sampling]
---
---
# Metropolis–Hastings

> [!abstract] Core idea
> **Metropolis–Hastings (MH)** constructs a Markov chain that spends the correct proportion of time in each state, even when the target probability $p(g)$ is known **only up to a normalising constant**. At each step we **propose**, then **accept or reject**; both outcomes count as a step.
>
> **Key formula:**
> $$\boxed{A(g\to g')=\min\left\{1,\frac{p(g')\,\Pi(g'\to g)}{p(g)\,\Pi(g\to g')}\right\}.}$$
> For a **symmetric** proposal, $A=\min\{1,p(g')/p(g)\}$.
>
> Course: **DATA5441 Week 6**, lecture PDF pp. **74–78**, and Tutorial 6, §§1–2. Prerequisite: [[Markov chain Monte Carlo on graphs]]. See also [[Maximum entropy and ERGMs]].

## 1. Why do we need MH?

In Week 4 we sampled *uniformly* from particular graph spaces (fixed $N$, fixed $N,L$, or a fixed degree sequence). But if we want graphs with **more triangles or higher clustering**, uniform sampling may almost never visit the desired configurations. We instead want to choose the probability $p(g)$ of each graph in a suitable space $\Omega$.

MH solves the **sampling problem**: given a target distribution $p$, how can we generate representative states **without independently drawing a fresh state from $p$**? Choosing a principled target $p$ is a separate problem, addressed by [[Maximum entropy and ERGMs]].

> [!definition] Target, proposal, acceptance and transition
> Let $g_t\in\Omega$ be the current graph. Distinguish:
> - $p(g)$: **target** probability of graph $g$ (the distribution we want to sample);
> - $\Pi(g\to g')$: **proposal** probability of suggesting $g'$ given $g$;
> - $A(g\to g')$: **acceptance** probability after that suggestion;
> - $W(g\to g')$: probability the chain actually moves from $g$ to $g'$ in one step.
>
> For $g'\ne g$,
> $$W(g\to g')=\Pi(g\to g')A(g\to g').$$
> Rejections and self-proposals give the remaining probability $W(g\to g)=1-\sum_{h\ne g}W(g\to h)$.

## 2. The MH algorithm

![[Assets/mh-accept-reject.png|800]]

> [!definition] One MH iteration
> Given the current state $g_t$:
> 1. **Propose** $g'\sim\Pi(g_t\to\cdot)$, staying within the permitted graph space $\Omega$.
> 2. **Compute** $A(g_t\to g')$ using the boxed MH formula above.
> 3. Draw $u\sim U[0,1]$. If $u<A$, **accept** and set $g_{t+1}=g'$; otherwise **reject** and set $g_{t+1}=g_t$.
> 4. **Repeat**, recording the resulting state after every step, including rejections.
>
> The simplified **Metropolis** rule applies only when $\Pi(g\to g')=\Pi(g'\to g)$ for the relevant moves:
> $$\boxed{A(g\to g')=\min\left\{1,\frac{p(g')}{p(g)}\right\}.}$$

**Interpretation:** a move to a *more probable* state is always accepted (for a symmetric proposal), but a move to a *less probable* state may still be accepted. Those occasional downhill moves are essential for exploring the graph space rather than merely maximising $p(g)$.

## 3. Why does MH work? Detailed balance and its consequences

Recall that a distribution $p$ satisfies **detailed balance** with $W$ if

$$p(g)W(g\to g')=p(g')W(g'\to g)\qquad(g,g'\in\Omega).$$

This means that, at equilibrium, the probability flow from $g$ to $g'$ equals the reverse flow.

> [!proof]- Derive the MH acceptance probability (important)
> For $g\ne g'$, substitute $W=\Pi A$ into detailed balance:
> $$p(g)\Pi(g\to g')A(g\to g')=p(g')\Pi(g'\to g)A(g'\to g).$$
> Rearranging gives
> $$\frac{A(g\to g')}{A(g'\to g)}=\frac{p(g')\Pi(g'\to g)}{p(g)\Pi(g\to g')}=:R.$$
> Since an acceptance probability cannot exceed $1$, choose $A(g\to g')=\min\{1,R\}$ and $A(g'\to g)=\min\{1,R^{-1}\}$.
>
> **Verification:**
> $$\begin{aligned}
> p(g)W(g\to g')
> &=\min\{p(g)\Pi(g\to g'),\ p(g')\Pi(g'\to g)\}\\
> &=p(g')W(g'\to g).
> \end{aligned}$$
> Thus the MH transition satisfies detailed balance, including the trivial diagonal case. $\square$

> [!theorem] Stationarity and convergence
> **Detailed balance implies stationarity:** summing $p(g)W(g\to g')=p(g')W(g'\to g)$ over $g$ shows that the distribution remains $p$ after a transition.
>
> For a **finite** state space, if the chain is also **irreducible** (every positive-probability state is reachable) and **aperiodic** (no forced periodic cycle), then $p$ is the **unique limiting distribution**, regardless of the initial state.
>
> In particular, after sufficient equilibration, averages along a long trajectory estimate ensemble averages:
> $$\boxed{\langle x\rangle_p=\sum_{g\in\Omega}p(g)x(g)\ \approx\ \frac1S\sum_{s=1}^S x(g_{t_s}).}$$
> The right-hand samples are generally **correlated**, not independent.

### Consequences to understand

| Fact | Meaning for using MH |
|---|---|
| **Normalisation cancels** | If $p(g)=w(g)/Z$, then $p(g')/p(g)=w(g')/w(g)$; we never have to compute $Z$. |
| **Rejections count** | If a move is rejected, $g_{t+1}=g_t$ must still appear in the trajectory; ignoring repeats distorts the sampled law. |
| **Initial state matters at first** | Discard an initial **burn-in** period before estimating equilibrium quantities. |
| **Successive samples are dependent** | A slowly mixing chain can give many stored values but little *effective* information. Check traces, use longer runs and compare independent runs. |
| **Proposal choice matters** | A valid proposal must explore the desired support; a very local proposal can mix badly, even with a high acceptance rate. |
| **Symmetry must be checked** | If $\Pi(g\to g')\ne\Pi(g'\to g)$, retain the proposal ratio in the **Hastings** formula. |

> [!warning] Stationary is not the same as well mixed
> Detailed balance alone does **not** guarantee that a run has reached equilibrium. If proposals are trapped in a small region, sample averages can be badly biased. If a target assigns zero weight to some graphs (for example $w(g)=C(g)^{10}$ when $C(g)=0$), apply the ratio formula on the **positive-probability support** and start in a state of positive weight.

## 4. Tutorial 6: sampling a simple probability density

The lecture's one-dimensional example makes the mechanism easy to see. Take
$$p(x)=2x,\qquad 0\le x\le1,\qquad \mathbb E[X]=\int_0^1 2x^2\,dx=\boxed{\tfrac23}.$$
Propose $x'=(x+\varepsilon)\bmod1$ with $\varepsilon\sim U[-\delta,\delta]$. This is symmetric, so for $x>0$,
$$\boxed{A(x\to x')=\min\{1,x'/x\}.}$$
**Example:** from $x=0.8$, proposing $x'=0.4$ has acceptance probability $0.4/0.8=0.5$. Proposing $x'=0.9$ is always accepted.

![[Assets/mh-mixing-example.png|850]]

*The diagrams are illustrative simulations with the same target $p(x)=2x$. A tiny proposal width gives very high acceptance but explores only a small region over hundreds of steps; a wider proposal explores the interval more effectively.*


> [!example] Tutorial 6, Exercises 1.1–1.3
> - **Small $\delta$:** consecutive states are similar, so a short run can be concentrated near its initial value.
> - **Global symmetric proposal** $x'\sim U[0,1]$: often traverses the state space more efficiently for this particular target.
> - **Weight $w(x)=3x$:** the constant cancels; after normalisation this is still $p(x)=2x$, with $\mathbb E[X]=2/3$.
> - **Weight $w(x)=x^2$:** after normalisation $p(x)=3x^2$, giving $\mathbb E[X]=\int_0^1 3x^3\,dx=3/4$.
>
> **Exam lesson:** an unnormalised *weight* need not itself integrate to $1$. MH uses ratios of weights, not their unknown normalising constants.

## 5. Graph proposals: which constraints are preserved?

![[Assets/graph-proposals.png|800]]

The proposal decides **which graph space the algorithm explores**, while the acceptance rule decides **how it weights those graphs**.

| Graph space | Example proposal | Always preserved |
|---|---|---|
| $\Omega_N$: all simple graphs on $N$ labelled nodes | Toggle one uniformly chosen unordered node pair | $N$ |
| $\Omega_{N,L}$: fixed number of links | Remove an edge, add a non-edge | $N,L$ |
| $\Omega(\mathbf z)$: fixed degree sequence | Double-edge swap $(a,b),(c,d)\mapsto(a,c),(b,d)$ | $N,L,$ every $z_i$ |

> [!remark] Symmetric edge replacement (Trial Exam 1, Q7)
> Let $Y=\binom N2$. Remove one of the $L$ edges uniformly; then add one of the $Y-L+1$ non-edges **of the intermediate graph**, including the edge just removed. Every specified reversible replacement has proposal probability
> $$\Pi(g\to g')=\frac1{L(Y-L+1)}=\Pi(g'\to g).$$
> Re-adding the removed edge gives a self-proposal. For double-edge swaps, similarly draw a single candidate in a symmetric way and treat an invalid swap as a self-proposal; *repeatedly searching until success* can change the proposal probabilities.

## 6. Exam: derive acceptance probabilities quickly

For a **symmetric** proposal, first write the unnormalised weight $w(g)$ and compute $w(g')/w(g)$.

> [!exam] Trial Exam 2, Q2(f): edge toggles on $\Omega_N$
> 1. **Uniform** $w_1(g)=1$: $\boxed{A_1=1}$.
> 2. **Link-squared** $w_2(g)=L(g)^2$: $\boxed{A_2=\min\{1,[L(g')/L(g)]^2\}}$ when $L(g)>0$ (the empty graph has zero target weight).
> 3. **Exponential link bias** $w_3(g)=e^{\beta L(g)}$:
>    $$\boxed{A_3=\min\{1,e^{\beta[L(g')-L(g)]}\}.}$$
>
> For a **triangle-biased** fixed-$L$ ensemble, $w_\beta(g)=e^{\beta T(g)}$:
> $$\boxed{A=\min\{1,e^{\beta\Delta T}\},\qquad\Delta T=T(g')-T(g).}$$
> If $\beta=1.5$ and a proposed move destroys two triangles, $A=e^{-3}\approx0.050$; if it creates two triangles, $A=1$.

> [!code]- Minimal Metropolis step (symmetric graph proposal)
> ```python
> import numpy as np
>
> def metropolis_step(g, propose, statistic, beta, rng):
>     h = propose(g, rng)  # Must be a genuinely symmetric proposal.
>     delta = beta * (statistic(h) - statistic(g))
>     if np.log(rng.random()) < min(0.0, delta):
>         return h
>     return g  # A rejection still advances Markov time.
> ```
> This implements $p_\beta(g)\propto e^{\beta x(g)}$. It does **not** include the Hastings correction for a non-symmetric proposal.

> [!question]- Self-test
> 4. **Why does the normalising constant $Z$ disappear?** It cancels in $p(g')/p(g)$.
> 5. **What if a proposal is rejected?** Keep $g_{t+1}=g_t$ and count the step.
> 6. **Why doesn't high acceptance imply good sampling?** Proposals can be too small to explore the state space efficiently.
> 7. **Which graph move preserves degrees?** A valid double-edge swap.
> 8. **Does detailed balance alone imply convergence from any start?** No; irreducibility and aperiodicity are also needed for the standard finite-state convergence conclusion.
> 9. **How does the acceptance formula change for non-symmetric proposals?** Multiply the target ratio by $\Pi(g'\to g)/\Pi(g\to g')$.

---
Related: [[Markov chain Monte Carlo on graphs]] · [[Maximum entropy and ERGMs]] · [[Stochastic block models]] · [[Reconstruction from node activity]]
