---
tags: [data5441, ch10, dynamics]
aliases: [Robustness, Resilience, Random failures, Targeted attacks, Critical failure fraction]
---
# Percolation and robustness of random graphs

> [!abstract] Summary
> **Robustness** means retaining a giant connected component after failures. On an *uncorrelated, locally tree-like random graph*, a giant component survives independent deletion with probability $q$ precisely when the surviving mean excess degree exceeds $1$. Broad degree distributions are usually robust to **random failure** but vulnerable to **targeted hub removal**.
> Chapter: [[Ch10 Resilience and percolation]] · **Week 10**, lecture pp. 137–143; Tutorial 10 §§2–3.

## 1. What are we measuring?

> [!definition] Failure experiment and giant component
> Start with a graph $g$ of $N$ original nodes. Delete each **edge** or **node** independently with probability $q$; let $p=1-q$ be the survival probability. The principal observable is
> $$S_N(q)=\frac{N_1(q)}{N},$$
> where $N_1$ is the largest connected-component size and the denominator is the **original $N$**. In large random graphs a non-zero limiting $S_N$ indicates a **giant component**.

> [!remark] Giant component versus diameter
> The giant-component fraction measures **how much of the network remains mutually reachable**. The diameter of the *largest surviving component* measures **how far apart its most distant nodes are**. Near a finite-size breakdown, a component can become long and tenuous, so its diameter often increases before it collapses; this is not a universal monotonic law.

## 2. Derive the critical failure probability

> [!theorem] Random failure threshold *(course formula sheet)*
> Let $P(z)$ be the original degree distribution and $\langle z\rangle>0$. Write
> $$\kappa=\frac{\langle z(z-1)\rangle}{\langle z\rangle}=\frac{\langle z^2\rangle}{\langle z\rangle}-1.$$
> For independent, uniform **bond failure** (and uniform random **site failure**, under the same configuration-model assumptions), the giant component persists when
> $$\boxed{(1-q)\kappa>1.}$$
> The formal threshold is
> $$\boxed{q_c=1-\frac{1}{\langle z^2\rangle/\langle z\rangle-1}}\qquad\left(p_c=\frac{\langle z\rangle}{\langle z^2\rangle-\langle z\rangle}\right).$$
> If $\kappa\le1$ initially, there is no giant component to destroy at $q=0$; a negative formal $q_c$ has no physical meaning as a failure fraction.

> [!derivation]- Why does $\langle z^2\rangle$ appear?
> When following a random edge, we reach degree $z$ with the **size-biased** probability $zP(z)/\langle z\rangle$, not $P(z)$. The arrival edge cannot be used to continue, so the expected number of *additional* edges is
> $$\sum_z(z-1)\frac{zP(z)}{\langle z\rangle}=\kappa.$$
> Only the fraction $p=1-q$ survives, leaving mean offspring $p\kappa$. A supercritical branching process requires $p\kappa>1$.
>
> Equivalently, for bond deletion $z'\mid z\sim\mathrm{Bin}(z,p)$, so $\langle z'\rangle=p\langle z\rangle$ and $\langle z'(z'-1)\rangle=p^2\langle z(z-1)\rangle$, leading again to $\kappa'=p\kappa$.

## 3. Examples you should calculate quickly

| Original graph | $\langle z^2\rangle/\langle z\rangle$ | Critical $q_c$ |
|---|---:|---:|
| Poisson / ER, mean degree $c>1$ | $c+1$ | $1-1/c$ |
| $k$-regular, $k>2$ | $k$ | $1-1/(k-1)$ |
| Scale-free tail, $2<\gamma\le3$ (diverging second moment) | $\to\infty$ | $\to1$ |

> [!example] ER with average degree $4$
> Since $\langle z^2\rangle=c^2+c=20$, we have $\kappa=20/4-1=4$ and $\boxed{q_c=1-1/4=0.75}$. The prediction concerns the **large-$N$ giant-component threshold**, not the point where a finite graph's largest component becomes exactly empty.

