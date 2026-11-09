---
tags: [data5441, ch05, models]
aliases: [Watts–Strogatz, Small world, Milgram, Kleinberg]
---
---
# Small-world networks

> [!abstract] Core idea
> A **small-world network** combines three features: **sparsity**, **short paths**, and **high clustering**. The Watts–Strogatz (WS) model explains how a small proportion of random *long-range shortcuts* can greatly shorten paths in a regular lattice without destroying its local triangles.
>
> **Key formulas:** $L=NQ$, $\langle z\rangle=2Q$, $C(0)=\dfrac{3(Q-1)}{2(2Q-1)}$, and $C(p)\approx C(0)(1-p)^3$.
>
> Course: Week 5, [[Ch05 Mechanistic models]].

## 1. What makes a network small-world?

> [!definition] Small-world conditions (DATA5441)
> For a sequence of graphs with $N\to\infty$, we look for:
> 1. **Sparsity:** $\langle z\rangle=O(1)$ (equivalently $L=O(N)$).
> 2. **Short distances:** typical shortest-path length $\ell\sim\log N$.
> 3. **High clustering:** $C\to C_*>0$, rather than vanishing as $N$ grows.
>
> Here $C$ denotes the clustering coefficient (transitivity or average local clustering as appropriate). For the initial regular ring, these coincide.

Why is this remarkable? A **regular ring** is highly clustered but has long paths, while a **sparse Erdős–Rényi graph** has short paths (within its giant component) but clustering $C\sim\langle z\rangle/N\to0$. Small-world networks have *both* desirable features.

| Network | Typical distances | Clustering |
|---|---|---|
| Regular ring ($Q$ fixed) | $\ell=\Theta(N)$ | $C=\Theta(1)$ for $Q\ge2$ |
| Sparse ER (supercritical) | $\ell=\Theta(\log N)$ in the giant component | $C=O(N^{-1})$ |
| WS, fixed $0<p<1$ and $Q\ge2$ | $\ell=O(\log N)$ | $C\approx C(0)(1-p)^3>0$ |

## 2. Watts–Strogatz construction

Start with $N$ vertices on a ring. Join each vertex to the $Q$ nearest neighbours **on each side**, where $Q\ge2$ is fixed. Hence
$$z_i=2Q,\qquad L=\frac{N(2Q)}2=NQ,\qquad \langle z\rangle=2Q.$$
Independently select each of the $L$ original edges for **rewiring** with probability $p\in[0,1]$. Move one endpoint to another randomly chosen vertex (avoiding self-loops and duplicate edges).

- $p=0$: the regular ring; local triangles and long distances.
- Small $p>0$: most local edges survive, while a few rewired edges form shortcuts.
- $p=1$: a random-like network with low clustering; **not exactly** an Erdős–Rényi graph.

The process **preserves $N$ and $L$**, hence sparsity, but *not each node's degree*.

![[Assets/small-world-shortcut.png|750]]
*The red edge takes the marked pair from six steps apart to one step. The green triangle survives. One shortcut can improve paths for many node pairs while leaving most local triangles untouched.*

## 3. Clustering in the original ring ($p=0$)

> [!proposition] Ring clustering
> Provided $N>3Q$, every node has the same clustering coefficient:
> $$C(0)=\frac{3(Q-1)}{2(2Q-1)}.$$
> As $Q\to\infty$ (with $N>3Q$), this approaches $3/4$.

> [!proof]- Why exactly $\tfrac32Q(Q-1)$ triangles per node?
> Fix a node $i$. Its $2Q$ neighbours form $\binom{2Q}{2}=Q(2Q-1)$ potential pairs. Every **edge between two neighbours of $i$** completes exactly one triangle through $i$.
>
> - **Both neighbours on the right:** all $Q$ form a clique, so there are $\binom Q2$ pairs.
> - **Both on the left:** another $\binom Q2$ pairs.
> - **One on each side:** offsets $-a$ and $+b$ are connected precisely when $a+b\le Q$; hence $\sum_{a=1}^{Q-1}(Q-a)=\binom Q2$ pairs.
>
> Therefore $T_i=3\binom Q2=\tfrac32Q(Q-1)$ triangles contain $i$. Dividing by all possible neighbour pairs gives
> $$C_i=\frac{T_i}{\binom{2Q}{2}}=\frac{3Q(Q-1)/2}{Q(2Q-1)}=\frac{3(Q-1)}{2(2Q-1)}.\qquad\square$$

**Distances before rewiring.** Every step moves at most $Q$ ring positions, so the distance between vertices separated by $s\le\lfloor N/2\rfloor$ ring positions is $\lceil s/Q\rceil$. Consequently,

