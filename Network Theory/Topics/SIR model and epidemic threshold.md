---
tags: [data5441, ch12, dynamics]
aliases: [SIR, Epidemic threshold, Mean-field epidemics, Degree-based mean field]
---
# SIR model and the epidemic threshold

> [!abstract] Summary
> Week 12 studies **continuous-time** epidemic dynamics on large random networks. **Order 0** replaces all degrees by $\langle z\rangle$; **order 1** treats every degree class separately. These lead to different approximate outbreak thresholds:
> $$\boxed{\text{Order 0: }\frac\lambda\mu>\frac1{\langle z\rangle};\qquad\text{Order 1: }\frac\lambda\mu>\frac{\langle z\rangle}{\langle z^2\rangle}.}$$
> Chapter: [[Ch12 Epidemics and games on networks]] · **2026 lecture pp. 151–159** · Jeny pp. 53–56.

## 1. Epidemic states, rates and the quantity of interest

> [!definition] Continuous-time SIS and SIR
> - **SIS:** a susceptible node becomes infected through an infected neighbour, $S+I\xrightarrow{\lambda}I+I$, and an infected node recovers to susceptibility, $I\xrightarrow{\mu}S$.
> - **SIR:** the infection event is the same, but recovery produces a permanently removed/recovered state, $I\xrightarrow{\mu}R$.
>
> Here $\lambda$ is the **infection rate per S–I contact** and $\mu$ the **recovery rate per infected node**, measured per unit time. They are **not** the probabilities per selected update in [[SI and SIS models]].

