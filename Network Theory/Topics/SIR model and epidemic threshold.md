---
tags: [data5441, ch12, dynamics]
aliases: [SIR, Epidemic threshold, Mean-field epidemics, Degree-based mean field]
---
# SIR model and the epidemic threshold

> [!abstract] Summary
> In **SIR**, susceptible nodes become infected through contacts and then recover permanently. The Week 12 lecture derives increasingly detailed **mean-field approximations**. The order-0 threshold depends on $\langle z\rangle$, while order 1 sees the excess influence of **high-degree nodes** through $\langle z^2\rangle$. SIR also connects to percolation, but the exact bond-percolation criterion and the lecture's degree-based mean-field threshold are **not identical formulas**.
> Chapter: [[Ch12 Epidemics and games on networks]] · **Week 12**, lecture pp. 151–159.

## 1. Continuous-time epidemic states

> [!definition] SIS versus SIR and notation
> An infected node transmits to each susceptible neighbour at rate $\lambda$ per S–I link and recovers at rate $\mu$ per infected node.
> - **SIS:** $S\to I\to S$, so a recovered node can be reinfected.
> - **SIR:** $S\to I\to R$, with $R$ permanently removed/immune.
> Write $s(t),i(t),r(t)$ for the three population fractions; $s+i+r=1$. Here **$i(t)$ is an infected fraction**, not a node index. The process starts with a small positive seed $i(0)$.

## 2. Order 0: homogeneous mean field

> [!definition] Order-0 equations
> Replace individual degrees by $c=\langle z\rangle$ and assume neighbours are randomly mixed. A susceptible node sees approximately $ci$ infected neighbours, so
> $$\boxed{\dot s=-\lambda csi,\quad \dot i=\lambda csi-\mu i,\quad \dot r=\mu i.}$$
> - $\lambda csi$: new infections (requires **S and I**).
> - $\mu i$: recoveries (leave I, enter R).
> - No flow **out of R** in SIR.

![[Assets/w12-sir-threshold.png|780]]

> [!theorem] Order-0 final size and epidemic threshold
> In the limit of a **vanishing but non-zero initial seed**, $i(t)\to0$ and the final ever-infected fraction $r_\infty$ satisfies
> $$\boxed{r_\infty=1-\exp\!\left(-\frac{\lambda c}{\mu}r_\infty\right).}$$
> A positive macroscopic outbreak branch exists precisely when
> $$\boxed{R_0^{(0)}=\frac{\lambda c}{\mu}>1\quad\Longleftrightarrow\quad\frac\lambda\mu>\frac1{\langle z\rangle}.}$$

> [!derivation]- Final-size equation in four steps
> 1. Divide $\dot s$ by $\dot r$: $ds/dr=-(\lambda c/\mu)s$.
> 2. Integrate: $s(t)=s_0e^{-(\lambda c/\mu)[r(t)-r_0]}$.
> 3. With $r_0=0$, $s_0\to1$ and $i_\infty=0$, use $s_\infty=1-r_\infty$.
> 4. Thus $r_\infty=1-e^{-ar_\infty}$, $a=\lambda c/\mu$. The right side has slope $a$ at $r=0$ and is strictly concave, so a **second**, positive intersection exists iff $a>1$.
>
> If the initial infected fraction is exactly zero, infection **never starts**, regardless of this threshold.

## 3. Order 1: distinguish the degrees

> [!definition] Degree-based mean-field approximation
> Keep the degree distribution $P(z)$, and let $s_z,i_z,r_z$ be S, I and R **fractions within degree class $z$**. Following a random edge is degree biased, so the probability its other endpoint is infected is approximated by
> $$\boxed{\Theta(t)=\frac{\sum_z zP(z)i_z(t)}{\langle z\rangle}.}$$
> The **degree-class equations** become
> $$\boxed{\dot s_z=-\lambda zs_z\Theta,\qquad\dot i_z=\lambda zs_z\Theta-\mu i_z,\qquad\dot r_z=\mu i_z.}$$
> **Assumptions:** large uncorrelated random graph, independent neighbour states and mean-field closure. These equations include degree variability but not the full history/correlations of who infected whom.

> [!theorem] Course order-1 threshold
> Near disease-free conditions, the non-trivial outbreak branch exists in this approximation when
> $$\boxed{\frac\lambda\mu>\frac{\langle z\rangle}{\langle z^2\rangle}.}$$
> The **second moment** appears because a randomly traversed link is especially likely to reach a high-degree node.

