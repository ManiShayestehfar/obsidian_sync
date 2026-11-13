---
tags: [data5441, ch10, dynamics]
aliases: [Site percolation, Bond percolation, Percolation threshold, Bethe lattice]
---

# Percolation on lattices

> [!abstract] Summary
> **Percolation** studies whether randomly retained nodes or edges allow travel across a network or over arbitrarily large distances. The central result is a **critical occupation probability** $p_c$: below it extensive connections disappear, above it they are possible. Geometry controls $p_c$; an infinite $k$-regular tree gives the exact benchmark $p_c=1/(k-1)$.
>
> **Study order:** site/bond percolation → finite crossing experiments → 1D and 2D lattices → Bethe-lattice derivation → relation to random graphs.
>
> Chapter: [[Ch10 Resilience and percolation]] · **2026 lecture pp. 128–136** · **Tutorial 10 §§1.1–1.3**.

## 1. What is the percolation problem?

In a communication network, a signal needs a path of working links. In a porous material, water needs a connected path of pores. Both reduce to the same question: **does a retained network contain a sufficiently large connected cluster?**

> [!definition] Site and bond percolation
> Start with a fixed underlying graph $G_0=(V,E)$, usually a lattice.
> - **Bond percolation:** independently keep each edge with probability $p$; every original node stays.
> - **Site percolation:** independently keep each node with probability $p$ and retain edges only between surviving nodes.
>
> The **failure probability** is $q=1-p$. An *occupied/open* element is retained; a *vacant/closed* element is removed. A **cluster** is a connected component of the occupied network.

> [!definition] Three observables
> | Quantity | Question | Finite/infinite setting |
> |---|---|---|
> | $\pi_n(p)$ | Is there a path crossing a finite $n\times n$ box (e.g. top to bottom)? | Probability over random configurations |
> | $\theta(p)$ | Does a specified node belong to an infinite cluster? | Infinite lattice |
> | $K_1=N_1/N_0$ | What fraction of the **original** $N_0$ nodes lies in the largest retained cluster? | Finite simulation; see [[Percolation and robustness]] |
>
> In particular, $\pi_n$ is a *crossing probability*, whereas $\theta$ is a *root-membership probability*.

> [!definition] Percolation threshold
> For an infinite connected lattice, define $p_c=\inf\{p:\theta(p)>0\}$. Typically $\theta(p)=0$ for $p<p_c$ and $\theta(p)>0$ for $p>p_c$.
> For large square boxes of fixed aspect ratio, the crossing probability generally approaches $0$ below $p_c$ and $1$ above it; the finite-size transition is smooth. Do not infer the behaviour *at* $p=p_c$ from this statement.

## 2. Geometry determines the threshold

### 2.1 One-dimensional lattice

For an infinite line, $z=2$: a path from the origin to arbitrarily great distance needs **every edge along that path to be open**. The probability that the first $n$ specified edges survive is $p^n$.

For $p<1$, $p^n\to0$ as $n\to\infty$. Therefore

$$\boxed{p_c^{\mathrm{1D}}=1,\qquad q_c=0.}$$

The same conclusion holds for independent site occupation. **There is no tolerance to any positive density of defects in one dimension.**

### 2.2 Square lattice: four versus eight neighbours

A **four-neighbour** square lattice connects each site to its horizontal and vertical neighbours. An **eight-neighbour** lattice additionally connects diagonal neighbours. Site occupation is independent in either case.

![[Assets/w10-lattice-neighbours.png|700]]

*Same occupied sites ($p=0.50$), but extra diagonal connections make a crossing possible in the illustrated eight-neighbour realisation. This is a seeded simulation, not a claim that every realisation crosses.*

> [!proposition] Adding permitted edges cannot increase the threshold
> Couple the four- and eight-neighbour models by using **identical occupied sites**. Every four-neighbour path is also an eight-neighbour path, so
> $$\pi_n^{(8)}(p)\ge\pi_n^{(4)}(p),\qquad p_c^{(8)}\le p_c^{(4)}.$$
> This is a path-inclusion argument; it does not require computing either threshold.

> [!example] Thresholds used in Tutorial 10
> | Infinite lattice | Percolation type | Critical occupation $p_c$ |
> |---|---|---:|
> | 1D chain | Site or bond | $1$ |
> | Square, **4 neighbours** | Site | $\approx0.592746$ |
> | Square, **8 neighbours** | Site | $\approx0.407254$ |
> | Square, 4 neighbours | **Bond** | $1/2$ |
> | Triangular lattice | Site | $1/2$ |
>
> **Warning:** $0.592746$ is for *site* percolation on the **four-neighbour** lattice. The square-lattice *bond* threshold is instead $1/2$.

