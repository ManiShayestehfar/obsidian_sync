---
tags: [data5441, ch10, dynamics]
aliases: [Robustness, Resilience, Random failures, Targeted attacks, Critical failure fraction]
---
# Percolation and robustness of random graphs

> [!abstract] Summary
> Randomly delete links (or nodes) with probability $q$. A random graph keeps a giant component while $q<q_c=1-\dfrac1{\langle z^2\rangle/\langle z\rangle-1}$. Broad degree distributions push $q_c\to1$ (robust to failures), but removing the hubs breaks them quickly (fragile to attacks).
> Chapter: [[Ch10 Resilience and percolation]]

> [!theorem] Critical failure fraction *(formula sheet)*
> For an uncorrelated, locally tree-like random graph with degree distribution $P(z)$, deleting links (or nodes) independently with probability $q$ destroys the giant component when $q>q_c$, where
> $$q_c=1-\frac{1}{\dfrac{\langle z^2\rangle}{\langle z\rangle}-1},\qquad\text{equivalently}\quad p_c=1-q_c=\frac{\langle z\rangle}{\langle z^2\rangle-\langle z\rangle}.$$

> [!proof]-
> Follow a link to a node. Its mean number of further links is $\kappa=\dfrac{\langle z^2\rangle}{\langle z\rangle}-1$ (degree bias; see [[Configuration model]]). Each further link survives with probability $p=1-q$, so the surviving branching process has mean offspring $p\kappa$.
> A giant component exists iff $p\kappa>1$. The critical point is $p_c=1/\kappa$, i.e. $q_c=1-1/\kappa$.
> Check under bond thinning: the surviving degree satisfies $z'\mid z\sim\mathrm{Bin}(z,p)$, with $\langle z'\rangle=p\langle z\rangle$ and $\langle z'(z'-1)\rangle=p^2\langle z(z-1)\rangle$. So the new excess degree is $p\kappa$. $\square$

> [!example] Standard cases
> | Network | $\langle z^2\rangle/\langle z\rangle$ | $q_c$ |
> |---|---|---|
> | ER, $\langle z\rangle=c$ | $c+1$ | $1-1/c$ (e.g. $0.75$ at $c=4$) |
> | $z$-regular | $z$ | $1-1/(z-1)$ |
> | half degree $4$, half degree $k$ | $\dfrac{16+k^2}{4+k}$ | $1-\dfrac{4+k}{12+k^2-k}$ |
> | scale-free, $2<\gamma\le3$ | $\to\infty$ | $\to1$ |

> [!exam] Trial Exam 2, Q7(c)(ii–iii): uniform degrees on $\{1,\dots,z^*\}$
> Here $\langle z^2\rangle/\langle z\rangle=(2z^*+1)/3$, so
> $$q_c=1-\frac{3}{2(z^*-1)}\approx1-\frac3{2z^*}\quad(z^*\gg1).$$
> - Sketch: $\theta(q)$ decreases from its $q=0$ value and vanishes at $q_c$.
> - Increasing $z^*$ increases $q_c$ towards $1$, so the network becomes **more robust** to random failures.

> [!definition] Targeted attack
> Remove nodes in decreasing order of degree.
> - **Static:** rank degrees once.
> - **Adaptive:** re-rank after each removal.
>
> With degree-dependent survival $\phi_z$, the branching factor becomes $\sum_zz(z-1)P(z)\phi_z/\langle z\rangle$, so removing hubs reduces it fastest.

> [!theorem] Robust yet fragile
> Heavy-tailed networks have $\langle z^2\rangle\to\infty$:
> - **robust** to random failure ($q_c\to1$), because random removals rarely hit hubs;
> - **fragile** under targeted attack, because removing a small fraction of hubs makes $\langle z^2\rangle$ finite and small, destroying the giant component.
>
> ER graphs behave similarly under failure and attack, because their degrees are homogeneous.

![[tutorial-10-cell-58-plot-1.png|650]]

> [!remark] Observables in tutorial 10
> - $S=N_1/N_0$ uses the **original** $N_0$. It cannot increase as more items are removed (nested failures).
> - The diameter of the largest cluster **peaks** near the transition (a finite-size signature).
> - The diameter is undefined once the graph is empty.

> [!code]- Simulating failures (tutorial 10)
> ```python
> rng = np.random.default_rng(13); marks = rng.random(G.number_of_edges())
> for q in qs:                           # nested: same marks for every q
>     H = nx.Graph(); H.add_nodes_from(G)
>     H.add_edges_from(e for e, u in zip(G.edges(), marks) if u > q)
>     S.append(len(max(nx.connected_components(H), key=len)) / G.number_of_nodes())
> ```

> [!selftest]- Self-test
> 1. Derive $q_c$ from the branching argument.
> 2. ER with $\langle z\rangle=4$: what is $q_c$? — $0.75$.
> 3. Why are scale-free networks robust to failure but fragile to attack?

---
Related: [[Percolation on lattices]] · [[Configuration model]] · [[Power laws]] · [[SIR model and epidemic threshold]] · [[Threshold model and cascades]]