> [!derivation]- Short derivation from an integrated infection pressure
> Let $\Phi(t)=\int_0^t\Theta(u)\,du$. With $s_z(0)\simeq1$, integrating $\dot s_z=-\lambda zs_z\Theta$ gives $s_z(t)\simeq e^{-\lambda z\Phi(t)}$.
>
> Integrate $\dot r_z=\mu i_z$ and use $\Theta=\sum_z zP(z)i_z/\langle z\rangle$. At the final state $i_z(\infty)=0$, one obtains
> $$\Phi_\infty=\frac{1}{\mu}\left[1-\frac{1}{\langle z\rangle}\sum_z zP(z)e^{-\lambda z\Phi_\infty}\right]=:h(\Phi_\infty).$$
> The zero solution always exists. The positive solution appears when $h'(0)>1$, and
> $$h'(0)=\frac\lambda\mu\frac{\langle z^2\rangle}{\langle z\rangle}.$$
> Hence the stated order-1 threshold. This is a **mean-field** derivation, not an exact SIR result on every graph.

> [!example] ER with $\langle z\rangle=4$
> - **Order 0:** $\lambda/\mu>1/4$.
> - **Order 1:** Poisson degrees give $\langle z^2\rangle=4^2+4=20$, hence $\lambda/\mu>4/20=1/5$.
>
> Allowing degree variability **lowers the predicted threshold**.

## 4. Relation to percolation — and its limits

> [!proposition] Transmissibility and branching
> An infectious node can transmit across a given edge before recovery. If infection and recovery are **independent exponential clocks** with rates $\lambda$ and $\mu$, the probability of transmission along that edge is
> $$\boxed{\mathcal T=\Pr(T_{\rm infection}<T_{\rm recovery})=\frac{\lambda}{\lambda+\mu}\approx\frac\lambda\mu\quad(\lambda\ll\mu).}$$
> A locally tree-like *branching/percolation* heuristic gives a threshold
> $$\boxed{\mathcal T\left(\frac{\langle z^2\rangle}{\langle z\rangle}-1\right)>1.}$$
> The **$-1$** excludes the edge used to arrive. The lecture recovers the order-1 **scaling** by approximating $\mathcal T\approx\lambda/\mu$ and $\langle z^2\rangle/\langle z\rangle-1\approx\langle z^2\rangle/\langle z\rangle$ for large excess degree.

> [!warning] Do not conflate the two thresholds
> The lecture's $\lambda/\mu>\langle z\rangle/\langle z^2\rangle$ belongs to the **degree-based mean-field ODE**. The $\mathcal T\kappa>1$ condition belongs to an **edge-based branching approximation**. They need not coincide numerically for finite moments. Moreover, exponential recovery creates dependencies among transmissions from the same infected node, so treating all edges as *independent* bond-percolation trials is an additional simplification. See [[Percolation and robustness]].

## 5. Scale-free consequence and exam focus

> [!theorem] Vanishing threshold in a heavy-tailed limit
> For $P(z)\sim z^{-\gamma}$ with $2<\gamma<3$, $\langle z\rangle$ stays finite but $\langle z^2\rangle\to\infty$ as the network grows. Both the lecture's order-1 threshold and the branching threshold **tend to zero**. Thus there is **no positive asymptotic critical infection-to-recovery ratio** under these assumptions. This does **not** imply that every seed causes a giant outbreak with probability $1$ on a finite network.

> [!exam] Remember
> - Order 0: $\lambda/\mu>1/\langle z\rangle$.
> - Order 1: $\lambda/\mu>\langle z\rangle/\langle z^2\rangle$ (**course result**).
> - The epidemic has a transient **I peak**; **R** accumulates and measures the final outbreak size.
> - Percolation provides the intuition: following an edge samples **high-degree nodes disproportionately**.

> [!selftest]- Check your understanding
> 1. Why is $\dot r=\mu i$ but $\dot s$ negative? — Recovery adds R; infection removes S.
> 2. Which quantity changes the order-1 threshold relative to order 0? — The degree second moment $\langle z^2\rangle$.
> 3. Why can a finite heavy-tailed graph still have outbreaks that die out? — Extinction has positive probability, and its degree moments are finite.

---
Related: [[SI and SIS models]] · [[Binary-state dynamics]] · [[Percolation and robustness]] · [[Power laws]]
