---
tags: [data5441, ch12, dynamics]
aliases: [Game theory, Prisoner's dilemma, Nash equilibrium, Cooperation on networks]
---
# Evolutionary games on networks

> [!abstract] Summary
> A **game** specifies available actions and their payoffs. The **prisoner's dilemma** illustrates the conflict between the individually optimal choice (defection) and the collective optimum (cooperation). On a network, each node plays its neighbours and may imitate a better-scoring neighbour. The lecture uses this model to explain how **hubs and cooperative neighbourhoods** can support cooperation.
> Chapter: [[Ch12 Epidemics and games on networks]] · **2026 lecture pp. 160–167** · Jeny pp. 57–59.

## 1. Actions, payoffs and optimality

> [!definition] Two-player game (lecture)
> A game between players $i$ and $j$ has:
> 1. a set $\mathcal Q=\{e_1,\ldots,e_{|\mathcal Q|}\}$ of possible actions (strategies);
> 2. a payoff matrix $M_{e_i,e_j}$, giving the **payoff to the player choosing the row action $e_i$** against an opponent choosing column action $e_j$.

> [!definition] Individual versus collective optimum
> - **Individually optimal choice / best response:** maximise your own payoff while the opponent's choice is held fixed.
> - **Collective optimum:** maximise the **sum** of both players' payoffs.
> - A **Nash equilibrium** is an action pair in which neither player benefits from unilaterally switching strategy.
>
> When the best responses produce the collective optimum, the lecture calls this a **win–win** situation. When not, there is a conflict between individual and collective incentives.

## 2. Prisoner's dilemma

> [!example] Classical prisoner’s dilemma (lecture p. 160)
> Let $C$ mean **cooperate** and $D$ mean **defect**. Taking payoffs to be **minus years in prison**, the row player's matrix is
> $$M=\begin{array}{c|cc}&C&D\\\hline C&-2&-10\\D&0&-5\end{array}.$$
> - Against **C**, defecting yields $0>-2$.
> - Against **D**, defecting yields $-5>-10$.
> Therefore D is each player's **dominant choice** and $(D,D)$ is the Nash equilibrium, with total payoff $-10$.
> - But $(C,C)$ gives total payoff $-4$, the **collective optimum**.

> [!remark] Lecture's examples and possible changes
> Similar tensions arise for **public goods (fishing)**, **arms races** and **advertising competition**. The lecture lists changing payoffs through regulation, **repeated** encounters and increased **communication** as possible mechanisms for cooperation. It then asks whether **network structure itself** can help.

## 3. Weak prisoner's dilemma used for the network model

> [!definition] Lecture's simplified payoff matrix (p. 162)
> $$\boxed{M=\begin{array}{c|cc}&C&D\\\hline C&1&0\\D&b&0\end{array},\qquad b>1,\quad\text{example: }b=1.5.}$$
> Here $b$ is the **temptation to defect**. Against a cooperator, a defector receives $b>1$, while a cooperator receives $1$. Against a defector, both earn $0$ in this simplified model.
>
> At the lecture's $b=1.5$, $(C,C)$ has total payoff $2$, whereas $(D,C)$ has total payoff $1.5$: mutual cooperation is collectively better, although exploiting a cooperator is individually tempting.

## 4. Playing the game on a fixed network

> [!definition] Network payoff (lecture)
> Each node $i$ adopts an action $e_i\in\{C,D\}$. The game is played on **each edge** in a round, and node $i$ accumulates the **sum**
> $$\boxed{S_i=\sum_{j=1}^{N}A_{ij}M_{e_i,e_j}.}$$
> The total payoff generally depends on degree because a high-degree node plays more games. **Do not divide by the degree:** the lecture uses an accumulated score, not an average payoff.

> [!algorithm] Evolutionary game on a network (lecture pp. 163–164)
> 1. **Initialise:** assign each node C or D, typically at random.
> 2. **Play:** each connected pair plays the game; compute $S_i$ for all nodes.
> 3. **Choose a neighbour:** each node $i$ chooses a random neighbour $j$.
> 4. **Imitate:** if $S_j>S_i$, node $i$ adopts $j$'s strategy; otherwise it keeps its own.
> 5. **Repeat** rounds; measure the fraction of cooperators,
> $$\boxed{\rho_C(t)=\frac1N\sum_{i=1}^{N}\mathbf1\{e_i(t)=C\}.}$$
> Cooperation **prevails** when $\rho_C(t)\to1$. The lecture's rule is a successful-neighbour imitation rule, not a universal rule for all evolutionary games.

> [!remark] What the time evolution looks like (lecture p. 164)
> The lecture's example initially shows $\rho_C(t)$ **falling** (defectors exploit cooperators), then **rising** towards 1. The model outcome depends on the network and the selected game parameters; the plotted trajectory is an example, not a guarantee.

![[Assets/w12-lecture-cooperation-trajectory.png|660]]

![[Assets/w12-lecture-cooperation-comparison.png|660]]

> [!note] How to read the lecture's comparison
> The lecturer reproduces a study comparing **scale-free networks (red squares)** with **regular networks (black circles)** for two network sizes. The **left column** is the prisoner's dilemma (horizontal variable $b$); the **right column** is the snowdrift game (horizontal variable $r$, introduced in the figure but not mathematically developed in the lecture). Both illustrate that **degree variability can favour cooperation** in these models. These are simulation results, not a proof that all networks with hubs cooperate.

## 5. Why hubs can help: the lecture's two-hub explanation

![[Assets/w12-game-hubs.png|650]]

> [!example] Two interconnected hubs $x$ and $y$ (lecture pp. 165–166; Jeny pp. 58–59)
> Let $x$ be a **cooperator** (C) and $y$ a **defector** (D), with approximately equal degree $z$, and suppose they are linked.
>
> **Initially:** their neighbours are roughly half C and half D, giving
> $$S_x\approx\frac z2,\qquad S_y\approx b\frac z2.$$
> Since $b>1$, the defecting hub initially scores more. However, hub $x$ switches to D in the lecture's imitation step **only if it chooses $y$** (or another better-scoring D neighbour); if $y$ is its only relevant D rival, that chance is roughly $1/z$.
>
> **At an intermediate stage:** suppose $x$'s other $z-1$ neighbours are C, and $y$'s other $z-1$ neighbours are D. Then
> $$\boxed{S_x=z-1,\qquad S_y=b.}$$
> If $z-1>b$, the cooperative hub now has the higher payoff. When $y$ selects $x$, it imitates C; cooperation can spread from the cluster around $x$.
>
> **Main idea:** a group of cooperating neighbours can reinforce one another's payoffs. High-degree nodes can support this process, helping explain the lecture's scale-free versus regular-network comparison.

## 6. Beyond the fixed-network game

> [!remark] Co-evolution (brief closing remark, lecture p. 167)
> So far, **strategies evolve** while the network $A$ stays fixed. The lecture briefly mentions **co-evolution**: strategies and network connections may both change. No additional co-evolution algorithm is derived in the provided lecture notes.

> [!exam] Essential points
> - Distinguish **individual** and **collective** optima and calculate them from a payoff matrix.
> - For the lecture's classical game, $(D,D)$ is Nash, but $(C,C)$ is collectively best.
> - Know the weak game $M$ with temptation $b$.
> - Be able to compute $S_i=\sum_j A_{ij}M_{e_i,e_j}$ and apply the **successful-neighbour imitation** rule.
> - Explain the **two-hub payoff reversal** from $z/2$ versus $bz/2$ to $z-1$ versus $b$.

> [!selftest]- Quick checks
> 1. In the weak game, what does D earn from a C neighbour? — $b$.
> 2. A cooperator has 4 C neighbours and 3 D neighbours. What is its score? — $4$.
> 3. Why is using the *sum*, rather than the average, important? — Degree affects the total score and the success of hubs.
> 4. Is the toy model a proof that every scale-free network reaches full cooperation? — No; it explains the lecture's observed mechanism.

---
Related: [[Binary-state dynamics]] · [[Power laws]] · [[Community detection]]
