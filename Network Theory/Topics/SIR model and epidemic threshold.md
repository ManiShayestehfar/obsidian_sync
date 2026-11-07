---
tags: [data5441, ch12, dynamics]
aliases: [SIR, Epidemic threshold, Mean-field epidemics, Degree-based mean field]
---
# SIR model and the epidemic threshold

> [!abstract] Summary
> Continuous-time SIR in mean field.
> - **Order 0** (homogeneous): an outbreak occurs iff $\lambda/\mu>1/\langle z\rangle$.
> - **Order 1** (degree classes): the threshold becomes $\lambda/\mu>\langle z\rangle/\langle z^2\rangle$, the same as the percolation threshold.
>
> For scale-free networks with $2<\gamma<3$, $\langle z^2\rangle\to\infty$, so there is no threshold.
> Chapter: [[Ch12 Epidemics and games on networks]] · Lecture pp. 151–159

> [!definition] SIS and SIR (continuous time)
> - **SIS:** S + I $\xrightarrow{\lambda}$ I + I, then I $\xrightarrow{\mu}$ S.
> - **SIR:** S + I $\xrightarrow{\lambda}$ I + I, then I $\xrightarrow{\mu}$ R (recovered, permanently immune).
>
> $\lambda$ is the infection rate per S–I contact and $\mu$ the recovery rate, both per unit time.
> Fractions: $s=\#S/N$, $\rho=\#I/N$, $r=\#R/N$, with $s+\rho+r=1$ for all $t$.
> Goal: equations valid as $N\to\infty$ with $\langle z\rangle$ fixed, on random graphs.

## Order 0: homogeneous mean field

> [!definition] Order-0 equations
> Assume each node has $\langle z\rangle$ contacts met at random. Then a susceptible node has on average $\langle z\rangle\rho$ infected contacts, and
> $$\frac{ds}{dt}=-\lambda\langle z\rangle\rho s,\qquad\frac{d\rho}{dt}=\lambda\langle z\rangle\rho s-\mu\rho,\qquad\frac{dr}{dt}=\mu\rho,$$
> with initial conditions $\rho(0)=1-s_0\ll1$, $s(0)=s_0\approx1$, $r(0)=0$.

> [!theorem] Final outbreak size (order 0)
> As $t\to\infty$, $\rho\to0$, and $r_\infty$ solves
> $$r_\infty=1-e^{-\frac{\lambda\langle z\rangle}{\mu}r_\infty}.$$
> A non-trivial solution $r_\infty>0$ (an outbreak) exists iff
> $$\frac{\lambda\langle z\rangle}{\mu}>1\quad\Longleftrightarrow\quad\frac{\lambda}{\mu}>\frac{1}{\langle z\rangle}\qquad(\text{epidemic threshold}).$$

> [!proof]-
> Divide the $s$ and $r$ equations:
> $$\frac{ds}{dr}=-\frac{\lambda\langle z\rangle}{\mu}s,$$
> which is separable and linear. So $s(r)=s_0e^{-\lambda\langle z\rangle r/\mu}\approx e^{-\lambda\langle z\rangle r/\mu}$.
> As $t\to\infty$, $\rho_\infty=0$, so $r_\infty=1-s_\infty=1-e^{-\lambda\langle z\rangle r_\infty/\mu}$.
> The right-hand side $h(r)=1-e^{-ar}$, with $a=\lambda\langle z\rangle/\mu$, is increasing and concave, with $h(0)=0$ and $h(r)<1$. The line $r$ meets $h$ at some $r>0$ iff $h'(0)=a>1$. $\square$
> Note: $\lambda/\mu$ is a property of the disease, while $\langle z\rangle$ is a property of the network.

> [!remark] Shape of the outbreak
> - $s(t)$ decreases from $\approx1$ to $s_\infty$.
> - $\rho(t)$ rises and falls (the epidemic peak).
> - $r(t)$ increases to $r_\infty$, the measured size of the outbreak.
>
> Plotting $r_\infty$ against $\lambda/\mu$ gives $0$ below $1/\langle z\rangle$ and a positive, increasing value above it.

## Order 1: degree-based mean field

> [!definition] Order-1 equations
> Take a random graph with degree distribution $P(z)$ and treat each degree class separately, with $s_z,\rho_z,r_z$ the fractions within class $z$. A link points to an infected node with probability
> $$\Theta(t)=\frac{\sum_zzP(z)\rho_z(t)}{\langle z\rangle}\qquad(0).$$
> Then
> $$\frac{ds_z}{dt}=-\lambda zs_z\Theta\ \ (1),\qquad\frac{d\rho_z}{dt}=\lambda zs_z\Theta-\mu\rho_z\ \ (2),\qquad\frac{dr_z}{dt}=\mu\rho_z\ \ (3),$$
> with $r_z(0)=0$, $\rho_z(0)=1-s_0\ll1$ and $s_z(0)=s_0\approx1$.

