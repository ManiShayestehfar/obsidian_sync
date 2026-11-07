---
tags: [data5441, ch11, dynamics]
aliases: [SI model, SIS model, Epidemic simulation]
---
# SI and SIS models (discrete simulation)

> [!abstract] Summary
> In tutorial 11, susceptible nodes are infected with probability $1-(1-\lambda)^m$ when selected, and infected nodes recover with probability $\mu$ (SIS). SI on a connected graph eventually infects everyone. Mean field predicts an SIS threshold at $\lambda\langle z\rangle=\mu$, but finite SIS always dies out eventually.
> Chapter: [[Ch11 Cascades and binary models]]

> [!definition] One asynchronous update (tutorial convention)
> Pick a node uniformly at random. Let $m$ be its number of infected neighbours.
> - **S node:** becomes I with probability $1-(1-\lambda)^m$.
> - **I node:** in SI, stays I; in SIS, becomes S with probability $\mu$.
>
> $\lambda$ and $\mu$ are probabilities per selection, and $N$ selections make one sweep.

> [!proof]- Infection probability
> Each of the $m$ infected neighbours independently fails to transmit with probability $1-\lambda$. All fail with probability $(1-\lambda)^m$, so infection occurs with probability $1-(1-\lambda)^m\approx\lambda m$ for small $\lambda$. $\square$

> [!proposition] SI long-time behaviour
> On a finite graph with $\lambda>0$, every node in a component containing an initial infection is eventually infected (almost surely). Other components stay susceptible.

> [!theorem] Homogeneous mean-field SI and SIS
> Ignore correlations and replace degree by $\langle z\rangle$.
> - **SI:** $\dot\rho=\lambda\langle z\rangle\rho(1-\rho)$, a logistic curve $\rho(t)=\Big[1+\frac{1-\rho_0}{\rho_0}e^{-\lambda\langle z\rangle t}\Big]^{-1}$. Curves collapse when plotted against $\lambda\langle z\rangle t$, for equal $\rho_0$.
> - **SIS:** $\dot\rho=\lambda\langle z\rangle\rho(1-\rho)-\mu\rho$. The state $\rho=0$ is unstable iff $\lambda\langle z\rangle>\mu$, in which case $\rho^*=1-\dfrac{\mu}{\lambda\langle z\rangle}$.

> [!theorem] Finite SIS dies out
> On a finite graph with $\mu>0$ and no external infection, the all-susceptible state is absorbing and reachable from every state. So extinction happens almost surely. A long-lived endemic plateau is **metastable**.

> [!proof]-
> From any configuration, the sequence "select each infected node in turn and let it recover" has positive probability and ends at all-S. A finite Markov chain with an absorbing state reachable from everywhere is absorbed almost surely. $\square$

![[tutorial-11-cell-60-plot-1.png|600]]

> [!selftest]- Self-test
> 1. Derive $1-(1-\lambda)^m$.
> 2. What is the mean-field SIS threshold? — $\lambda\langle z\rangle=\mu$.
> 3. Why does finite SIS die out? — The all-susceptible state is absorbing.

---
Related: [[Binary-state dynamics]] · [[SIR model and epidemic threshold]]