![[Assets/w10-lecture-lattice-table.png|650]]

*The lecturer’s broader threshold table (2026 lecture p. 135). It includes honeycomb, cubic, BCC and higher-dimensional lattices. **Key lesson:** $p_c$ depends on dimension and graph geometry, not just the degree $z$. For example, a four-neighbour square lattice and a 4-regular tree both have degree $4$, but their site thresholds are about $0.5927$ and $1/3$, respectively. The full list is for interpreting, not memorising numerical constants.*

### 2.3 How to estimate $p_c$ numerically (Tutorial 10, Exercise 1.2)

> [!algorithm] Monte Carlo crossing experiment
> 1. Choose a lattice side length $n$ and an occupation probability $p$.
> 2. Independently occupy each of its $n^2$ sites with probability $p$.
> 3. Find connected occupied clusters using **four** or **eight** neighbours, as specified.
> 4. Record $X=1$ if an occupied cluster touches both the **top and bottom** boundaries; otherwise set $X=0$.
> 5. Repeat for $R$ independent realisations and estimate $\hat\pi_n(p)=R^{-1}\sum_{r=1}^R X_r$.
> 6. Sweep over $p$ and repeat for increasing $n$. Locate the rapidly changing region or an approximate 50% crossing point.
>
> The statistical standard error at a fixed $p$ is approximately $\sqrt{\hat\pi(1-\hat\pi)/R}$. Larger boxes reduce finite-size effects; more realisations reduce sampling noise. The 50% crossing is a **finite-size estimator**, not a universal definition of $p_c$.

![[Assets/w10-crossing-probability.png|700]]

*Independent numerical crossing trials on finite square lattices. Dotted vertical lines show the known infinite-lattice site thresholds; plotted fluctuations are sampling effects.*

> [!code]- Connectivity kernels from the tutorial
> ```python
> import numpy as np
> from scipy.ndimage import label
>
> four = np.array([[0, 1, 0], [1, 1, 1], [0, 1, 0]])
> eight = np.ones((3, 3), dtype=int)
> occupied = np.random.default_rng(13).random((100, 100)) < 0.5
> labels, n_clusters = label(occupied, structure=eight)
> crossing_labels = (set(labels[0]) & set(labels[-1])) - {0}
> spans = bool(crossing_labels)
> ```
> A label of $0$ denotes **unoccupied** sites and must be excluded from the crossing test.

### 2.4 Cluster sizes near the threshold (Tutorial 10, Exercise 1.1)

Sort the connected occupied clusters as $N_1\ge N_2\ge\cdots$ and plot size against **rank**. On approaching $p_c$ from below, the distribution becomes broad: large clusters become more common, rather than all clusters staying small. Above $p_c$, a macroscopic cluster emerges and becomes separated from the small-cluster population.

![[Assets/w10-cluster-size-ranks.png|700]]

*Seeded finite-box calculation. Near $p_c\approx0.592746$, the upper tail becomes broad; the largest component is especially prominent above the threshold. Rank-size curves are not themselves a proof of a power-law cluster distribution.*

> [!remark] Kolmogorov zero–one law (lecture p. 131)
> With independent occupation variables on an infinite lattice, the event **“some infinite occupied cluster exists”** is unchanged by altering finitely many occupancies; it is a *tail event*. The zero–one law therefore gives probability $0$ or $1$ for that event at each fixed $p$.
>
> **Crucial distinction:** the probability $\theta(p)$ that a *particular* site lies in an infinite cluster can be strictly between $0$ and $1$. The zero–one law does **not** force $\theta(p)$ to be binary.

## 3. Bethe lattice: derive the threshold exactly

A **Bethe lattice** is an infinite $k$-regular tree: every vertex has degree $k$, and there are no cycles. Its independence between outward branches makes percolation analytically tractable.

> [!definition] Branch-failure probability
> Let $u$ be the probability that traversing a *particular outward edge* **fails** to reach an infinite occupied path. This happens if the edge is closed, or if it is open but all $k-1$ subsequent branches fail. Hence
>
> $$\boxed{u=(1-p)+p\,u^{k-1}.}\tag{1}$$
>
> The solution $u=1$ always exists. The physically relevant solution is the **smallest solution in $[0,1]$**.

