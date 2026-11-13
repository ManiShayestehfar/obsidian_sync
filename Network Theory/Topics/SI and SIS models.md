---
tags: [data5441, ch11, dynamics]
aliases: [SI model, SIS model, Epidemic simulation]
---
# SI and SIS models (discrete simulation)

> [!abstract] Summary
> The Week 11 tutorial models infection through **random asynchronous node updates**. A susceptible node with $m$ infected neighbours becomes infected with probability $1-(1-\lambda)^m$ **when selected**. SI has no recovery; SIS adds recovery probability $\mu$ per selection. The main exercise is to understand the effects of $\lambda$, $\mu$, $N$ and $\langle z\rangle$ on $\rho_I(t)$.
> Chapter: [[Ch11 Cascades and binary models]] · **Tutorial 11, Section 3, Exercises 3.1–3.2** · lecture pp. 146, 151 · Jeny pp. 51–54.

## 1. The two models and the update convention

> [!definition] SI and SIS states
> - **S (susceptible):** can become infected by contact with an infected neighbour.
> - **I (infected):** can transmit infection to susceptible neighbours.
> - **SI:** $S\to I$; once infected, a node stays infected.
> - **SIS:** $S\to I\to S$; recovery creates a susceptible node again.
>
> Write $\rho_I(t)=\#\{\text{infected nodes}\}/N$; because there are two states, $\rho_S(t)=1-\rho_I(t)$.

> [!definition] Tutorial 11 time convention
> At each **elementary update**, choose one node uniformly at random (with replacement). If selected, it follows the transition rule for its **current state**. **$N$ selections form one sweep**. In this section, $\lambda,\mu\in[0,1]$ are probabilities *per applicable selection*, not continuous-time rates.

## 2. Infection through $m$ neighbours

> [!proposition] Per-selection infection probability
> Suppose the selected node is S and has $m$ neighbours in state I. Each infected neighbour transmits independently with probability $\lambda$. The probability that **none** succeeds is $(1-\lambda)^m$. Therefore
> $$\boxed{\Pr(S\to I\mid m,\text{ selected})=1-(1-\lambda)^m.}$$
>
> For $m=0$, the probability is $0$; for $m=1$, it is $\lambda$; for $m=2$, it is $2\lambda-\lambda^2$.

> [!remark] Small-$\lambda$ approximation
> Expanding the binomial expression gives
> $$1-(1-\lambda)^m\approx\lambda m\qquad (\lambda\ll1,\ m\lambda\ll1).$$
> This explains the $F_{k,m}=\lambda m$ **rate** that appears in the lecture's general framework, but the tutorial uses the **exact finite-probability expression** above.

## 3. SI: infection with no recovery

> [!algorithm] SI simulation (Tutorial 11)
> 1. Choose a graph, initial infected node(s), transmission probability $\lambda$ and number of sweeps.
> 2. Pick a node $i$ uniformly at random.
> 3. If $i$ is I, leave it unchanged. If it is S, count its infected neighbours $m_i$ and infect with probability $1-(1-\lambda)^{m_i}$.
> 4. Repeat $N$ times per sweep; record $\rho_I(t)$, and repeat sweeps.

> [!proposition] Qualitative long-time behaviour
> Because SI has no recovery, $\rho_I(t)$ **never decreases**. If $\lambda>0$ and the process is run indefinitely on a *finite* network, infection ultimately reaches every node in each connected component containing an initial infected node (with probability 1). Other components remain susceptible.

> [!example] Tutorial 11, Exercise 3.1: parameter effects
> The tutorial uses an ER graph with $p=\langle z\rangle/(N-1)$. Investigate the infected fraction for changing $\lambda$, $\langle z\rangle$ and $N$ **one parameter at a time**.
> - Increasing $\lambda$ usually makes infection spread **faster**.
> - Increasing $\langle z\rangle$ supplies **more possible infected contacts**.
> - If the graph is disconnected, an infection confined to one component cannot reach the others.
>
> **Curve collapse:** for sufficiently large, approximately homogeneous networks and small $\lambda$, the combination $\lambda\langle z\rangle$ largely controls the epidemic time scale. Plot the curves against $\tau=\lambda\langle z\rangle t$, using comparable initial fractions.

