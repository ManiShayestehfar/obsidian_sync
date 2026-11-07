---
tags: [data5441, ch05, models]
aliases: [Watts–Strogatz, Small world, Milgram, Kleinberg]
---
# Small-world networks

> [!abstract] Summary
> Real networks are sparse, have short distances like random graphs, and have high clustering like lattices. The Watts–Strogatz model shows that a few random shortcuts in a lattice shrink distances while clustering survives.
> Chapter: [[Ch05 Mechanistic models]]

> [!definition] Small-world network (course definition)
> A network sequence is **small-world** if it satisfies all three conditions:
> 1. **sparse:** $\langle z\rangle$ bounded as $N\to\infty$;
> 2. **short distances:** $\ell\sim\log N$;
> 3. **high clustering:** $C$ does not tend to $0$ (comparable to a lattice, much larger than ER at the same $\langle z\rangle$).
>
> Motivation: Milgram's letter-passing experiment found about six steps between strangers.

> [!definition] Watts–Strogatz (WS) model
> Place $N$ nodes on a ring and link each to its $Q$ nearest neighbours on each side, so $z_i=2Q$ and $L=NQ$. Then rewire each link independently with probability $p$, moving one endpoint to a uniformly random node while avoiding loops and multi-links.
> Rewiring preserves $L$ but not the individual degrees.
> - $p=0$: lattice (high $C$, $\ell\propto N$).
> - $p=1$: random graph (low $C$, $\ell\sim\log N$).

> [!theorem] Ring-lattice clustering and diameter
> For $N>3Q$,
> $$C(0)=\frac{3(Q-1)}{2(2Q-1)}\ \xrightarrow{Q\to\infty}\ \frac34,\qquad D=\Big\lceil\frac{\lfloor N/2\rfloor}{Q}\Big\rceil .$$

> [!proof]-
> A node has $2Q$ neighbours, giving $\binom{2Q}2=Q(2Q-1)$ neighbour pairs.
> - Each side is a clique of $Q$ neighbours: $2\binom Q2=Q(Q-1)$ links.
> - The neighbours at offsets $-a$ and $+b$ are linked iff $a+b\le Q$. For each $a\in\{1,\dots,Q-1\}$ there are $Q-a$ admissible values of $b$, giving $\sum_{a=1}^{Q-1}(Q-a)=Q(Q-1)/2$ links.
>
> In total there are $\tfrac32Q(Q-1)$ links among the neighbours, so $C(0)=\dfrac{\tfrac32Q(Q-1)}{Q(2Q-1)}$.
> For the diameter, each step advances at most $Q$ positions, and the farthest node is $\lfloor N/2\rfloor$ positions away. $\square$

> [!proposition] Clustering after rewiring (approximation)
> $$C(p)\approx C(0)(1-p)^3 .$$
> A triangle survives only if none of its $3$ links is rewired. This ignores new triangles created by rewiring.

> [!remark] The small-world regime
> $\ell(p)$ drops sharply already at small $p$, because a few shortcuts connect distant parts of the ring. $C(p)$ stays near $C(0)$ until $p$ is much larger. There is a wide window, roughly $1/(NQ)\ll p\ll1$, with both small $\ell$ and large $C$.

![[small-world-rewiring.png|650]]

> [!remark] Kleinberg: finding the short paths
> Short paths **existing** is different from them being **findable** by local (greedy) routing. In a 2D lattice with extra long-range links whose probability decays as $r^{-\alpha}$ in lattice distance $r$, greedy routing is efficient ($O(\log^2N)$ steps) only at $\alpha=2$, i.e. $\alpha$ equal to the dimension.

> [!exam] Is a model small-world? (Trial Exam 1, Q7e)
> Take uniform random graphs with $L=2N$, i.e. $\beta=0$. Check the three conditions:
> - sparse: $\langle z\rangle=4$, yes;
> - short distances: $\ell\sim\log N$, yes;
> - high clustering: no, since $C\to0$.
>
> So the model is **not** small-world. Neither ER nor BA has high clustering in the sparse large-$N$ limit.

> [!code]- NetworkX (tutorial 5)
> ```python
> G = nx.watts_strogatz_graph(N, k=2*Q, p=p, seed=13)
> nx.transitivity(G); nx.average_shortest_path_length(G)
> ```

> [!selftest]- Self-test
> 1. What are the three small-world conditions? — Sparse, $\ell\sim\log N$, high $C$.
> 2. Why does $\ell$ fall faster than $C$ under rewiring? — A shortcut affects many paths but only a few triangles.

---
Related: [[Clustering]] · [[Paths and components]] · [[Erdos-Renyi graphs]] · [[Preferential attachment]]
