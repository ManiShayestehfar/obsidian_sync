---
tags: [data5441, ch04, models]
aliases: [Fixed degree sequence, Stub matching, Molloy–Reed, Excess degree]
---
# Configuration model

> [!abstract] Summary
> The configuration model fixes the degree sequence and randomises everything else. It is the right null model for networks with broad degree distributions. Its giant component appears when $\langle z^2\rangle/\langle z\rangle>2$.
> Chapter: [[Ch04 Sampling random graphs]]

> [!definition] Configuration model (stub matching)
> Give node $i$ exactly $z_i$ half-links ("stubs"), where $\sum_iz_i=2L$ must be even. Pair the $2L$ stubs uniformly at random.
> Degrees are preserved exactly, but self-loops and multi-links can occur. The uniform simple-graph version with the same degrees is a different ensemble; it is sampled with degree-preserving swaps (see [[Markov chain Monte Carlo on graphs]]).

> [!definition] Graphical sequence
> A degree sequence is **graphical** if some simple graph realises it. An even sum is necessary but not sufficient: $(3,3,1,1)$ has even sum but is not graphical.

> [!theorem] Expected number of links between $i$ and $j$
> For $i\ne j$,
> $$\mathbb E[A_{ij}]=\frac{z_iz_j}{2L-1}\approx\frac{z_iz_j}{2L}.$$

> [!proof]-
> Each of the $z_i$ stubs of $i$ is paired with a uniformly chosen one of the other $2L-1$ stubs, and $z_j$ of these belong to $j$. Summing the $z_i$ indicator expectations gives $z_iz_j/(2L-1)$. $\square$
>
> This $z_iz_j/2L$ is exactly the null term in **modularity**; see [[Community detection]].

> [!theorem] Giant component criterion (Molloy–Reed)
> In the large-$N$, locally tree-like limit, a giant component exists iff
> $$\frac{\langle z^2\rangle}{\langle z\rangle}>2\qquad\Longleftrightarrow\qquad \kappa=\frac{\langle z^2\rangle-\langle z\rangle}{\langle z\rangle}>1 .$$

> [!proof]- Branching argument
> Follow a random link. By degree bias (see [[Sampling and friendship paradox]]), it reaches a node of degree $z$ with probability $zP(z)/\langle z\rangle$, and that node has $z-1$ further links. The mean number of new links reached is
> $$\kappa=\sum_z(z-1)\frac{zP(z)}{\langle z\rangle}=\frac{\langle z^2\rangle-\langle z\rangle}{\langle z\rangle}.$$
> Exploring a component is a branching process with offspring mean $\kappa$. It survives (giant component) iff $\kappa>1$, i.e. $\langle z^2\rangle/\langle z\rangle>2$. $\square$
>
> **Checks:** Poisson$(c)$ degrees have $\kappa=c$, recovering the ER threshold $c>1$. A $z$-regular graph has $\kappa=z-1$.

> [!proposition] Generating-function form
> Let $G_0(s)=\sum_zP(z)s^z$ and $G_1(s)=G_0'(s)/\langle z\rangle$. The probability $u$ that a link does not lead to the giant component solves $u=G_1(u)$ (smallest root), and $S=1-G_0(u)$.

> [!proposition] Clustering of the configuration model
> $$C\approx\frac{\langle z\rangle}{N}\left(\frac{\langle z^2\rangle-\langle z\rangle}{\langle z\rangle^2}\right)^{2}\xrightarrow{N\to\infty}0\quad(\text{finite moments}).$$
> Observed clustering far above the degree-preserving null indicates triangle closure that the degrees do not explain.

> [!exam] Trial Exam 2, Q7(c)(i): uniform degrees on $\{1,\dots,z^*\}$
> Here $\langle z\rangle=(z^*+1)/2$ and $\langle z^2\rangle=(z^*+1)(2z^*+1)/6$, so $\langle z^2\rangle/\langle z\rangle=(2z^*+1)/3$.
> - $z^*=1$: ratio $1<2$, no giant component.
> - $z^*=2$: ratio $5/3<2$, no giant component.
> - $z^*=3$: ratio $7/3>2$, giant component.
>
> The transition lies between $z^*=2$ and $3$.

> [!code]- NetworkX
> ```python
> assert nx.is_graphical(z)
> M = nx.configuration_model(z, seed=13)          # multigraph, defects possible
> G = nx.Graph(M); G.remove_edges_from(nx.selfloop_edges(G))   # "erased": degrees change!
> ```

> [!selftest]- Self-test
> 1. Which null model preserves an observed broad degree sequence? — The configuration model.
> 2. What is the giant component criterion? — $\langle z^2\rangle/\langle z\rangle>2$.
> 3. Why does erasing loops and multi-links change the model? — It reduces degrees.

---
Related: [[Sampling and friendship paradox]] · [[Percolation and robustness]] · [[Power laws]] · [[Markov chain Monte Carlo on graphs]]