$$\boxed{D(0)=\left\lceil\frac{\lfloor N/2\rfloor}{Q}\right\rceil},\qquad \ell(0)=\Theta(N/Q).$$

For fixed $Q$, these distances grow *linearly*, not logarithmically: the initial ring is **not** small-world.

## 4. Clustering after rewiring ($p >0$)

Each of the three edges of an *original triangle* remains unrewired with probability $1-p$. As the three selections are independent,
$$\Pr(\text{original triangle survives unchanged})=(1-p)^3.$$
Thus $\mathbb E[T_{\mathrm{original,\ surviving}}]=T(0)(1-p)^3$; neglecting triangles created by new edges and changes to the connected-triple denominator gives the standard approximation:

> [!proposition] WS clustering law (approximation)
> $$C(p)\approx C(0)(1-p)^3.$$
> When $p\ll1$, the binomial expansion yields $C(p)\approx C(0)(1-3p)$.
## 5. Why paths become short before clustering disappears

The number $S$ of original edges selected for rewiring is $\operatorname{Binomial}(NQ,p)$, so
$$\boxed{\mathbb E[S]=pNQ},\qquad \Pr(S\ge1)=1-(1-p)^{NQ}.$$

The characteristic scale for the *first* rewired edges is therefore $p\asymp 1/(NQ)$, which can be very small for large $N$. Rewired edges can join widely separated regions, bypassing long sections of the ring. Meanwhile, for $p\ll1$ the majority of original triangles survive.

![[Assets/small-world-curves.png|750]]

*Illustrative finite-$N$ simulation. The normalised average path length (orange) falls much sooner than clustering (green). The dashed line is the analytical clustering approximation.*

> [!remark] The small-world window — an important distinction
> At fixed large $N$, there is typically an intermediate regime with **many shortcuts** but **most clustering retained**; heuristically $1/(NQ)\ll p\ll1$ describes this crossover.
>
> **However:** $pNQ\gg1$ by itself does *not* prove $\ell=O(\log N)$ if $p=p_N\to0$ as $N\to\infty$. A clean asymptotic example is to keep a **small constant** $0<p<1$ and $Q\ge2$ as $N$ grows: clustering remains positive, and typical distances grow logarithmically.

## 6. Extension: Kleinberg and navigability

The WS model concerns whether **short paths exist**. Kleinberg asks whether a traveller who knows only their current neighbours and the target's location can **find** them.

On a $d$-dimensional lattice, suppose a long-range contact at lattice distance $r$ is chosen with weight proportional to $r^{-\alpha}$. Then **greedy decentralised routing** is polylogarithmically efficient only when $\alpha=d$. In two dimensions, $\alpha=2$ gives expected greedy routing time $O((\log N)^2)$, whereas other fixed exponents do not give polylogarithmic decentralised delivery times.

> [!tip] Distinction to remember
> **Small-world:** short paths exist. **Navigable small-world:** a local routing rule can efficiently find them.

## 7. Exam checklist

> [!exam] Testing whether a model is small-world (Trial Exam 1, Q7e)
> For uniformly sampled graphs with $L=2N$:
> - **Sparse?** Yes: $\langle z\rangle=2L/N=4$.
> - **Short paths?** Yes: typical distances in the giant component are $O(\log N)$.
> - **High clustering?** No: $C\sim 4/N\to0$.
>
> **Conclusion:** this random-graph model is **not small-world** under the course definition. The basic sparse ER and BA models both lack non-vanishing clustering in the large-$N$ limit.

> [!question]- Self-test
> 1. **Which three properties define a small-world sequence?** Bounded mean degree, logarithmic typical distances, non-vanishing clustering.
> 2. **Why is $L=NQ$?** Each of $N$ vertices has degree $2Q$ and each undirected edge is counted twice.
> 3. **Why the factor $(1-p)^3$?** Each of the three original edges of a triangle must escape independent rewiring.
> 4. **What is $C(0)$ when $Q=2$?** $1/2$.
> 5. **Does $pNQ\gg1$ automatically imply logarithmic distances for $p=p_N\to0$?** No; it signals many rewired edges, not the full asymptotic distance scaling.
> 6. **Why can distances fall before clustering?** A shortcut affects many shortest paths; only triangles involving rewired local edges are directly disrupted.

> [!code]- NetworkX: minimal WS experiment
> ```python
> import networkx as nx
>
> G = nx.watts_strogatz_graph(n=N, k=2*Q, p=p, seed=13)
> C = nx.transitivity(G)
> ell = nx.average_shortest_path_length(G)  # requires a connected graph
> ```

---
Related: [[Clustering]] · [[Paths and components]] · [[Erdos-Renyi graphs]] · [[Preferential attachment]]