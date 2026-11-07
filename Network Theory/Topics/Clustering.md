---
tags: [data5441, ch01, foundations]
aliases: [Clustering coefficient, Transitivity, Triangles]
---
# Clustering

> [!abstract] Summary
> Clustering measures triangle closure: are my neighbours also neighbours of each other? There are two graph-level versions, $C_{net}$ (transitivity) and $\langle C\rangle$ (mean local clustering), and they generally differ.
> Chapter: [[Ch01 Networks and high dimensions]]

> [!definition] Local clustering coefficient *(formula sheet)*
> Let $T_i$ be the number of triangles containing node $i$. Then
> $$C_i=\frac{T_i}{\binom{z_i}{2}}=\frac{2T_i}{z_i(z_i-1)}\quad(z_i\ge2),\qquad C_i=0\ \text{ if } z_i<2 .$$
> $C_i$ is the fraction of pairs of neighbours of $i$ that are linked.

> [!definition] Global clustering and average clustering *(formula sheet)*
> $$C_{net}=\frac{3T}{\sum_i\binom{z_i}{2}},\qquad \langle C\rangle=\frac1N\sum_{i=1}^N C_i ,$$
> where $T$ is the total number of triangles. $C_{net}$ is the fraction of closed **wedges** (connected triples). NetworkX: `nx.transitivity` gives $C_{net}$ and `nx.average_clustering` gives $\langle C\rangle$.

> [!theorem] Triangle counts from $A$
> For a simple undirected graph,
> $$T_i=\tfrac12(A^3)_{ii},\qquad T=\tfrac16\operatorname{tr}(A^3),\qquad C_{net}=\frac{\sum_i\binom{z_i}2C_i}{\sum_i\binom{z_i}2}.$$

> [!proof]-
> A closed walk of length $3$ in a loop-free simple graph is a triangle traversed in one of $2$ orientations. Fixing the start node $i$ gives $(A^3)_{ii}=2T_i$. Each triangle has $3$ possible start nodes, so $\operatorname{tr}A^3=6T$.
> For the last identity, $\sum_iT_i=3T$ and $T_i=\binom{z_i}{2}C_i$. Hence $C_{net}$ is the average of $C_i$ weighted by the wedge count $\binom{z_i}2$. $\square$
>
> **Consequence:** $C_{net}$ weights high-degree nodes more heavily than $\langle C\rangle$ does.

> [!example] Hub with two triangles
> Take a hub joined to $5$ leaves, then add two disjoint leaf–leaf links.
> - Degrees are $(5,2,2,2,2,1)$ and local coefficients are $(\tfrac15,1,1,1,1,0)$.
> - So $\langle C\rangle=7/10$.
> - There are $T=2$ triangles and $\sum_i\binom{z_i}2=10+4\cdot1=14$, so $C_{net}=6/14=3/7$.

![[clustering-definitions.png|650]]

> [!theorem] Clustering of ER graphs
> In $G(N,p)$, two neighbours of a node are linked independently with probability $p$. Hence $\mathbb E[C_i\mid z_i\ge2]=p$ and $C\approx p=\langle z\rangle/(N-1)$. For fixed $\langle z\rangle$ this tends to $0$ as $N\to\infty$.

> [!exam] How it is examined
> Short-answer items ask for $C_i$ of a named node read from a figure, for $\langle C\rangle$, or for comparisons. Examples: "is $C$ larger than for a random $8$-regular graph?" (larger, if there are dense groups), or comparisons between a real network and its fitted ER graph (see the caveat in [[Exam patterns]]). Count the links among the neighbours directly from the figure.

> [!remark] Lattice values (tutorial)
> In the 8-neighbour lattice, corner, edge and interior nodes have $C_i=1,\ 3/5,\ 3/7$ respectively. The 4-neighbour lattice has $C=0$.

> [!selftest]- Self-test
> 1. Why can $\langle C\rangle\ne C_{net}$? — $C_{net}$ is a wedge-weighted average of the $C_i$.
> 2. ER with $N=200$, $L=1000$: what is $C$? — $C\approx p=10/199\approx0.050$.
> 3. Is the clustering of a graph of dense groups larger than that of a random $z$-regular graph? — Larger: random regular graphs are locally tree-like.

---
Related: [[Paths and components]] · [[Erdos-Renyi graphs]] · [[Small-world networks]] · [[Maximum entropy and ERGMs]]
