---
tags: [data5441, ch11, dynamics]
aliases: [Binary dynamics, Voter model, Majority rule, Synchronous update, Asynchronous update]
---
# Binary-state dynamics on networks

> [!abstract] Summary
> **Week 11 starts with a fixed network and states that evolve on it.** For binary states $\phi_i\in\{0,1\}$, the probability of changing state depends on a node's degree $k_i$ and its number $m_i$ of active neighbours. The **update rule and update schedule** must both be specified: synchronous and asynchronous dynamics can have different long-time outcomes.
> Chapter: [[Ch11 Cascades and binary models]] · **2026 lecture pp. 144–147** · **Tutorial 11, Section 1** · Jeny pp. 51–52.

## 1. From a network to a dynamical system

> [!definition] Network, states and transitions
> Let $g$ be a sparse, simple graph on $N$ nodes, with adjacency matrix $A$ and node degrees $k_i=\sum_j A_{ij}$. Assign node $i$ the binary state $\phi_i(t)\in\{0,1\}$. Define
> $$m_i(t)=\sum_{j=1}^N A_{ij}\phi_j(t),\qquad 0\le m_i\le k_i.$$
> Thus $m_i$ counts the **neighbours in state 1**, not all active nodes in the network.
>
> The binary-state framework uses transition rates (or probabilities, for discrete updates)
> $$\boxed{0\xrightarrow{\,F_{k,m}\,}1,\qquad 1\xrightarrow{\,R_{k,m}\,}0.}$$
> The functions $F_{k,m}$ and $R_{k,m}$ encode the particular model.

> [!definition] Main observable
> The fraction of nodes in state 1 is
> $$\boxed{\rho(t)=\frac1N\sum_{i=1}^N\phi_i(t)}.$$
> We investigate the evolution of $\rho(t)$ and, when it exists, the long-time value $\rho_\infty=\lim_{t\to\infty}\rho(t)$. **The same $\rho$ can correspond to different network configurations.**

## 2. Models using the same framework

| Model | What state 1 represents | $0\to1$: $F_{k,m}$ | $1\to0$: $R_{k,m}$ |
|---|---|---|---|
| **SI** | Infected | Infection through infected neighbours | $0$ (no recovery) |
| **SIS** | Infected | Infection through infected neighbours | Recovery at rate $\mu$ |
| **Voter** | Opinion 1 | $m/k$ | $(k-m)/k$ |
| **Majority rule** | Opinion 1 | Choose the majority opinion | Choose the majority opinion |
| **Threshold** | Adopted an innovation | Adopt when $m/k>q_i$ | $0$ (irreversible adoption) |

> [!remark] Interpret the table carefully
> - For the **voter model**, a node copies a uniformly chosen neighbour. Consequently, a 0-node switches with probability $m/k$; a 1-node switches with probability $(k-m)/k$.
> - In **majority rule**, the node takes the strict majority of its neighbours' states. The Tutorial 11 convention is to **retain the current state on a tie**.
> - The SIS/SI **continuous-time rates** used in the Week 12 lecture and the **per-selection probabilities** used in Tutorial 11 are different conventions: see [[SI and SIS models]].
> - An isolated node ($k=0$) requires a convention; in the tutorial, it retains its state under majority and cannot be newly activated by the threshold rule.

![[Assets/w11-lecture-binary-table-crop.png|740]]
^binary-lecture-table

> [!note] Reading the lecturer's comparison table
> Lecture p. 146 shows several processes in the $F$/$R$ framework. The key exam skill is **recognising the transition rule**, not memorising every entry in the literature table.

## 3. Updating states: an essential modelling choice

> [!algorithm] Synchronous update — **all at once**
> 1. Start from the current vector $\phi(t)$.
> 2. Compute each proposed $\phi_i(t+1)$ from the **same old configuration** $\phi(t)$.
> 3. Replace all states simultaneously.
>
> The order in which the proposals are calculated does not change the outcome of this step.

> [!algorithm] Random asynchronous update — **one at a time** (Tutorial 11)
> 1. Select a node $i$ uniformly at random, **with replacement**.
> 2. Compute its new state using the **current** states of its neighbours.
> 3. Change only node $i$.
> 4. Repeat $N$ selections to obtain **one sweep**; repeat sweeps as required.
>
> A node may be selected several times, or not at all, within one sweep. **Sequential** and **random-permutation** asynchronous updating are other choices mentioned in the lecture.