> [!theorem] Epidemic threshold with degree heterogeneity
> An outbreak occurs iff
> $$\frac{\lambda}{\mu}>\frac{\langle z\rangle}{\langle z^2\rangle}=\frac{1}{\langle z^2\rangle/\langle z\rangle}.$$
> For Poisson degrees, $\langle z^2\rangle=\langle z\rangle^2+\langle z\rangle$, which gives a threshold slightly below $1/\langle z\rangle$. Order 0 is recovered when degrees are homogeneous.

> [!proof]-
> **Step 1.** Integrating (1) gives $s_z(t)=e^{-\lambda z\phi(t)}$, where $\phi(t)=\int_0^t\Theta(t')dt'$ and $s_0\approx1$.
> **Step 2.** By (0) and (3),
> $$\phi(t)=\frac{1}{\langle z\rangle}\sum_zzP(z)\int_0^t\rho_zdt'=\frac{1}{\langle z\rangle}\sum_zzP(z)\frac{r_z}{\mu}.$$
> **Step 3.** Differentiate and use $\rho_z=1-s_z-r_z$:
> $$\frac{d\phi}{dt}=\frac{1}{\langle z\rangle}\sum_zzP(z)\rho_z=1-\frac{1}{\langle z\rangle}\sum_zzP(z)s_z-\mu\phi .$$
> **Step 4.** As $t\to\infty$, $\rho_z\to0$, so $d\phi/dt=\Theta\to0$. Substituting Step 1 gives the implicit equation
> $$\phi_\infty=\frac1\mu-\frac{1}{\mu\langle z\rangle}\sum_zzP(z)e^{-\lambda z\phi_\infty}=:h(\phi_\infty).$$
> **Step 5.** $\phi_\infty=0$ always solves it, and $h$ is increasing and concave. A non-trivial solution exists iff $h'(0)>1$:
> $$h'(0)=\frac{\lambda}{\mu\langle z\rangle}\sum_zz^2P(z)=\frac{\lambda}{\mu}\frac{\langle z^2\rangle}{\langle z\rangle}>1 .\qquad\square$$

## Connection to percolation

> [!theorem] SIR as bond percolation
> An infected node stays infectious for a time $T\sim1/\mu$. The probability that it transmits to a given neighbour is
> $$p=1-(1-\lambda\,dt)^{T/dt}\approx1-e^{-\lambda T}\approx\frac{\lambda}{\mu}\quad(\text{small }\lambda/\mu).$$
> So the final outbreak is the cluster of bond percolation with occupation probability $p$. Using the percolation threshold ([[Percolation and robustness]]),
> $$p_c=\frac{1}{\langle z^2\rangle/\langle z\rangle-1}\approx\frac{\langle z\rangle}{\langle z^2\rangle}\quad(\text{when }\langle z^2\rangle/\langle z\rangle\gg1),$$
> and $p\approx\lambda/\mu>p_c$ recovers $\lambda/\mu>\langle z\rangle/\langle z^2\rangle$.

> [!theorem] No epidemic threshold in scale-free networks
> If $P(z)\sim z^{-\gamma}$ with $2<\gamma<3$, then $\langle z^2\rangle\to\infty$ as $N\to\infty$. So $\langle z\rangle/\langle z^2\rangle\to0$, and **any** $\lambda/\mu>0$ leads to an outbreak.

> [!exam] What to be able to do
> - Write the order-0 and order-1 ODEs and explain each term.
> - Derive $r_\infty=1-e^{-\lambda\langle z\rangle r_\infty/\mu}$ and the threshold from the slope condition.
> - Explain the percolation mapping and the consequence for scale-free networks.

> [!selftest]- Self-test
> 1. Why does $\langle z^2\rangle$ (not just $\langle z\rangle$) enter at order 1? — Infection travels along links and reaches high-degree nodes preferentially.
> 2. What is the threshold for ER with $\langle z\rangle=4$ at order 1? — $\langle z^2\rangle=20$, so $\lambda/\mu>1/5$.
> 3. Why do all viruses spread on scale-free networks? — $\langle z^2\rangle\to\infty$.

---
Related: [[SI and SIS models]] · [[Binary-state dynamics]] · [[Percolation and robustness]] · [[Power laws]]