> [!proof]- Why $\lambda\langle z\rangle$ controls the SI time scale (mean-field approximation)
> Approximate the probability that a neighbour is infected by $\rho_I(t)$ and replace individual degrees by $\langle z\rangle$. In the small-$\lambda$ regime,
> $$\frac{d\rho_I}{dt}\approx\lambda\langle z\rangle\rho_I(1-\rho_I).$$
> Hence using $\tau=\lambda\langle z\rangle t$ gives $d\rho_I/d\tau\approx\rho_I(1-\rho_I)$, so the parameter dependence is largely absorbed into a rescaling of time. This is a **homogeneous mean-field approximation**, not an exact formula for each sampled graph.

## 4. SIS: recovery allows infection to disappear

> [!algorithm] SIS simulation (Tutorial 11)
> Follow the same random asynchronous scheme, but at each selection:
> - If the node starts the selection in S, infect with probability $1-(1-\lambda)^m$.
> - If it starts in I, recover to S with probability $\mu$.
>
> Use **only one of these rules** per selection. A node cannot be infected and recover in the same elementary update, although it may be selected more than once during a sweep.

> [!remark] Spreading versus recovery
> In SI the infected fraction is non-decreasing. In SIS, $\rho_I(t)$ can **rise and fall** because infection and recovery compete. The infection-free state $\rho_I=0$ is **absorbing**: with no infected nodes, no new infections are possible.

> [!proposition] Approximate SIS threshold (Tutorial 11, Exercise 3.2)
> For a homogeneous network in the small-$\lambda$ regime, the mean-field balance is
> $$\frac{d\rho_I}{dt}\approx\lambda\langle z\rangle\rho_I(1-\rho_I)-\mu\rho_I.$$
> At low prevalence $\rho_I\approx0$, the initial growth rate has sign $\lambda\langle z\rangle-\mu$. Thus the **approximate** change from decay to initial growth is
> $$\boxed{\lambda\langle z\rangle\approx\mu.}$$
> Here $\lambda$ and $\mu$ are the **tutorial's per-selection probabilities**; this approximation is most transparent when they are small.

> [!example] Notebook parameters
> For $\lambda=0.004$ and $\mu=0.08$, the homogeneous estimate predicts a transition near $\langle z\rangle\approx\mu/\lambda=20$. Exercise 3.2 varies average degree and estimates the **late-time infected fraction over a finite observation window**.

![[Assets/w11-si-sis-meanfield.png|640]]

> [!note] Figure scope
> These are **illustrative homogeneous mean-field trajectories**, not direct measurements from Tutorial 11's discrete random-graph simulation.

> [!remark] Finite observation window versus long-time limit
> SIS simulations may show a persistent positive **late-time plateau**. Nevertheless, on a finite network with $\mu>0$ and no external infections, the infection-free configuration is eventually reached almost surely. The tutorial therefore reports a **finite-window estimate** $\widehat\rho_\infty$, which is not necessarily the literal infinite-time limit.

## 5. Exam comparison

| Feature | SI | SIS |
|---|---|---|
| Susceptible becomes infected | $1-(1-\lambda)^m$ on selection | Same |
| Infected becomes susceptible | Never | With probability $\mu$ |
| Is infection irreversible? | Yes | No |
| Can $\rho_I(t)$ decrease? | No | Yes |
| Long-run question | How far does infection reach? | Spread versus recovery / finite-time persistence |

> [!selftest]- Quick checks
> 1. Derive the infection probability when a susceptible node has $m$ infected neighbours. — Complement of the probability that all $m$ attempts fail.
> 2. What does $\tau=\lambda\langle z\rangle t$ test? — Mean-field time-scale collapse in SI.
> 3. With $\lambda=0.004$, $\mu=0.08$, what degree marks the approximate SIS crossover? — $20$.
> 4. Why can a finite SIS run have a positive plateau although its true long-time infection count vanishes? — It has not yet reached the absorbing all-S configuration.

---
Related: [[Binary-state dynamics]] · [[Threshold model and cascades]] · [[SIR model and epidemic threshold]]
