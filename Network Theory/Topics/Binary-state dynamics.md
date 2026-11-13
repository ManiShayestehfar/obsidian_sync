---
tags: [data5441, ch11, dynamics]
aliases: [Binary dynamics, Voter model, Majority rule, Synchronous update, Asynchronous update]
---
# Binary-state dynamics on networks

> [!abstract] Summary
> Here the **graph is fixed**, but each node has a changing binary state $\phi_i\in\{0,1\}$. Local rules determine state changes, and the **update schedule** can change the outcome. The same framework includes voter, majority, threshold and epidemic dynamics; distinguish **transition rates** (continuous time) from **per-update probabilities** (discrete simulation).
> Chapter: [[Ch11 Cascades and binary models]] · **Week 11**, lecture pp. 144–147; Tutorial 11 §1.

## 1. General binary-state framework

> [!definition] States, neighbourhood counts and transitions
> For an undirected graph with adjacency matrix $A$, let
> $$\phi_i(t)\in\{0,1\},\qquad z_i=\sum_jA_{ij},\qquad m_i(t)=\sum_jA_{ij}\phi_j(t).$$
> Thus $m_i$ is the number of neighbours of node $i$ presently in state $1$. In a **continuous-time** model, let $F_{z,m}$ denote the rate $0\to1$ and $R_{z,m}$ the rate $1\to0$. The principal observable is
> $$\rho(t)=\frac1N\sum_i\phi_i(t),$$
> the fraction in state $1$. It may settle, oscillate or fluctuate; a constant fraction does **not** imply the node states are unchanged.

| Rule (interpretation) | $0\to1$ | $1\to0$ |
|---|---|---|
| **SI** (infection only) | rate $\lambda m$ | $0$ |
| **SIS** (infection and recovery) | rate $\lambda m$ | rate $\mu$ |
| **Voter** (copy random neighbour) | probability $m/z$ | probability $(z-m)/z$ |
| **Strict majority** (adopt majority) | switch if $m>z/2$ | switch if $m<z/2$ |
| **Permanent threshold adoption** | activate if $m/z>q_i$ | $0$ |

> [!remark] These rows have different time conventions
> SI and SIS rates are *continuous-time* descriptions (or small-step approximations). Voter and majority rules here specify the outcome of a **node-selection update**. For isolated nodes, $m/z$ is undefined; specify an explicit convention, normally **no change**. See [[SI and SIS models]] and [[Threshold model and cascades]].

## 2. Update order is part of the model

> [!definition] Synchronous versus asynchronous
> - **Synchronous:** update *all* nodes simultaneously using the same previous-time configuration.
> - **Asynchronous random:** choose one node uniformly, update its state, and repeat; one **sweep** means $N$ selections. Choices are usually with replacement.
> - **Asynchronous sequential / random permutation:** visit nodes one at a time in a specified or reshuffled order, updating the current configuration after each move.
>
> In random-with-replacement sweeps, a particular node is not selected with probability $(1-1/N)^N\to e^{-1}$; therefore **one sweep does not guarantee one update per node**.

![[Assets/w11-update-schedules.png|710]]

> [!example] Why synchronous majority can oscillate
> Two linked nodes in states $(0,1)$ each see the opposite value. Updating both simultaneously gives $(0,1)\to(1,0)\to(0,1)\to\cdots$, a **period-two cycle** with $\rho=1/2$. If node $1$ is updated first asynchronously, $(0,1)\to(1,1)$, an absorbing consensus. The model rule alone does not determine the outcome: the **schedule matters**.

## 3. Long-time outcomes and a useful convergence argument

> [!definition] Attractors and terminology
> - **Consensus:** all nodes are $0$, or all are $1$.
> - **Mixed fixed point:** some $0$ and some $1$ remain, but no selected node would change.
> - **Cycle:** repeated configurations under synchronous deterministic updates.
> - **Stochastic consensus:** many finite voter-model realisations eventually reach consensus, but the winning opinion is random.

> [!theorem] Strict asynchronous majority reaches a fixed point
> On a **finite undirected graph**, use the deterministic strict-majority rule, with ties leaving the node unchanged. If nodes are selected fairly (e.g. independently and uniformly), the process reaches a fixed point **almost surely**, possibly a mixed one.

> [!proof]- Disagreeing-edge potential
> Let $H$ be the number of edges joining nodes in opposite states. A node flips only when it has **more disagreeing than agreeing neighbours**. If these numbers are $a>b$, then after the flip $H$ changes by $b-a<0$. Thus every actual flip **strictly decreases a non-negative integer**. There are only finitely many flips. Fair random selection eventually updates any remaining unstable node, so the chain settles into a fixed point. This reasoning does **not** apply unchanged to synchronous updates, since many flips occur together.
## 4. Mean-field idea (optional bridge to Week 12)

> [!derivation]- Degree-class closure
> Let $\rho_z(t)$ be the fraction of degree-$z$ nodes in state $1$ and $P(z)$ the degree distribution. Under an **uncorrelated, independent-neighbour approximation**, the probability that a neighbour is active is $$\omega(t)=\frac{\sum_z zP(z)\rho_z(t)}{\langle z\rangle}.$$
> A degree-$z$ node then sees $m$ active neighbours with approximate probability $B_{z,m}(\omega)=\binom zm\omega^m(1-\omega)^{z-m}$. For continuous-time transition rates, $$\dot\rho_z=(1-\rho_z)\sum_mF_{z,m}B_{z,m}(\omega)-\rho_z\sum_mR_{z,m}B_{z,m}(\omega).$$
> This **closure assumption**, not an exact network identity, is the reason the full $2^N$-state dynamics becomes a few equations.

> [!exam] Remember
> To describe a dynamical network model completely, state its **states, local transition rule, time convention, update order and measured observable**. For majority dynamics, *fixed $\rho$* does not mean *fixed configuration*.

> [!selftest]- Check your understanding
> 1. Why can one random asynchronous sweep leave some nodes unselected? — Sampling is with replacement.
> 2. Is a majority-rule mixed fixed point possible? — Yes; each node may agree with a local majority without global consensus.
> 3. What quantity decreases on each strict-majority asynchronous flip? — The number of disagreeing edges.

---
Related: [[Threshold model and cascades]] · [[SI and SIS models]] · [[SIR model and epidemic threshold]] · [[Evolutionary games on networks]]
