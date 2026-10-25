---
tags: [dynamics]
---

# Epidemic models

Infection provides a simple example of state dynamics on a network. The central questions are whether infection reaches new vertices, how quickly it grows, and whether recovery can extinguish it. Week 11’s simulations use **discrete random asynchronous updates**. Continuous-rate equations are useful approximations or supplementary models, not the same definition.

## The discrete SI and SIS rules

> [!definition] One selected-node update
> Let $m$ be the number of infected neighbours when a vertex is selected.
>
> - In **SI**, a susceptible vertex becomes infected with probability $1-(1-\lambda)^m$; infected vertices remain infected.
> - In **SIS**, the susceptible rule is the same, while an infected vertex returns to susceptible with probability $\mu$.
>
> Here $\lambda,\mu\in[0,1]$ are probabilities **per selection**. Apply only the rule for the vertex’s state at the beginning of its selection. A sweep makes $N$ independent uniform selections with replacement, so a vertex may change more than once across a sweep.

**Derivation of the infection probability.** Each of $m$ infected neighbours fails to transmit with probability $1-\lambda$. Independent failures have probability $(1-\lambda)^m$; complementing gives the rule. An isolated susceptible vertex cannot become infected.

For SI on a finite fixed graph, $\lambda>0$ and fair repeated updates eventually infect every vertex in a component containing an initial infection, almost surely. Other components remain susceptible. Infection cannot disappear, but a single seed need not reach the whole graph. At $\lambda=0$, only the initial seeds remain infected.

> [!code]- One simulator for the tutorial’s SI/SIS convention
> ```python
> import networkx as nx
> import numpy as np
>
> def simulate_infection(g, seeds, lam=0.02, mu=0.0, sweeps=200, seed=13):
>     seeds = set(seeds)
>     if (not 0 <= lam <= 1 or not 0 <= mu <= 1 or len(g) == 0
>         or not set(seeds) <= set(g) or sweeps < 0):
>         raise ValueError('Check probabilities, seeds and observation window')
>     rng = np.random.default_rng(seed)
>     nodes = list(g)
>     infected = set(seeds)
>     history = [len(infected)/len(nodes)]
>     for _ in range(sweeps):
>         if not infected:
>             history.extend([0.0] * (sweeps + 1 - len(history)))
>             break
>         for _ in nodes:
>             v = nodes[rng.integers(len(nodes))]
>             if v in infected:
>                 if rng.random() < mu:
>                     infected.remove(v)
>             else:
>                 m = sum(u in infected for u in g.neighbors(v))
>                 if rng.random() < 1 - (1-lam)**m:
>                     infected.add(v)
>         history.append(len(infected)/len(nodes))
>     return np.asarray(history)
>
> G = nx.erdos_renyi_graph(100, 10/99, seed=5441)
> trajectory = simulate_infection(G, {0, 1, 2}, lam=.01, mu=.08)
> ```
> `mu=0` gives SI. This routine returns a finite observation window, not an equilibrium claim. Padding after observed extinction is valid because infection cannot restart. Do not stop merely because two successive infected counts coincide.

## Mean-field reasoning for revision

Ignoring state correlations, replacing degree by $c$ and linearising weak infection pressure gives the SI approximation
$$\dot\rho\approx\lambda c\rho(1-\rho),\qquad\rho(t)\approx\frac1{1+[(1-\rho_0)/\rho_0]e^{-\lambda ct}}.$$
This suggests curves with the same initial fraction collapse under $\tau=\lambda ct$. With a **single seed** at different $N$, $\rho_0=1/N$ changes: a time shift is also needed. In the logistic approximation, $\log[\rho/(1-\rho)]=\lambda ct+\log[\rho_0/(1-\rho_0)]$. Stochastic early growth and disconnectedness can spoil this collapse.

For a fixed degree $k$ under an independent-neighbour closure, the selected susceptible’s average infection probability is $1-(1-\lambda\rho)^k$. Its first-order expansion at $\rho=0$ is $\lambda k\rho$. The homogeneous SIS approximation therefore gives
$$\dot\rho\approx\lambda c\rho(1-\rho)-\mu\rho.$$
Its zero state is linearly unstable when $\lambda c>\mu$, and its positive fixed point is $\rho^*=1-\mu/(\lambda c)$ in that regime. These are mean-field predictions in sweep-time units, not exact thresholds for every discrete graph process.

