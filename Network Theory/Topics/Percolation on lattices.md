---
tags: [data5441, ch10, dynamics]
aliases: [Site percolation, Bond percolation, Percolation threshold, Bethe lattice]
---
# Percolation on lattices

> [!abstract] Summary
> Keep each site or bond independently with probability $p$. Above a critical $p_c$ a spanning or infinite cluster appears. The value of $p_c$ depends on the geometry. On a tree with branching factor $k-1$, $p_c=1/(k-1)$, the template for the random-graph results.
> Chapter: [[Ch10 Resilience and percolation]]

> [!definition] Site and bond percolation
> - **Bond:** each link is kept (occupied) independently with probability $p$.
> - **Site:** each node is kept with probability $p$, together with the links between kept nodes.
>
> Write $q=1-p$ for the failure (removal) probability.

> [!definition] Order parameter
> $\theta(p)=\lim_{N\to\infty}N_1/N$, where $N_1$ is the size of the largest cluster, normalised by the **original** $N$. The threshold is $p_c=\inf\{p:\theta(p)>0\}$. In a finite box, use the probability of a cluster crossing the box.

> [!theorem] Bond percolation on a regular tree (Bethe lattice)
> On an infinite tree where every node has degree $k$, so each reached node has $k-1$ onward branches,
> $$p_c=\frac1{k-1}.$$

> [!proof]-
> Exploring from a node, each occupied bond leads to a node with $k-1$ further bonds, each occupied with probability $p$. The number of new occupied branches has mean $p(k-1)$. A Galton–Watson process survives with positive probability iff its mean offspring is $>1$ (excluding degenerate cases). Hence $p_c(k-1)=1$. $\square$
> For the probability $u$ that a branch is finite, $u=1-p+pu^{k-1}$. For $k=3$ the non-trivial root is $u=(1-p)/p$ for $p>1/2$.

| Infinite lattice | Site $p_c$ | Bond $p_c$ |
|---|---|---|
| 1D line | $1$ | $1$ |
| Square (4 neighbours) | $\approx0.5927$ | $1/2$ |
| Triangular | $1/2$ | $2\sin(\pi/18)\approx0.3473$ |
| $k$-regular tree | $1/(k-1)$ | $1/(k-1)$ |

> [!remark] Tutorial 10 lessons
> - The 8-neighbour square lattice contains all 4-neighbour links, so its threshold is **lower**: the site $p_c\approx0.407$ was estimated from the 50% crossing point.
> - In finite systems the transition is smooth and shifts with system size.
> - Coupling all $p$ values to the same random numbers gives nested clusters.

![[tutorial-10-cell-06-plot-1.png|650]]

> [!theorem] Zero–one law (background)
> On an infinite connected locally finite graph, the existence of **some** infinite cluster is a tail event, so it has probability $0$ or $1$ (Kolmogorov). The probability that a **given** node is in an infinite cluster can lie strictly between $0$ and $1$.

> [!selftest]- Self-test
> 1. Bond $p_c$ of the $3$-regular tree? — $1/2$.
> 2. Why can adding diagonals not raise $p_c$? — More links can only create more connections.

---
Related: [[Percolation and robustness]] · [[Configuration model]] · [[Erdos-Renyi graphs]]