> [!exam] Trial Exam 2, Q7 — uniform degrees $1,\ldots,z^*$
> With $P(z)=1/z^*$, $\langle z\rangle=(z^*+1)/2$ and $\langle z^2\rangle=(z^*+1)(2z^*+1)/6$; hence
> $$\frac{\langle z^2\rangle}{\langle z\rangle}=\frac{2z^*+1}{3},\qquad \boxed{q_c=1-\frac{3}{2(z^*-1)}}.$$
> For $z^*\gg1$, $q_c\approx1-3/(2z^*)$. **More degree heterogeneity makes the graph more robust to uniform random failures** in this model.

![[Assets/w10-robustness-curves.png|720]]

> [!remark] Interpret the finite-size figure
> The plot shows repeated **random edge deletion** on ER and BA graphs with similar initial average degree. It is **illustrative simulation**, not a theoretical BA threshold. The ER vertical line marks its predicted $q_c$; finite networks have a smooth crossover. BA resilience is stronger in the infinite-size heavy-tailed limit, but differences can be modest for these small finite graphs.

## 4. Random failures versus targeted attacks

> [!definition] Targeted node attack
> Instead of removing nodes uniformly at random, remove **high-degree nodes first**. A **static** attack ranks degrees once; an **adaptive** attack recalculates degrees after each deletion. The removed fraction is measured relative to the original nodes.

> [!proposition] Why hubs matter
> Hubs contribute disproportionately to $\langle z^2\rangle$ because of the **squared** degree. Random failure typically misses the few highest-degree hubs; attacking them removes a substantial share of the network's potential onward connections.
>
> For a degree-dependent site-survival probability $\phi_z$, the corresponding configuration-model branching condition is
> $$\boxed{\frac{\sum_z z(z-1)P(z)\phi_z}{\langle z\rangle}>1.}$$
> This explains the **robust-yet-fragile** behaviour of heterogeneous networks; the exact attack threshold depends on the degree distribution and the attack protocol.

> [!algorithm] Tutorial 10 — numerical robustness experiment
> 1. Generate an ER or BA network and store the **original** $N$ and its edges.
> 2. **Random failure:** assign each edge one uniform random mark $u_e$; at failure fraction $q$, retain precisely $u_e>q$ (nested deletion).
> 3. **Targeted attack:** order nodes by initial degree (or recompute degrees if adaptive) and delete the first $\lfloor qN\rfloor$ nodes.
> 4. For every $q$, compute $N_1/N$ and, if non-empty, the largest-component diameter.
> 5. Repeat over independent networks / deletion orders; report averages and variability.

> [!code]- Minimal NetworkX example — nested bond failures
> ```python
> import numpy as np
> import networkx as nx
> rng = np.random.default_rng(13)
> edges = list(G.edges())
> marks = rng.random(len(edges))  # sample once for all q
> fractions = []
> for q in np.linspace(0, 1, 51):
>     H = nx.Graph()
>     H.add_nodes_from(G)          # preserve the original N
>     H.add_edges_from(e for e, u in zip(edges, marks) if u > q)
>     n1 = max((len(c) for c in nx.connected_components(H)), default=0)
>     fractions.append(n1 / len(G))
> ```
> This models **edge failure**; for node attacks remove vertices instead. The nesting of the same edge marks ensures that increasing $q$ cannot increase $N_1$ within a realisation.

> [!exam] Remember
> **Use $z-1$ when traversing an edge**. The key inequality is $p(\langle z^2\rangle/\langle z\rangle-1)>1$; do **not** confuse $p$ (survival) and $q$ (deletion). The same degree variability that makes hubs common in BA-like graphs gives random-failure resilience and targeted-attack vulnerability.

> [!selftest]- Check your understanding
> 1. Compute $q_c$ for ER with $c=6$. — $5/6$.
> 2. Why does degree bias change the branching factor? — Following an edge samples $zP(z)$, and the arrival edge is already used.
> 3. Does removing 30% of edges imply 30% of vertices leave the network? — No; bond deletion keeps every original vertex.

---
Related: [[Percolation on lattices]] · [[Configuration model]] · [[Power laws]] · [[SIR model and epidemic threshold]] · [[Threshold model and cascades]]