> [!theorem] Percolation threshold of the $k$-regular tree
> For $k\ge3$, an infinite occupied cluster is possible precisely when
> $$\boxed{p(k-1)>1\quad\Longleftrightarrow\quad p>p_c=\frac1{k-1}.}$$
> Accordingly, $\boxed{q_c=1-1/(k-1)}$. For $k=2$, the result reduces to the 1D threshold $p_c=1$.

> [!derivation]- Why the derivative/branching criterion is $p(k-1)>1$
> Let $f(u)=1-p+pu^{k-1}$. At the trivial fixed point, $f'(1)=p(k-1)$. The fixed point $u=1$ loses stability as $p(k-1)$ exceeds $1$, and then a second fixed point $u<1$ is available.
>
> Equivalently, an open edge reaches a node with $k-1$ candidate outgoing edges, each open with probability $p$; the mean number of surviving offspring is $p(k-1)$. Infinite branching requires a mean exceeding $1$.

### 3.1 Worked calculation: $k=3$

Equation (1) becomes $u=1-p+pu^2$, or

$$p u^2-u+(1-p)=0\quad\Longleftrightarrow\quad(u-1)(pu+p-1)=0.$$

Thus

$$u=\begin{cases}1,&0\le p\le1/2,\\(1-p)/p,&1/2<p\le1.\end{cases}$$

The probability that **one specified outward branch** reaches infinity is $1-u$. The probability that the **root vertex** belongs to an infinite cluster is instead

$$\boxed{\theta(p)=1-u^3}\qquad(k=3),$$

because all three branches must fail for the root to be disconnected from infinity. Both become positive at $p_c=1/2$, but they are **different probabilities**.

![[Assets/w10-bethe-probabilities.png|700]]

> [!remark]- How this relates to the lecturer's $w=(1-p+pw)^2$
> The lecture defines $w$ as the probability that the **two onward branches of a reached degree-three node** eventually terminate. These two branches fail independently with probability $1-p+pw$, giving
> $$w=(1-p+pw)^2.$$
> The nontrivial solution is $w=((1-p)/p)^2$ for $p>1/2$.
>
> In the notation above, $w=u^2$ and the lecturer's $1-w$ is the survival probability *after arriving at a node*. The root-membership probability is $1-u^3$. **All conventions give the same threshold** $p_c=1/2$.

> [!example] Tutorial 10, Exercise 1.3: $k=5$
> $$p_c=\frac1{5-1}=\boxed{0.25},\qquad q_c=\boxed{0.75}.$$
> The tutorial compares this with edge deletion on **finite random 5-regular graphs**, which are locally tree-like, rather than finite depth-five trees, which have many leaves and boundary effects.

## 4. From lattices to random-graph robustness

The tree's threshold comes from the expected number of **new neighbours after following an edge**. For a $k$-regular tree this is $k-1$; for a random degree distribution it becomes

$$\kappa=\sum_z(z-1)\frac{zP(z)}{\langle z\rangle}=\frac{\langle z^2\rangle}{\langle z\rangle}-1.$$

Therefore the tree condition $p(k-1)>1$ generalises to $p\kappa>1$ in locally tree-like, uncorrelated random graphs. This is derived carefully in [[Percolation and robustness]].

> [!exam] Five facts to recognise immediately
> 1. **$p$ retains; $q=1-p$ removes.**
> 2. Four-neighbour square **site** percolation has $p_c\approx0.592746$; eight-neighbour site percolation has a lower threshold.
> 3. Infinite 1D percolation requires $p=1$.
> 4. For a $k$-regular tree, $p_c=1/(k-1)$; use **$k-1$**, not $k$.
> 5. A finite box shows a **smooth crossing curve**, not a mathematically sharp transition.

> [!selftest]- Self-test
> 1. Distinguish $\pi_n(p)$, $\theta(p)$ and $K_1$. — Crossing probability, root-membership probability, finite largest-component fraction.
> 2. Why is $p_c^{(8)}\le p_c^{(4)}$? — All four-neighbour paths remain available with eight-neighbour connections.
> 3. Derive the $k=3$ tree equation and its threshold. — $u=1-p+pu^2$, $p_c=1/2$.
> 4. Why may the event “an infinite cluster exists” have probability $1$ while $\theta(p)<1$? — The latter requires a **specified** node to belong to it.
> 5. What does the broad upper tail of a component rank-size plot suggest? — Growing clusters and proximity to percolation, not a definitive critical exponent.

---
**Related:** [[Percolation and robustness]] · [[Configuration model]] · [[Erdos-Renyi graphs]] · [[Threshold model and cascades]]
