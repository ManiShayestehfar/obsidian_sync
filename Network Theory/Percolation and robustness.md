---
tags: [dynamics]
---

# Percolation and robustness

> [!definition] Retention and removal
> In **bond percolation**, each edge is retained independently with probability $p$; in **site percolation**, each vertex is retained independently with probability $p$, together with edges whose endpoints survive. Write $q=1-p$ for removal probability. A finite largest-component fraction is a random quantity; a percolating giant is a positive limiting fraction in a specified graph sequence.

Let $p_k$ be the original degree distribution, $\langle k\rangle>0$, and $\kappa=\langle k(k-1)\rangle/\langle k\rangle$. The following describes an uncorrelated, locally tree-like configuration-model limit, not every graph with those moments.

> [!theorem] Uniform-retention threshold
> The branching process is supercritical when $p\kappa>1$. If $\kappa>1$, the threshold is
> $$p_c=\frac1\kappa=\frac{\langle k\rangle}{\langle k^2\rangle-\langle k\rangle},\qquad q_c=1-p_c.$$
> The strict inequality identifies the supercritical regime. Equality and degenerate degree laws need separate analysis. If $\kappa<1$, no feasible $p\le1$ makes this branching process supercritical.

> [!proof] Two equivalent calculations
> Following a surviving connection reaches a degree-biased vertex with $\kappa$ potential onward edges on average; independent retention leaves mean $p\kappa$.
>
> For bond thinning, $K'\mid K=k\sim\mathrm{Binomial}(k,p)$, hence
> $$\mathbb E[K']=p\mathbb E[K],\qquad\mathbb E[(K')^2]=p^2\mathbb E[K^2]+p(1-p)\mathbb E[K].$$
> Equivalently $\mathbb E[K'(K'-1)]=p^2\mathbb E[K(K-1)]$, giving new excess mean $p\kappa$ for $p>0$.

Using the generating functions in [[Configuration model]], the branch-failure equation is $u=1-p+pG_1(u)$. Bond giant fraction is $1-G_0(u)$; site giant fraction relative to the **original** vertex count is $p[1-G_0(u)]$. The site fraction conditional on retention omits the leading $p$.

## Examples and targeted removal
A $k$-regular tree has threshold $1/(k-1)$ for $k\ge2$. For $k=3$, $u=1-p+pu^2$ has a nontrivial root $u=(1-p)/p$ when $p>1/2$, and the root vertex’s bond survival probability is $1-u^3$. A branch probability and a full root probability are not the same quantity. A line has threshold one. A Poisson model with original mean degree four has $p_c=1/4$, hence $q_c=3/4$.

If a degree-$k$ vertex is retained with probability $\phi_k$, the analogous branching factor is
$$\frac1{\langle k\rangle}\sum_k k(k-1)p_k\phi_k.$$
The denominator is the original mean degree. Preferential removal of hubs changes this factor differently from uniform retention. Sequential attacks that continually recompute degrees add another adaptive mechanism.

For suitable heavy-tailed model sequences with diverging second moment and finite mean, $p_c\to0$. This does not imply a finite network is unaffected by failures, or that its giant remains large for tiny $p$. Nor may a random-removal formula be applied unchanged to arbitrary targeted attacks.

> [!code] Measure bond robustness without changing the denominator
> ```python
> import networkx as nx
> import numpy as np
>
> G = nx.random_regular_graph(4, 200, seed=5441)
> rng = np.random.default_rng(5441)
> rows = []
> for p in [0.2, 0.4, 0.6, 0.8, 1.0]:
>     for _ in range(20):
>         H = nx.Graph()
>         H.add_nodes_from(G)  # retain isolated vertices
>         H.add_edges_from((u, v) for u, v in G.edges() if rng.random() < p)
>         size = max(map(len, nx.connected_components(H)), default=0)
>         rows.append((p, size/len(G)))
> print(rows[:3])
> ```
> These are retention experiments on one fixed graph. Averaging also over the original graph ensemble answers a different question.

[[Epidemic models]] uses related branching ideas for transmission; [[Binary dynamics and cascades]] treats degree-dependent vulnerability.

> [!reference]- Sources
> Jenny’s notes Weeks 10 and 13, with corrected threshold parentheses, branch/root distinction and maximum-degree interpretation. Newman §§15.1–15.3 and §16.3. Related course foundations: Lectures Weeks 3–4. Current-course lecture/tutorial coverage after Week 7 was not supplied.
