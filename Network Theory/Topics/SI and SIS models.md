---
tags: [data5441, ch11, dynamics]
aliases: [SI model, SIS model, Epidemic simulation]
---
# SI and SIS models (discrete simulation)

> [!abstract] Summary
> **SI** has infection without recovery; **SIS** has infection followed by a return to susceptibility. Tutorial 11 simulates both by **random asynchronous node updates**. Simple mean-field equations predict logistic SI growth and an SIS persistence threshold, but **every finite SIS system without imported infections eventually reaches the disease-free absorbing state**.
> Chapter: [[Ch11 Cascades and binary models]] · **Week 11**, Tutorial 11 §3 (linked to Week 12 continuous-time epidemic lecture).

## 1. Individual node-update rules

> [!definition] Tutorial 11 convention
> Each elementary step chooses **one node uniformly at random**. Write $m_i$ for its number of infected neighbours. If the selected node is
> - **Susceptible (S):** it becomes infected (I) with probability
> $$\boxed{P(S\to I\mid m_i)=1-(1-\lambda)^{m_i}}.$$
> - **Infected (I):** in **SI**, it stays infected; in **SIS**, it recovers to S with probability $\mu$.
>
> Here $\lambda,\mu\in[0,1]$ are **per-selection probabilities**, and $N$ selections constitute approximately one sweep. These are not yet continuous-time transition rates.

> [!derivation]- Why is infection probability $1-(1-\lambda)^m$?
> Suppose each of the $m$ infected neighbours independently transmits with probability $\lambda$ during the selected node's update. The event **no transmission** has probability $(1-\lambda)^m$, so infection has the complementary probability. For $\lambda\ll1$ and moderate $m$,
> $$1-(1-\lambda)^m=\lambda m+O(\lambda^2 m^2),$$
> explaining the familiar infection rate $F_{z,m}\approx\lambda m$ in [[Binary-state dynamics]].

## 2. SI: infection spreads, nobody recovers

> [!proposition] Long-time SI on a finite graph
> If $\lambda>0$, then with fair random updates, **every vertex in a connected component containing an initial infected node eventually becomes infected almost surely**. Components without initially infected vertices remain susceptible. On a connected graph with at least one infected seed, $\rho(t)\to1$.

> [!derivation]- Homogeneous mean-field SI
> Assume every node has about $c=\langle z\rangle$ neighbours and neighbouring states are independent. The infection gain is proportional to **susceptible fraction** $(1-\rho)$ times **infected-contact density** $c\rho$:
> $$\dot\rho=\lambda c\rho(1-\rho).$$
> For $\rho(0)=\rho_0\in(0,1)$, separation of variables gives
> $$\boxed{\rho(t)=\frac1{1+(\rho_0^{-1}-1)e^{-\lambda ct}}}. $$
> This **logistic curve** is a continuum approximation to the discrete tutorial simulation; a disconnected graph or correlations can invalidate it.

## 3. SIS: competition between infection and recovery

> [!definition] Homogeneous mean-field SIS
> Add the loss of infected nodes due to recovery:
> $$\boxed{\dot\rho=\lambda c\rho(1-\rho)-\mu\rho=\rho[\lambda c(1-\rho)-\mu].}$$
> Its fixed points are $\rho_0^*=0$ and, when positive,
> $$\boxed{\rho_\mathrm{endemic}^*=1-\frac{\mu}{\lambda c}}.$$
> Linearising about $\rho=0$ gives $\dot\rho\approx(\lambda c-\mu)\rho$, so the **homogeneous mean-field** persistence condition is
> $$\boxed{\frac{\lambda}{\mu}>\frac1c\quad\text{(or }\lambda c>\mu\text{)}.}$$

![[Assets/w11-si-sis-meanfield.png|760]]

> [!remark] How to interpret the curves
> The plot solves the **mean-field ODEs**, not a stochastic network simulation. SI approaches full infection; SIS can approach a non-zero **mean-field plateau** above its threshold or decay below it. More accurate degree-heterogeneous epidemic approximations are introduced in [[SIR model and epidemic threshold]].

> [!theorem] Finite SIS always becomes extinct eventually
> In any **finite** graph, with $\mu>0$ and no external infection, the all-susceptible configuration is **absorbing** (no infected neighbour can start a new infection). It is reachable with positive probability from every configuration; hence SIS reaches it **almost surely**, even when mean-field predicts a stable endemic fraction.

> [!proof]- Why an apparent endemic state can still disappear
> From any state with $k$ infected nodes, there is a positive-probability sequence of selections in which each currently infected node is selected and recovers before any new infection occurs. That reaches the all-S state. On a finite Markov chain with this absorbing state reachable from every state, absorption happens eventually with probability $1$. A long-lived plateau is therefore **metastable**, not an exact non-zero stationary prevalence of a finite closed SIS system.

## 4. Tutorial algorithm and interpretation

> [!algorithm] Random asynchronous SIS simulation
> 1. Initialise the graph and the set of infected nodes; choose $\lambda,\mu$.
> 2. Repeat $N$ times per sweep: select a node uniformly **with replacement**.
> 3. If S, count infected neighbours and infect with probability $1-(1-\lambda)^m$; if I, recover with probability $\mu$.
> 4. Update its state **immediately**; record $\rho(t)$ after each sweep.
> 5. Repeat for several random seeds, graph types and parameters, and interpret plateaux versus extinction separately.

> [!exam] SI versus SIS
> **SI:** infection is permanent; any initially infected component ultimately becomes all-I (if $\lambda>0$). **SIS:** recovery permits a disease-free absorbing state; a persistent fraction is a **large-population or finite-time** concept. Always distinguish the tutorial's **probabilities per update** from continuous-time **rates**.

> [!selftest]- Check your understanding
> 1. With two infected neighbours and $\lambda=0.1$, what is the per-update infection probability? — $1-0.9^2=0.19$.
> 2. For $c=5$, $\lambda=0.02$, $\mu=0.2$, is homogeneous SIS above threshold? — No, since $\lambda c=0.1<0.2$.
> 3. How can SIS have an endemic mean-field fixed point but certain eventual extinction at finite $N$? — Mean-field neglects fluctuations and the absorbing state.

---
Related: [[Binary-state dynamics]] · [[SIR model and epidemic threshold]] · [[Threshold model and cascades]]
