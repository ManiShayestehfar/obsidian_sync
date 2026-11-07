---
tags: [data5441, ch11, dynamics]
aliases: [Binary dynamics, Voter model, Majority rule, Synchronous update, Asynchronous update]
---
# Binary-state dynamics on networks

> [!abstract] Summary
> Each node has a state $\phi_i\in\{0,1\}$. It flips $0\to1$ with rate $F$ and $1\to0$ with rate $R$, where the rates depend on the degree $z_i$ and the number $m_i$ of neighbours in state $1$. SI, SIS, voter, majority and threshold models are all special cases. The update schedule is part of the model.
> Chapter: [[Ch11 Cascades and binary models]]

> [!definition] Binary-state model (Gleeson)
> Each node $i$ has a state $\phi_i(t)\in\{0,1\}$. Let
> $$m_i=\sum_jA_{ij}\phi_j$$
> be the number of neighbours in state $1$. The transition rates $F_{z,m}$ ($0\to1$) and $R_{z,m}$ ($1\to0$) depend on $z_i$ and $m_i$. The main quantities are
> $$\rho(t)=\frac1N\sum_i\phi_i(t),\qquad\rho_\infty=\lim_{t\to\infty}\rho(t).$$

| Model | $F_{z,m}$ | $R_{z,m}$ |
|---|---|---|
| SIS | $\lambda m$ | $\mu$ |
| SI | $\lambda m$ | $0$ |
| Voter | $m/z$ | $(z-m)/z$ |
| Majority vote | $\approx1$ if $m>z/2$, $\tfrac12$ if $m=z/2$, $\approx0$ if $m<z/2$ | symmetric |
| Threshold | $0$ if $m<M_z$, $1$ if $m\ge M_z$ | $0$ |

> [!example] Central questions
> - **Disease models (SI):** does $\rho_\infty>0$ (an outbreak) occur from $\phi_i(0)=0$ for almost all $i$?
> - **Voter model:** is there consensus, i.e. $\rho_\infty\in\{0,1\}$?

> [!definition] Update schedules
> - **Synchronous:** every node updates at once, $t\to t+\Delta t$, using the old configuration.
> - **Asynchronous:** one node updates at a time, $t'\to t'+\Delta t'$ with $\Delta t'=\Delta t/N$, so $N$ single updates make one sweep. Nodes are selected **randomly** (with replacement) or **sequentially** ($i=1,\dots,N$, or a random permutation).
>
> In one random sweep, a given node is never chosen with probability $(1-1/N)^N\to e^{-1}$.

> [!definition] Long-run behaviour
> - **Consensus:** all nodes have the same state.
> - **Mixed fixed point:** a non-constant configuration in which no node changes.
> - **Cycle:** the configuration repeats periodically.
>
> A constant $\rho(t)$ does **not** imply a fixed configuration.

> [!example] Period-2 cycle under synchronous majority
> Two linked nodes with states $(0,1)$ each adopt their neighbour's state: $(0,1)\to(1,0)\to(0,1)\to\cdots$, while $\rho=1/2$ stays constant.

> [!theorem] Asynchronous strict majority converges
> On a finite undirected graph, consider strict-majority updates (keep the state on a tie) with asynchronous random selection. Every actual flip lowers the number of disagreeing links, so the process reaches a fixed point almost surely. The fixed point need not be consensus.

> [!proof]-
> Suppose node $i$ flips. It had $a$ disagreeing and $b$ agreeing links with $a>b$. After the flip they swap roles, so the disagreement count changes by $b-a<0$. This count is a non-negative integer, so only finitely many flips can occur. While some node is unstable, random selection picks it eventually with probability $1$. $\square$

![[tutorial-11-cell-13-plot-2.png|600]]

> [!remark] Mean-field (degree-class) approximation
> Assume neighbours' states are independent, each in state $1$ with probability $\omega=\sum_zzP(z)\rho_z/\langle z\rangle$. Then
> $$\dot\rho_z=(1-\rho_z)\sum_mF_{z,m}B_{z,m}(\omega)-\rho_z\sum_mR_{z,m}B_{z,m}(\omega),\qquad B_{z,m}(\omega)=\binom zm\omega^m(1-\omega)^{z-m}.$$
> Independence is a closure **assumption**. The Week 12 SIR equations are of this type; see [[SIR model and epidemic threshold]].

> [!selftest]- Self-test
> 1. Give $F$ and $R$ for SIS and for the voter model.
> 2. Why can synchronous updating create oscillations that asynchronous updating avoids?

---
Related: [[Threshold model and cascades]] · [[SI and SIS models]] · [[SIR model and epidemic threshold]] · [[Evolutionary games on networks]]