> [!definition] Population fractions
> $$s(t)=\frac{\#S}{N},\qquad \rho(t)=\frac{\#I}{N},\qquad r(t)=\frac{\#R}{N},\qquad s+\rho+r=1.$$
> For SIR, $r_\infty$ is the **fraction ever infected and recovered by the end**; the infectious fraction satisfies $\rho(t)\to0$ as the outbreak ends. We consider sparse random graphs with $N\to\infty$ and $\langle z\rangle$ finite.

## 2. Order 0 — homogeneous mean-field approximation

> [!definition] Approximation and ODEs (lecture equations 1–3)
> Assume every node has approximately $\langle z\rangle$ contacts and contacts are effectively random. The typical number of infected neighbours is $\langle z\rangle\rho$. Thus
> $$\boxed{\begin{aligned}\frac{ds}{dt}&=-\lambda\langle z\rangle s\rho,\\\frac{d\rho}{dt}&=\lambda\langle z\rangle s\rho-\mu\rho,\\\frac{dr}{dt}&=\mu\rho.\end{aligned}}$$
> **Interpretation:** new infections reduce S and increase I at the same rate; recoveries decrease I and increase R. The three right-hand sides sum to zero.
>
> Initial conditions in the lecture: $s(0)=s_0\approx1$, $\rho(0)=1-s_0\ll1$, $r(0)=0$.

> [!proposition] Implicit final-size equation
> $$\boxed{r_\infty=1-\exp\!\left(-\frac{\lambda\langle z\rangle}{\mu}r_\infty\right)}\qquad (s_0\approx1).$$

> [!proof]- Derivation (lecture pp. 153–154)
> Divide the susceptible equation by the recovered equation (while $\rho>0$):
> $$\frac{ds}{dr}=\frac{-\lambda\langle z\rangle s\rho}{\mu\rho}=-\frac{\lambda\langle z\rangle}{\mu}s.$$
> Integrating gives $s(r)=s_0e^{-\lambda\langle z\rangle r/\mu}$. At the end, $\rho_\infty=0$ and $r_\infty=1-s_\infty$. Substituting $s_0\approx1$ yields the stated equation. For general $s_0$, retain $r_\infty=1-s_0e^{-\lambda\langle z\rangle r_\infty/\mu}$.

> [!theorem] Order-0 epidemic threshold (lecture)
> Set $a=\lambda\langle z\rangle/\mu$ and $h(r)=1-e^{-ar}$. The fixed-point equation is $r=h(r)$; $r=0$ always solves it. A **non-zero** solution appears when the slope of the right-hand side at zero exceeds the slope of $r$:
> $$h'(0)=a>1\quad\Longleftrightarrow\quad\boxed{\frac{\lambda}{\mu}>\frac1{\langle z\rangle}}.$$
> This is the **order-0 mean-field threshold**, not an exact threshold for every finite graph. $\lambda/\mu$ describes the disease; $\langle z\rangle$ describes the network.

![[Assets/w12-sir-threshold.png|660]]

> [!exam] Reading an SIR curve
> - $s(t)$ **decreases** (fewer susceptibles).
> - $\rho(t)$ usually **rises, peaks, then falls** to 0.
> - $r(t)$ **increases** to the final outbreak size $r_\infty$.
> - Plotting $r_\infty$ against $\lambda/\mu$ shows a transition at the appropriate mean-field threshold.

## 3. Order 1 — degree-class mean-field approximation

> [!definition] Why degree heterogeneity matters
> In a random graph with degree distribution $P(z)$, different degrees have different numbers of opportunities to encounter infection. Define $s_z(t),\rho_z(t),r_z(t)$ as the S, I, R fractions **within degree class $z$**. The overall quantities are
> $$\{s,\rho,r\}=\sum_z P(z)\{s_z,\rho_z,r_z\}.$$

> [!definition] Probability of reaching an infected node (lecture equation 0)
> A random **edge endpoint** has a size-biased degree distribution, proportional to $zP(z)$. Hence the probability that it is infected is
> $$\boxed{\Theta(t)=\frac{\sum_z zP(z)\rho_z(t)}{\langle z\rangle}}.$$
> A degree-$z$ susceptible node has an expected $z\Theta(t)$ infected neighbours.

> [!definition] Order-1 equations (lecture equations 1–3)
> $$\boxed{\begin{aligned}\frac{ds_z}{dt}&=-\lambda z s_z\Theta(t),\\\frac{d\rho_z}{dt}&=\lambda z s_z\Theta(t)-\mu\rho_z,\\\frac{dr_z}{dt}&=\mu\rho_z.\end{aligned}}$$
> The lecture takes $s_z(0)\approx1$, $\rho_z(0)\ll1$ and $r_z(0)=0$. The assumptions are still **mean field**: states of neighbouring nodes are approximated by degree-class averages rather than correlated configurations.

> [!theorem] Order-1 epidemic threshold (lecture pp. 157–158)
> $$\boxed{\frac{\lambda}{\mu}>\frac{\langle z\rangle}{\langle z^2\rangle}.}$$
> This includes degree variability through the **second moment** $\langle z^2\rangle$, rather than only through $\langle z\rangle$.

> [!proof]- Concise derivation using the lecturer's $\Phi(t)$
> Define $\Phi(t)=\int_0^t\Theta(u)\,du$, so $\dot\Phi=\Theta$. From the first equation (with $s_z(0)\approx1$),
> $$s_z(t)=e^{-\lambda z\Phi(t)}.\tag{4}$$
> From $\dot r_z=\mu\rho_z$ and $r_z(0)=0$,
> $$\Phi(t)=\frac1{\mu\langle z\rangle}\sum_z zP(z)r_z(t).\tag{5}$$
> At long times, $\rho_z\to0$ and $r_z=1-s_z$. Combining (4)–(5) gives
> $$\Phi_\infty=\frac1{\mu\langle z\rangle}\sum_z zP(z)\bigl(1-e^{-\lambda z\Phi_\infty}\bigr)=:h(\Phi_\infty).$$
> The trivial solution is $\Phi_\infty=0$. A non-zero solution appears if
> $$h'(0)=\frac\lambda{\mu\langle z\rangle}\sum_z z^2P(z)=\frac\lambda\mu\frac{\langle z^2\rangle}{\langle z\rangle}>1,$$
> giving the threshold.

> [!example] Comparing orders 0 and 1
> For Poisson degrees of mean $c$, $\langle z^2\rangle=c^2+c$. At $c=4$:
> - **Order 0:** $\lambda/\mu>1/4$.
> - **Order 1:** $\lambda/\mu>4/20=1/5$.
>
> Their difference reflects the **degree variability** accounted for by order 1. For a regular graph of degree $z_0$, both formulas reduce to $\lambda/\mu>1/z_0$.

## 4. Connection to the Week 10 percolation calculation

> [!remark] Lecture's approximate correspondence (p. 159)
> An infected node remains infectious for a typical time $T\sim1/\mu$. The lecture approximates the probability of passing infection along one edge by
> $$p\approx1-e^{-\lambda T}\approx\frac\lambda\mu\qquad(\lambda/\mu\ll1).$$
> From Week 10, the **bond occupation threshold** for a locally tree-like random graph is
> $$p_c=\frac1{\langle z^2\rangle/\langle z\rangle-1}\approx\frac{\langle z\rangle}{\langle z^2\rangle}\quad\text{when }\langle z^2\rangle\gg\langle z\rangle.$$
> Substituting the approximations $p\approx\lambda/\mu$ and $p_c\approx\langle z\rangle/\langle z^2\rangle$ **recovers the lecture's order-1 threshold**.
>
> **Scope:** This is the approximate comparison presented in the lecture. The two displayed critical expressions should **not** be equated as exact identities for finite degree moments.

> [!proposition] Consequence for scale-free networks (lecture)
> If $P(z)\propto z^{-\gamma}$ with $2<\gamma<3$, the second degree moment grows without bound as the network size increases, while the mean stays finite. Therefore
> $$\boxed{\frac{\langle z\rangle}{\langle z^2\rangle}\longrightarrow0.}$$
> **In the order-1 large-network approximation**, the epidemic threshold vanishes: even very small positive $\lambda/\mu$ can be above the threshold. This is a statement about the model and asymptotic limit, not a claim that every real-world infection invariably spreads.

## 5. Exam checklist

> [!exam] What to be able to reproduce
> 1. State the SIR transitions and define $s,\rho,r$.
> 2. Write and explain all three **order-0 equations**; divide $ds/dt$ by $dr/dt$ to obtain $r_\infty$.
> 3. Explain the slope test $h'(0)>1$ and threshold $1/\langle z\rangle$.
> 4. Define $\Theta(t)$, including why $zP(z)$ appears, and state the **order-1 equations**.
> 5. Follow the short $\Phi$ derivation to $\langle z\rangle/\langle z^2\rangle$.
> 6. Explain the **approximate** percolation connection and the consequence for scale-free networks.

> [!selftest]- Quick checks
> 1. What causes $\rho(t)$ to fall in SIR? — Recovery into the R class and depletion of susceptibles.
> 2. Why is $\Theta\ne\rho$ in general? — Random links preferentially reach high-degree nodes.
> 3. For Poisson mean 4, what are the two threshold estimates? — $1/4$ (order 0) and $1/5$ (order 1).
> 4. Why does the order-1 threshold vanish for $2<\gamma<3$? — $\langle z^2\rangle$ diverges as $N\to\infty$.

---
Related: [[SI and SIS models]] · [[Binary-state dynamics]] · [[Percolation and robustness]] · [[Power laws]]
