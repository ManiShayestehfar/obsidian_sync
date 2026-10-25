---
tags: [dynamics]
---

# Binary dynamics and cascades

A network becomes a dynamical system when each vertex receives a state and an update rule. The same graph can support consensus, persistent disagreement, oscillation or spreading depending on that rule. This chapter establishes the simulation language; [[Threshold cascades]] and [[Epidemic models]] specialise it.

## States and update conventions

> [!definition] Binary network process
> Let $X_i(t)\in\{0,1\}$ and $m_i(t)=\sum_jA_{ij}X_j(t)$, the number of active neighbours. The active fraction is $\rho(t)=N^{-1}\sum_iX_i(t)$. A model specifies when a vertex changes, how it chooses its new state, and how updates are scheduled.
>
> In continuous time, rates $F_{k,m}$ and $R_{k,m}$ describe $0\to1$ and $1\to0$ events; a rate $r$ gives event probability $r\,dt+o(dt)$ over a short interval. The tutorial instead uses discrete update probabilities, which must lie in $[0,1]$.

| Schedule | Meaning of one step/sweep | Information used |
| --- | --- | --- |
| Synchronous | Update every vertex once | All new states computed from the same old configuration |
| Sequential asynchronous | Visit a specified order | Later updates see earlier changes |
| Random permutation | Visit every vertex once in a fresh order | Exactly one selection per vertex per sweep |
| Random with replacement | Make $N$ independent uniform selections | Each vertex selected once only **on average** |

These schedules need not produce the same process after a change of clock. In one with-replacement sweep, a particular vertex is not selected with probability $(1-1/N)^N$, approaching $e^{-1}$.

## Majority dynamics and its attractors

Use strict neighbour majority and retain the current state on a tie. Isolates therefore retain their states. This differs from a voter model, which copies one randomly selected neighbour.

> [!definition] Long-run outcomes
> **Consensus** means every vertex has the same state. A **mixed fixed point** is a nonconstant configuration in which no update can change a state. A **cycle** returns periodically to earlier full configurations. An unchanged value of $\rho(t)$ does not by itself imply a fixed configuration.

The synchronous rule on two adjacent vertices with states $(0,1)$ swaps them to $(1,0)$ and back: a period-two orbit with constant $\rho=1/2$. Mixed fixed points can arise when adjacent groups each retain their own local majority.

> [!theorem] Asynchronous strict-majority descent
> On a finite unweighted undirected graph, every actual asynchronous strict-majority flip decreases the number of disagreeing edges. With fair random vertex selection, the process reaches a fixed point almost surely; the fixed point need not be consensus.

**Proof.** If a vertex has $a$ disagreeing and $b$ agreeing incident edges with $a>b$, flipping changes the disagreement count by $b-a<0$. A tie is not flipped. This nonnegative integer can decrease only finitely often. Whenever an unstable vertex remains, independent uniform selections eventually choose an unstable vertex with probability one, causing another decrease. Thus the process cannot remain forever outside the fixed configurations. $\square$

![[tutorial-11-cell-13-plot-2.png|650]]
*Supplied Tutorial 11, cell 13: examples of synchronous consensus, a mixed fixed point and a period-two cycle. Constant active fraction can conceal a changing configuration.*

> [!code]- Correct synchronous and asynchronous sweeps
> ```python
> import networkx as nx
> import numpy as np
>
> def majority_sweep(g, state, rng, synchronous=True):
>     current = dict(state)
>     nodes = list(g)
>     def next_state(v):
>         active = sum(current[u] for u in g.neighbors(v))
>         k = g.degree(v)
>         return 1 if 2*active > k else 0 if 2*active < k else current[v]
>     if synchronous:
>         return {v: next_state(v) for v in nodes}  # current remains unchanged
>     for _ in nodes:
>         v = nodes[rng.integers(len(nodes))]
>         current[v] = next_state(v)
>     return current
>
> G = nx.path_graph(2)
> rng = np.random.default_rng(13)
> state = {0: 0, 1: 1}
> print(majority_sweep(G, state, rng, synchronous=True))
> ```
> Check stability by testing whether **any vertex is eligible to change**, not by observing one sweep with no flips. Randomness can leave eligible vertices unselected. For deterministic synchronous dynamics, repeated full configurations detect cycles; repetition in a stochastic process does not establish a deterministic attractor.

## Approximation beyond direct simulation

For degree classes with law $p_k$ and active fraction $\rho_k$, an uncorrelated-neighbour mean-field closure uses
$$\omega=\frac{\sum_k kp_k\rho_k}{\langle k\rangle},\qquad B_{k,m}(\omega)=\binom{k}{m}\omega^m(1-\omega)^{k-m}.$$
Then a continuous-time binary model is approximated by
$$\dot\rho_k=(1-\rho_k)\sum_mF_{k,m}B_{k,m}(\omega)-\rho_k\sum_mR_{k,m}B_{k,m}(\omega).$$
Activation contributes positively and deactivation negatively. Degree weighting comes from sampling an edge endpoint. Independence of neighbouring states is a **closure assumption**, not a consequence of sparsity. The supplied Week 11 tutorial focuses on explicit updates; this equation is supplementary background from Jenny’s notes and the cited binary-dynamics framework.

## For revision

- Specify the state space, transition rule, tie rule and schedule before discussing outcomes.
- Explain why a synchronous cycle can disappear under asynchronous updates.
- Distinguish continuous rates from probabilities per selected-node update, and identify a genuine fixed point using the full configuration.

> [!reference]- Sources
> Lecture Week 11 pp.1–4; Tutorial 11 §1 and Ex.1.1, especially cells 9 and 13. Jenny’s notes Week 11 provides supplementary mean-field material. The asynchronous descent proof is given explicitly above. Newman Chapter 17 supplies general dynamical-systems context. The figure is a supplied notebook output.