![[Assets/tutorial-11-cell-60-plot-1.png|720]]
*Supplied Tutorial 11, cell 60: fixed $\lambda=0.004,\mu=0.08$ gives the mean-field reference $c_c=20$. Simulation points are late-window averages with variation across runs, not proof of eternal infection.*

> [!theorem] Finite SIS has an absorbing extinction state
> On a finite closed graph with $\mu>0$ under the stated random asynchronous rule, infection becomes extinct almost surely. There are no spontaneous external infections.

**Proof.** The all-susceptible state is absorbing. From any configuration, there is a positive-probability sequence that selects each currently infected vertex for recovery without selecting susceptible vertices in between. Thus extinction is reachable from every state. In a finite Markov chain this excludes any other closed recurrent class, so absorption occurs almost surely. $\square$

A long-lived positive infected fraction is therefore a metastable finite-window observation or a limit/conditioned description. Runs with small initial infection can die out even in a regime where a mean-field endemic solution exists.

## Supplementary: continuous-rate and SIR models

The following material was present in Jenny’s notes and the earlier vault. It is useful background, but it is **not additional Week 11 lecture coverage**: SIR and continuous-time results should be revisited against the forthcoming Week 12 material.

In continuous time, use infection rate $\beta$ per infected edge and recovery rate $\delta$, both with units of inverse time. SI has no recovery; SIS returns to susceptibility; SIR moves irreversibly from susceptible to infected to recovered/removed.

> [!definition] Homogeneous continuous-time SIR closure
> With mean degree $c$ and fractions $s,i,r$,
> $$\dot s=-\beta csi,\qquad\dot i=\beta csi-\delta i,\qquad\dot r=\delta i,\qquad s+i+r=1.$$
> Early growth requires $\beta c s_0>\delta$; setting $s_0=1$ is a small-seed approximation.

For $r_0=0$, dividing $\dot s$ by $\dot r$ and integrating gives $s=s_0e^{-(\beta c/\delta)r}$. With $i_\infty=0$,
$$r_\infty=1-s_0e^{-(\beta c/\delta)r_\infty}.$$
The exactly infection-free initial state stays infection-free; the positive limiting branch is interpreted through an introduced small infection.

Degree-based closures replace a single infected fraction by $i_k$ and $\Theta=\sum_k kp_ki_k/\langle k\rangle$. For SIS,
$$\dot i_k=-\delta i_k+\beta k(1-i_k)\Theta.$$
Its linearisation predicts $\beta/\delta>\langle k\rangle/\langle k^2\rangle$. A node-based independence closure instead has Jacobian $\beta A-\delta I$ and threshold $\beta\rho(A)>\delta$. They are different approximation schemes.

Finally, fixed infectious duration $\tau$ with Poisson transmission gives edge transmissibility $T=1-e^{-\beta\tau}$. Exponential duration with rate $\delta$ gives $T=\beta/(\beta+\delta)$, approximately $\beta/\delta$ only when that ratio is small. A locally tree-like early SIR branching criterion is $T\kappa>1$. Shared random recovery times can correlate outgoing transmissions, so a single mean $T$ does not make every observable identical to independent bond percolation.

## For revision

- Write the selected-node SI/SIS probabilities and explain a with-replacement sweep.
- Derive the approximate product $\lambda c$, SI time rescaling and SIS balance $\lambda c\approx\mu$.
- Distinguish a finite observation-window plateau from survival forever, and keep discrete probabilities separate from continuous rates. See [[Binary dynamics and cascades]] and [[Percolation and robustness]].

> [!reference]- Sources
> Lecture Week 11 pp.1–4; Tutorial 11 §3, Ex.3.1–3.2 and cells 50, 58, 60. Jenny’s notes Week 11 provides supplementary SIR/mean-field material; forthcoming Week 12 has not been supplied. Newman §§16.1–16.3, 16.5–16.7. The figure is a supplied notebook result; approximations and proofs are stated in the text.