> [!remark] Comparing time conventions
> One synchronous step updates all $N$ nodes; one asynchronous sweep makes $N$ *attempted* single-node updates. In the lecture's notation, $N\Delta t'=\Delta t$. In a random sweep, the probability that a specified node is never selected is $(1-1/N)^N\to e^{-1}$.

![[Assets/w11-update-schedules.png|640]]

## 4. Majority-rule dynamics and long-time outcomes

> [!definition] Strict majority with ties unchanged (Tutorial 11)
> If $m_i$ of the $k_i$ neighbours are in state 1, the proposed state is
> $$\phi_i^{\mathrm{new}}=\begin{cases}1,&2m_i>k_i,\\0,&2m_i<k_i,\\\phi_i,&2m_i=k_i.\end{cases}$$

> [!example] Why the update schedule matters
> On a single edge, take initial states $(0,1)$. Synchronous majority makes both nodes copy their neighbour:
> $$(0,1)\longrightarrow(1,0)\longrightarrow(0,1)\longrightarrow\cdots.$$
> This is a **period-two cycle**, with $\rho(t)=1/2$ throughout. Under asynchronous updating, the first node chosen copies the other, giving $(0,0)$ or $(1,1)$: **consensus**.

> [!definition] Classifying simulation outcomes (Tutorial 11, Exercise 1.1)
> - **Consensus:** all nodes are 0, or all are 1.
> - **Mixed fixed point:** both states occur, but no node changes on further updates.
> - **Oscillatory/cyclic behaviour:** configurations repeat without settling (possible under synchronous updates).
>
> **Do not infer a fixed point just because $\rho(t)$ is constant.** Inspect the node states, or check the transition rule.

## 5. Degree-class approximation (Jeny's Week 11 notes)

> [!remark] Motivation and assumption
> Simulating each node separately becomes expensive for large networks. Jeny presents a **degree-class mean-field approximation**: instead of tracking every $\phi_i$, track $\rho_k(t)$, the fraction of degree-$k$ nodes in state 1. Approximate the states of a node's neighbours as independent.
>
> The probability that a random *neighbour* is in state 1 is
> $$\omega(t)=\frac{\sum_k kP(k)\rho_k(t)}{\langle k\rangle}.$$
> Under the independence assumption, the number $m$ of active neighbours of a degree-$k$ node follows
> $$B_{k,m}(\omega)=\binom{k}{m}\omega^m(1-\omega)^{k-m}.$$

> [!proposition] Mean-field equation (as presented by Jeny)
> $$\boxed{\frac{d\rho_k}{dt}=(1-\rho_k)\sum_{m=0}^{k}F_{k,m}B_{k,m}(\omega)-\rho_k\sum_{m=0}^{k}R_{k,m}B_{k,m}(\omega).}$$
> **Meaning:** rate entering state 1 minus rate leaving state 1. The binomial factor averages over the number of active neighbours. This is an **approximation**, not an exact equation for a fixed graph.

> [!exam] Essential distinctions
> 1. **Graph structure:** $A_{ij}$ and $k_i$ specify who interacts.
> 2. **Local influence:** $m_i=\sum_jA_{ij}\phi_j$.
> 3. **Transition model:** $F_{k,m}$ and $R_{k,m}$ specify what can happen.
> 4. **Update schedule:** simultaneous versus one-node-at-a-time updates specify when it happens.
> 5. **Outcome:** consensus, mixed fixed point, or cycle; $\rho(t)$ alone may not distinguish them.

> [!selftest]- Quick checks
> 1. In a voter model, why is $F_{k,m}=m/k$? — A uniform neighbour is in state 1 with probability $m/k$.
> 2. With 4 neighbours, 2 active, and a strict-majority rule, what happens? — A tie; retain the current state.
> 3. What is the difference between one asynchronous *update* and one *sweep*? — One selected node versus $N$ selections.
> 4. Can $\rho(t)$ stay constant while the configuration changes? — Yes; the two-node synchronous cycle is an example.

---
Related: [[Threshold model and cascades]] · [[SI and SIS models]] · [[SIR model and epidemic threshold]] · [[Evolutionary games on networks]]
