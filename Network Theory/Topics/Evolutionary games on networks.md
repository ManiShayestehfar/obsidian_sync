---
tags: [data5441, ch12, dynamics]
aliases: [Game theory, Prisoner's dilemma, Nash equilibrium, Cooperation on networks]
---
# Evolutionary games on networks

> [!abstract] Summary
> A **game** specifies players' actions and payoffs. In the prisoner's dilemma, individuals gain by defecting even though mutual cooperation is better collectively. Put players on a **network**, sum payoffs over neighbours and allow imitation of successful neighbours: cooperation can then survive, particularly around **cooperative hubs** and densely connected groups. These are model-dependent tendencies, not guarantees.
> Chapter: [[Ch12 Epidemics and games on networks]] · **Week 12**, lecture pp. 160–167.

## 1. Payoff matrices and two kinds of optimum

> [!definition] A two-player game
> Each player chooses an action $e\in\mathcal Q$. The payoff matrix $M_{e_i,e_j}$ gives the **row player's payoff** for actions $e_i$ (row) and $e_j$ (column). The other player has its corresponding payoff. A **best response** maximises one player's payoff while holding the other's action fixed.
> - **Nash equilibrium:** neither player can **strictly improve** their payoff by changing action alone.
> - **Collective optimum:** the pair of actions maximising the **sum** of their payoffs.
>
> A Nash equilibrium need **not** be collectively optimal.

> [!example] Classical prisoner's dilemma (lecture)
> With actions $C$ (cooperate), $D$ (defect), take the following *row-player payoffs* (negative years in prison):
> $$M=\begin{array}{c|cc} & C&D\\\hline C&-2&-10\\D&0&-5\end{array}.$$
> If the other cooperates, defecting gives $0>-2$; if the other defects, defecting gives $-5>-10$. Thus **D is strictly dominant**, so $(D,D)$ is the **unique Nash equilibrium**. Yet $(C,C)$ yields total payoff $-4$, better than $-10$ at $(D,D)$.

> [!remark] What can change the outcome?
> Regulation changes payoffs; repeating games adds memory; communication changes information. **Network structure** can also change which strategies accumulate high payoffs and therefore get copied.

## 2. The weak prisoner's dilemma used in network simulations

> [!definition] Weak prisoner's dilemma
> The lecture also uses the simplified payoff matrix
> $$\boxed{M=\begin{array}{c|cc}&C&D\\\hline C&1&0\\D&b&0\end{array},\qquad 1<b<2.}$$
> Here $b$ is the **temptation to defect**: against C, D earns $b>1$; against D, both actions earn $0$. Therefore D is **weakly dominant** (not strictly, because the payoffs tie against D). Mutual cooperation gives the highest **total** payoff when $b<2$.

## 3. Evolution on a fixed network

> [!definition] Payoff accumulated from neighbours
> Give each node $i$ a strategy $e_i\in\{C,D\}$. In each round every adjacent pair plays the game; node $i$ receives
> $$\boxed{S_i=\sum_{j=1}^N A_{ij}M_{e_i,e_j}.}$$
> This is the **sum** of payoffs from all its edges, not the average. Hence a high-degree node can achieve a large score simply because it plays more games.

> [!algorithm] Network evolutionary-game simulation (lecture rule)
> 1. **Initialise:** assign C or D to each node (often at random).
> 2. **Play:** on every edge, evaluate both players' payoffs using the matrix.
> 3. **Aggregate:** calculate the total score $S_i$ for each node.
> 4. **Imitate:** each node $i$ chooses one random neighbour $j$ and, if $S_j>S_i$, adopts $j$'s strategy. Otherwise it keeps its own. Specify whether all strategies change **simultaneously** after score calculation or by a chosen asynchronous convention.
> 5. Repeat and measure the cooperator fraction $\rho_C(t)=N^{-1}\sum_i\mathbf1\{e_i=C\}$.
>
> This is a **dynamical process on a fixed graph**; the links do not change. The outcome can vary with initial states, update details, $b$ and topology.

## 4. How cooperative hubs can help

![[Assets/w12-game-hubs.png|740]]

> [!example] Two-hub explanation (lecture toy model)
> Consider a cooperative hub $x$ joined to five C leaves and one defecting hub $y$. Let $y$ be joined to five D leaves and to $x$. Under the weak prisoner's dilemma:
> $$S_x=5\cdot1+0=5,\qquad S_y=b+5\cdot0=b.$$
> At $b=1.5$, $S_x>S_y$, so **if** $y$ samples $x$ as its neighbour, it imitates cooperation. By contrast, in an **initially mixed** neighbourhood with about half the neighbours cooperating, a D hub can initially outscore a C hub because $b>1$. The lecture's narrative is: **C initially struggles, but cooperative neighbourhoods can organise and then outperform D hubs**.

> [!remark] Why degree heterogeneity matters — and its limitation
> Hubs influence many neighbours, and accumulated scores favour well-connected successful players. An established cooperative hub can create a reinforcing region of cooperation. This helps explain why scale-free networks may sustain cooperation better than homogeneous networks in the lecture's comparison. It does **not** imply that every BA graph or every value of $b$ achieves full cooperation; the result depends on the precise payoff and update rule.

## 5. Beyond static networks

> [!definition] Co-evolution
> The models above keep the adjacency matrix $A$ fixed and evolve only strategies. **Co-evolutionary** models allow strategies **and** connections to change, for instance by breaking links with defectors or forming links with cooperators. This is an extension, not part of the basic simulation.

> [!exam] Remember
> - **Nash:** no player benefits from changing **alone**; **collective optimum:** maximum **sum**.
> - **Lecture game:** $S_i=\sum_jA_{ij}M_{e_i,e_j}$, then imitation of a better-scoring neighbour.
> - **Weak** prisoner's dilemma has ties against D; don't call D **strictly** dominant.
> - **Hubs and cooperative clusters** can help, but are not a universal proof of cooperation.

> [!selftest]- Check your understanding
> 1. Why is $(D,D)$ a Nash equilibrium in the classical prisoner’s dilemma? — D is each player's strict best response to D.
> 2. If a C node has $4$ C neighbours and $3$ D neighbours in the weak game, what is its payoff? — $4$.
> 3. Why can the outcome depend on network topology even with identical payoffs? — The topology determines interaction partners, cumulative scores and imitation opportunities.

---
Related: [[Binary-state dynamics]] · [[Power laws]] · [[Community detection]]
