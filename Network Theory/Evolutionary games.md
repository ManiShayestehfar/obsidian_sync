---
tags: [dynamics]
---

# Evolutionary games

Network games couple strategic choices through graph interactions. The payoff matrix alone is not a dynamical model: strategy-update rules and timing must also be specified.

> [!definition] Payoffs, best responses and Nash equilibrium
> In a symmetric two-player game, $M_{ab}$ is the payoff to the row player choosing $a$ against $b$; the other player receives $M_{ba}$. A best response maximises one player’s payoff for the opponent’s fixed action. A **Nash equilibrium** is a strategy profile in which every player is best-responding, so no unilateral deviation improves their payoff. A single best response is not itself an equilibrium.

A strict prisoner’s dilemma uses $T>R>P>S$ for temptation, mutual-cooperation reward, mutual-defection payoff and sucker’s payoff. Defection strictly dominates cooperation. The social comparison also depends on total payoffs; $2R>T+S$ makes mutual cooperation preferable in total to an asymmetric outcome.

The student example is instead a **weak** prisoner’s-dilemma parametrisation:

| Row payoff $M$ | Opponent C | Opponent D |
| --- | ---: | ---: |
| C | $1$ | $0$ |
| D | $b$ | $0$ |

For $1<b<2$, mutual cooperation has total payoff $2>b$, but defection weakly dominates. Mutual defection is a Nash equilibrium; weak ties mean it need not be the only pure equilibrium. The source’s total payoff “$-4$” does not match this matrix.

> [!definition] Network imitation process
> Give each vertex a strategy $a_i\in\{C,D\}$. For accumulated payoffs set
> $$S_i=\sum_jA_{ij}M_{a_i a_j}.$$
> Choose a vertex and one neighbour; copy the neighbour’s strategy if its payoff is strictly larger. Specify asynchronous versus synchronous updates, tie handling, and whether payoffs are summed or degree-normalised. Measure cooperation by $\rho_C=N^{-1}\sum_i\mathbf1\{a_i=C\}$.

> [!example] A conditional hub argument
> In the weak payoff matrix, a cooperating degree-$k$ vertex with $k-1$ cooperating neighbours earns $k-1$. A defector with only one cooperating neighbour earns $b$. The cooperator has higher payoff if $k-1>b$. This local comparison suggests how a cooperative neighbourhood can help; it does not prove that all networks or all initial conditions evolve to cooperation.

> [!code] One asynchronous imitation update
> ```python
> import networkx as nx
> import numpy as np
>
> def imitation_step(g, strategies, payoff, rng):
>     state = dict(strategies)
>     vertices = list(g)
>     if not vertices:
>         return state
>     u = vertices[rng.integers(len(vertices))]
>     neighbours = list(g.neighbors(u))
>     if not neighbours:
>         return state
>     v = neighbours[rng.integers(len(neighbours))]
>     def score(w):
>         return sum(payoff[state[w], state[z]] for z in g.neighbors(w))
>     if score(v) > score(u):
>         state[u] = state[v]
>     return state
>
> G = nx.cycle_graph(10)
> rng = np.random.default_rng(5441)
> M = np.array([[1.0, 0.0], [1.5, 0.0]])  # 0=C, 1=D
> state = {v: int(rng.integers(2)) for v in G}
> for _ in range(100):
>     state = imitation_step(G, state, M, rng)
> print(np.mean([s == 0 for s in state.values()]))
> ```

Degree heterogeneity affects accumulated payoffs directly; dividing by degree changes the model. Cooperation claims therefore need the payoff, update rule, topology and initialisation. This is a strategic variant of [[Binary dynamics and cascades]], not a universal consequence of hubs or communities.

> [!reference]- Sources
> Jenny’s notes Week 12. Definitions, matrix arithmetic and update rules have been corrected and made explicit; the local hub comparison is conditional reasoning, not a general theorem. Newman Chapter 17 supplies dynamical-systems context rather than a derivation of this game. Current-course lecture/tutorial coverage after Week 7 was not supplied.
