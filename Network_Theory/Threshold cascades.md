---
tags: [dynamics]
---

# Threshold cascades

A single contact can spread a simple infection; adoption of a new behaviour may require reinforcement from a fraction of one’s neighbours. Threshold models make that distinction explicit and connect spreading to the percolation of vertices that respond to just one active contact.

## Progressive adoption and the strict threshold

> [!definition] The course’s threshold model
> Choose a seed set and thresholds $q_i\in[0,1]$. A previously inactive vertex with degree $k_i>0$ becomes active when
> $$\frac{m_i}{k_i}>q_i.$$
> Once active it stays active. Isolates remain inactive unless seeded. The **strict inequality** is the Week 11 lecture/tutorial convention; using $\ge$ changes behaviour at exact threshold values.

![[Assets/threshold-activation.png|760]]
*Illustration of the strict rule at $q=0.4$: one active neighbour out of three is insufficient; two suffice. The central vertex is the candidate for activation.*

For a fixed graph, seeds and thresholds, the active set grows monotonically. Under any fair update order, the final active set equals the smallest set containing the seeds that is closed under activation. To see this, successive activations belong to every closed superset of the seeds; conversely a fair process cannot stop before all eligible vertices have activated. This equality concerns the **final set**, not identical time trajectories.

> [!code]- Queue-based final cascade, without redundant sweeps
> ```python
> from collections import deque
> import networkx as nx
>
> def cascade_closure(g, seeds, q):
>     seeds = set(seeds)
>     if not 0 <= q <= 1 or not set(seeds) <= set(g):
>         raise ValueError('Require q in [0,1] and valid seeds')
>     active = set(seeds)
>     count = {v: 0 for v in g}
>     queue = deque(active)
>     while queue:
>         v = queue.popleft()
>         for u in g.neighbors(v):
>             if u in active:
>                 continue
>             count[u] += 1
>             if count[u] / g.degree(u) > q:
>                 active.add(u)
>                 queue.append(u)
>     return active
>
> G = nx.path_graph(8)
> assert len(cascade_closure(G, {0}, 0.49)) == 8
> assert len(cascade_closure(G, {0}, 0.50)) == 1
> ```
> The strict boundary matters. Each activated vertex is processed once, giving an efficient closure computation. It does not reproduce asynchronous sweep times.

## Vulnerability links adoption to percolation

> [!definition] Vulnerable vertex
> A degree-$k$ vertex is vulnerable if one active neighbour suffices: $1/k>q_i$. Write $v_k=\Pr(q_i<1/k\mid K=k)$ for $k\ge1$. Decide vulnerability using **original degrees**. If constructing the induced vulnerable graph, recompute degrees within that graph afterwards.

A giant vulnerable component permits a macroscopic cascade when the seed can activate a vertex in it. It does not guarantee a large cascade from every seed. Non-vulnerable vertices can join later after receiving multiple active contacts; the final cascade can therefore exceed the vulnerable component.

> [!theorem] Vulnerable branching factor
> In an uncorrelated locally tree-like random-graph approximation with original degree law $p_k$,
> $$R_v=\frac{\sum_{k\ge1}k(k-1)p_kv_k}{\langle k\rangle}.$$
> The vulnerable branching process is supercritical when $R_v>1$. Equality is the critical boundary.

**Proof.** An arriving edge reaches degree $k$ with probability $kp_k/\langle k\rangle$. Only a vulnerable destination activates from that one contact, and it then offers $k-1$ onward branches. Averaging gives the expression. The denominator remains the original mean degree: conditioning only on being vulnerable would omit the chance of reaching a vulnerable vertex. $\square$

The lecture’s moment ratio needs careful interpretation. A ratio $\langle d^2\rangle/\langle d\rangle>2$ can be applied as the same branching diagnostic to **internal degrees $d$ of the induced vulnerable graph**, assuming that graph is adequately described by the locally tree-like approximation. This is how the notebook computes it. Replacing those degrees with the original degrees of vulnerable vertices, without thinning their neighbours, is not the same criterion. In a finite graph this moment diagnostic does not certify a particular component size or seed outcome.

## Reading the experiments

![[Assets/tutorial-11-cell-36-plot-1.png|720]]
*Supplied Tutorial 11, cell 36: internal-degree moment ratio of the vulnerable subgraph of its fixed ER graph. The discontinuities occur as the strict threshold crosses values $1/k$.*

For uniform $q$, vulnerability switches at reciprocal degrees: at $q=0.2$, a degree-five vertex is no longer vulnerable because $1/5>0.2$ is false. Increasing $q$ can only shrink the cascade for fixed graph and seeds. Increasing ER density need not help monotonically: sparse graphs lack paths, while large degrees require more than one reinforcing neighbour.

The notebook declares a finite cascade “large” when at least half the original vertices activate. For its fixed graph and innovator, supplied outputs show a sharp change near $q=0.2$ and an approximately matching loss of a large vulnerable component. These are instance-specific observations. In particular, the displayed simulation cell 19 actually uses $q=0.2$, despite the surrounding exercise first asking about $0.15$; its small final fraction should not be read as the answer for $q=0.15$.

## For revision

- Keep irreversible activation, strict threshold and the initial seed explicit.
- Distinguish original degrees used for vulnerability from induced degrees used in the notebook diagnostic.
- Explain why threshold responses jump at $1/k$, why connectivity alone is insufficient, and why a giant vulnerable component need not be reached by every seed.

Connections: [[Percolation and robustness]] supplies the branching language; [[Binary dynamics and cascades]] supplies the update conventions.

> [!reference]- Sources
> Lecture Week 11 pp.5–7; Tutorial 11 §2 and Ex.2.1–2.2, particularly cells 18–36. Jenny’s notes Week 11. The vulnerable branching derivation corrects the original-degree interpretation in the handwritten ratio. Watts (2002), PNAS 99, 5766–5771, is the model reference cited in the lecture; Newman §§12.2, 15.3 give degree-biased/degree-dependent branching background. The notebook figure is a supplied output; the local activation diagram is newly drawn.
