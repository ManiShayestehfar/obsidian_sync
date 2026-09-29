---
tags: [dynamics]
---

# Binary dynamics and cascades

> [!definition] Binary-state process
> Each vertex has state $X_i(t)\in\{0,1\}$, degree $k_i$ and active-neighbour count $m_i(t)=\sum_jA_{ij}X_j(t)$. Specify activation rate $F_{k,m}$, deactivation rate $R_{k,m}$ and the update scheme. The active fraction is $\rho(t)=N^{-1}\sum_iX_i(t)$.
>
> A continuous-time rate has units of inverse time and is not itself a probability. Over a sufficiently short interval $dt$, an event with rate $r$ has probability $r\,dt+o(dt)$.

Synchronous updates change every vertex using the old state. Asynchronous updates change one vertex/event at a time and immediately affect later choices. These can produce different dynamics, not merely different clocks. If each vertex has update rate one, order $N$ updates correspond to one unit of time.

Examples include the voter rule (copy a random neighbour), majority vote (adopt a local majority with a specified tie/noise rule), and the infection/recovery processes in [[Epidemic models]]. Isolated vertices need their own update convention.

> [!derivation] Derivation: Degree-based mean field
> Let $\rho_k(t)$ be the fraction active among degree-$k$ vertices, and $p_k$ the degree distribution. Under an uncorrelated-neighbour, independent-state closure,
> $$\omega(t)=\frac{\sum_k kp_k\rho_k(t)}{\langle k\rangle},\qquad B_{k,m}(\omega)=\binom{k}{m}\omega^m(1-\omega)^{k-m},$$
> $$\dot\rho_k=(1-\rho_k)\sum_{m=0}^kF_{k,m}B_{k,m}(\omega)-\rho_k\sum_{m=0}^kR_{k,m}B_{k,m}(\omega).$$
> The first term counts inactive-to-active transitions and the second the reverse. The edge-endpoint distribution explains the degree weight in $\omega$. Sparse graphs can still have dynamical correlations; sparsity alone does not make this closure exact.

## Progressive threshold cascades
Take thresholds $\theta_i\in(0,1]$ and a seed set. An inactive vertex with $k_i>0$ activates when $m_i/k_i\ge\theta_i$ and remains active. Isolates activate only if seeded. This uses the inclusive convention; with strict $>$, change threshold equalities consistently. Retaining activation corrects the reversible rule written in the student notes.

> [!theorem] Vulnerable branching criterion
> Let $v_k=\Pr(\theta\le1/k\mid K=k)$, $k\ge1$. In an uncorrelated locally tree-like random-graph limit, the vulnerable branching process is supercritical when
> $$R_v=\frac{\sum_{k\ge1}k(k-1)p_kv_k}{\langle k\rangle}>1.$$
> An arriving edge reaches degree $k$ with probability $kp_k/\langle k\rangle$; vulnerability permits transmission through its other $k-1$ edges. This gives the formula. Normalising only over vulnerable vertices loses the probability of reaching one. A giant vulnerable cluster permits small-seed cascades when the seed can reach it; it does not guarantee a cascade from every seed.

> [!code] Monotone threshold closure
> ```python
> import networkx as nx
>
> def threshold_cascade(g, seeds, thresholds):
>     active = set(seeds)
>     if not active <= set(g) or set(thresholds) != set(g):
>         raise ValueError('Seeds and thresholds must match the vertices')
>     if any(not 0 < value <= 1 for value in thresholds.values()):
>         raise ValueError('Thresholds must lie in (0, 1]')
>     history = [len(active)]
>     while True:
>         added = {v for v in g if v not in active and g.degree(v) > 0
>                  and sum(u in active for u in g.neighbors(v))/g.degree(v)
>                  >= thresholds[v]}
>         if not added:
>             return active, history
>         active |= added
>         history.append(len(active))
>
> G = nx.path_graph(8)
> final, counts = threshold_cascade(G, {0}, {v: 0.5 for v in G})
> print(counts)
> ```
> This computes a synchronous progressive process and terminates because active sets only grow on a finite graph. It does not simulate the reversible voter or majority model.

For a homogeneous threshold, large degree provides more contacts but makes activation by **one** contact less likely. Thus increasing connectivity need not monotonically increase susceptibility to a small trigger. Contrast simple contagion with reinforcement-based activation.

> [!reference]- Sources
> Jenny’s notes Week 11; the mean-field equation and elementary derivations above clarify its assumptions. Newman §12.2 and §15.3 support degree-biased and degree-dependent branching. Watts (2002), “A simple model of global cascades on random networks”, PNAS 99, 5766–5771, [primary paper](https://www.stat.berkeley.edu/~aldous/260-FMIE/Papers/watts.pdf), for the progressive model and cascade criterion. Current-course lecture/tutorial coverage after Week 7 was not supplied.
