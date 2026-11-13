---
tags: [data5441, ch10, dynamics]
aliases: [Site percolation, Bond percolation, Percolation threshold, Bethe lattice]
---
# Percolation on lattices

> [!abstract] Summary
> **Percolation** asks whether randomly available sites or links can form a connected path across a system. Below a critical occupation probability $p_c$, only finite clusters occur in the infinite system; above it, an infinite cluster can occur. The **tree calculation** $p_c=1/(k-1)$ motivates the network-robustness criterion in [[Percolation and robustness]].
> Chapter: [[Ch10 Resilience and percolation]] · **Week 10**, lecture pp. 128–136; Tutorial 10 §1.

## 1. The percolation question

> [!definition] Site and bond percolation
> Start with a fixed lattice/graph. Independently retain each **site** (node) or **bond** (edge) with probability $p$; remove it with probability $q=1-p$.
> - **Bond percolation:** all nodes remain, but only occupied edges can be traversed.
> - **Site percolation:** occupied nodes remain together with edges connecting occupied neighbours.
> A **cluster** is a connected component of the retained network. The geometry matters: a square lattice with four neighbours is different from one with eight.

> [!definition] Critical occupation and observables
> In an infinite lattice, $p_c$ marks the onset of an **infinite connected cluster**. The probability that a designated node belongs to one is an order parameter $\theta(p)$, with $\theta(p)=0$ below $p_c$.
> In finite simulations, there is no true singularity. Measure the **largest-cluster fraction** $S_N(p)=N_1(p)/N$ or the **probability of crossing** a box. Increasing $N$ sharpens the crossover.

![[Assets/w10-site-percolation.png|760]]

> [!remark] How to read the figure
> The three panels use the **same random site marks** and increase $p$, so clusters can only merge or grow. The dramatic increase of the largest cluster near $p\simeq0.59$ is a *finite-size illustration*, not a calculation of $p_c$ from one picture.

## 2. One-dimensional and tree examples

> [!example] One-dimensional line
> An infinite occupied path requires *every* bond along that path to survive. For any $p<1$, the probability that the first $n$ bonds all survive is $p^n\to0$. Thus $\boxed{p_c=1}$ (for either bonds or sites in one dimension).

> [!theorem] Bond percolation on a $k$-regular tree
> Every reached vertex has $k-1$ **onward** edges (excluding the arrival edge). A positive probability of an infinite occupied branch appears precisely when
> $$\boxed{p(k-1)>1\quad\Longleftrightarrow\quad p>p_c=\frac1{k-1}.}$$
> In particular, a degree-$3$ Bethe lattice has $p_c=1/2$.

> [!derivation]- Two equivalent derivations
> **Branching:** each reached node has $\operatorname{Bin}(k-1,p)$ occupied onward links, giving mean offspring $p(k-1)$. The exploration survives with positive probability when this exceeds $1$.
>
> **Self-consistency:** let $u$ be the probability that following a *specified edge* fails to reach an infinite cluster. Either the edge is closed, or it is open and all $k-1$ outward branches fail:
> $$u=1-p+pu^{k-1}.$$
> The solution $u=1$ always exists; a second solution $u<1$ appears when the slope of the right-hand side at $u=1$ exceeds $1$, namely $p(k-1)>1$. For $k=3$, the non-trivial root is $u=(1-p)/p$.
>
> **Distinguish the probabilities:** $1-u$ is the chance a *particular outward direction* connects to infinity. The chance that a vertex belongs to an infinite occupied cluster is $1-u^k$ (bond model).

## 3. Geometry changes the threshold

| Infinite lattice | Site $p_c$ | Bond $p_c$ |
|---|---:|---:|
| 1D line | $1$ | $1$ |
| Square, 4 neighbours | $\approx0.5927$ | $1/2$ |
| Triangular | $1/2$ | $2\sin(\pi/18)\approx0.3473$ |
| $k$-regular tree, $k\ge3$ | $1/(k-1)$ | $1/(k-1)$ |

> [!example] Tutorial 10 — add diagonal neighbours
> An **eight-neighbour square lattice** allows extra paths, so its site threshold is **lower** than in the four-neighbour model (about $0.407$ rather than $0.593$). In Tutorial 10 the threshold is estimated from crossing probabilities, comparing multiple lattice sizes. Adding edges cannot make an existing crossing path disappear.

> [!algorithm] Finite-size site-percolation experiment
> 1. Fix an $M\times M$ lattice and sample one independent $U_i\sim\operatorname{Uniform}(0,1)$ per node.
> 2. For each $p$, retain the sites with $U_i<p$; connect occupied lattice neighbours.
> 3. Identify components and measure $N_1/M^2$ or whether any component crosses the box.
> 4. Repeat independently, average the observables, and compare larger $M$ values.
>
> Reusing the same marks across $p$ gives **nested realisations** and a clearer plot; it does not replace independent repetitions for error bars.

> [!remark] Zero–one law (conceptual)
> For independent percolation on an infinite lattice, the event **“there exists at least one infinite cluster somewhere”** has probability $0$ or $1$. This is *not* the probability that a specified node lies in an infinite cluster, which can be strictly between $0$ and $1$.

> [!exam] Remember
> 1. **Occupied fraction:** $p=1-q$; higher $p$ means more connectivity.
> 2. **1D line:** $p_c=1$; **degree-$3$ tree:** $p_c=1/2$.
> 3. **Tree calculation:** subtract the edge used to arrive, giving $k-1$ new possibilities.
> 4. **Lattices versus random graphs:** geometry changes the threshold, while the branching idea transfers to random networks.

> [!selftest]- Check your understanding
> 1. Why does bond percolation on a $5$-regular tree have $p_c=1/4$? — Each reached node has four onward edges.
> 2. Does a finite lattice literally undergo a discontinuous transition? — No; use finite-size crossing probabilities or largest-cluster statistics.
> 3. Why can adding diagonals only decrease (or preserve) $p_c$? — Every previously available occupied path is still possible.

---
Related: [[Percolation and robustness]] · [[Configuration model]] · [[Erdos-Renyi graphs]]
