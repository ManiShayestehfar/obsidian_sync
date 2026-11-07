---
tags: [data5441, ch12, dynamics]
aliases: [Game theory, Prisoner's dilemma, Nash equilibrium, Cooperation on networks]
---
# Evolutionary games on networks

> [!abstract] Summary
> In the prisoner's dilemma, defection is individually optimal although mutual cooperation is collectively optimal. When players sit on a network, play their neighbours and imitate better-scoring neighbours, cooperation can prevail. Degree heterogeneity (hubs) and cooperative communities help.
> Chapter: [[Ch12 Epidemics and games on networks]] · Lecture pp. 160–166

> [!definition] Two-player game
> A game between players $i$ and $j$ is defined by:
> 1. a set $\mathcal Q=\{e_1,\dots,e_{|\mathcal Q|}\}$ of actions;
> 2. a $|\mathcal Q|\times|\mathcal Q|$ payoff matrix $M_{e_ie_j}$, the payoff to the player choosing $e_i$ against $e_j$.

> [!definition] Individual and collective optimum; Nash equilibrium
> - **Individual optimal choice:** the action $e_i$ maximising $i$'s payoff $M_i$ with $e_j$ held fixed (a best response).
> - **Collective optimum:** $\max_{e_i,e_j}\{M_i+M_j\}$.
> - When the two coincide we have a "win–win" situation. The interesting case is when they differ.
> - A **Nash equilibrium** is a pair of actions in which each player's action is a best response to the other's, so no one gains by deviating alone.

> [!example] Prisoner's dilemma (lecture)
> $\mathcal Q=\{C,D\}$ (cooperate, defect). Payoffs are minus years in prison (rows: own action; columns: other's action):
> $$M=\begin{array}{c|cc}&C&D\\\hline C&-2&-10\\D&0&-5\end{array}$$
> - **Collective optimum:** $(C,C)$, with $M_i+M_j=-4$.
> - **Individual optimum:** $D$ regardless of $e_j$, since $0>-2$ and $-5>-10$.
>
> So $(D,D)$ is the Nash equilibrium, with total $-10$.
> The same structure models public goods (e.g. fishing), arms races and advertising competition.

> [!remark] How can cooperation be achieved?
> - Change the payoffs (regulation).
> - Play repeatedly, with memory of past games.
> - Allow or increase communication.
> - **Network structure** (below).

> [!definition] Weak prisoner's dilemma (used in class and in the network model)
> $$M=\begin{array}{c|cc}&C&D\\\hline C&1&0\\D&b&0\end{array},\qquad b>1\ \text{(temptation)},\ \text{e.g. }b=1.5 .$$
> Defection is weakly dominant, while $(C,C)$ maximises the total for $b<2$.

> [!definition] Evolutionary game on a network
> - **Initialisation:** each node gets $C$ or $D$ at random.
> - **Each round** $t\to t+1$: a game is played on every link. The payoff of node $i$ is
> $$S_i=\sum_{j=1}^NA_{ij}M_{e_ie_j}.$$
> - **Action update:** each node $i$ picks a random neighbour $j$. If $S_j>S_i$, then $e_i\leftarrow e_j$ (imitate the more successful).
> - **Measure:** $\rho(t)=\frac1N\sum_i\delta(e_i=C)$. Cooperation prevails if $\lim_{t\to\infty}\rho(t)=1$; it survives if the limit is $>0$.

> [!remark] Observations
> - **Tutorial:** $\rho(t)$ first decays (defectors exploit cooperators) and then rises to $\rho=1$.
> - **Santos & Pacheco (PRL):** scale-free networks sustain cooperation over a wide range of temptation $b$ (prisoner's dilemma) and cost ratio $r$ (snowdrift). On regular networks cooperation collapses quickly.
>
> **Degree variability favours cooperation.**

> [!example] Why hubs help: two-hub toy model
> Take two linked hubs $x$ (playing $C$) and $y$ (playing $D$), each with $z$ neighbours, half $C$ and half $D$ at $t=0$.
> - **At $t=0$:** $S_x\approx\frac z2\cdot1+\frac z2\cdot0=\frac z2<S_y\approx\frac z2\cdot b$. The chance that $x$ switches to $D$ per round is $\approx1/z$ (it must pick $y$ among its $z$ neighbours), which is small for a hub.
> - **Intermediate times:** the hubs' leaves imitate their hub, because a hub's payoff exceeds a leaf's. $x$'s neighbourhood becomes all-$C$ and $y$'s all-$D$. Now $S_x\approx z\cdot1$, while $y$ gains only from its single cooperating neighbour $x$: $S_y\approx b$.
> - **Eventually:** since $z>b$, $y$ copies $x$, and cooperation spreads.
>
> **Remarks:** cooperation may prevail if cooperators form communities at intermediate times. Hubs (scale-free networks) and assortative communities facilitate this.

> [!remark] Beyond
> So far the states (strategies) evolve on a fixed network. **Co-evolution** also lets links be added or removed.

> [!selftest]- Self-test
> 1. Define Nash equilibrium and find it in the lecture's PD matrix. — $(D,D)$.
> 2. Write the payoff $S_i$ and the imitation rule.
> 3. Explain, with the two-hub argument, why hubs favour cooperation.

---
Related: [[Binary-state dynamics]] · [[Power laws]] · [[Community detection]]
