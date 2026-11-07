---
tags: [data5441, ch11, dynamics]
aliases: [Threshold model, Watts cascade model, Vulnerable nodes, Global cascades]
---
# Threshold model and cascades

> [!abstract] Summary
> A node adopts when the **fraction** of its adopting neighbours exceeds its threshold. Low-degree nodes are easy to trigger ("vulnerable": one active neighbour suffices). Global cascades are possible when vulnerable nodes percolate, i.e. form a giant component.
> Chapter: [[Ch11 Cascades and binary models]]

> [!definition] Threshold model (Watts, PNAS 2002)
> Start with $\phi_i(0)=0$ for almost all $i$, plus a few seeds ("innovators"). Update by
> $$\phi_i(t+1)=\begin{cases}1&\text{if }\dfrac{m_i}{z_i}>q_i,\\[4pt]0&\text{otherwise,}\end{cases}$$
> where $m_i/z_i$ is the fraction of neighbours that have adopted. The thresholds $q_i$ are fixed in time and drawn i.i.d. from $f(q)$, with CDF $F(q)=\int_0^qf(q')dq'$. In the tutorial, adoption is permanent (active nodes stay active), seeds included.
> The question is $\rho_\infty$ as $N\to\infty$: $\rho_\infty=0$ means no cascade, and $\rho_\infty>0$ means a **global cascade**.

> [!example] Lecture example: $q_i=0.4$ for all $i$, synchronous
> - A node with $z=2$ and $m=1$ activates, since $1/2>0.4$.
> - A node with $z=3$ and $m=1$ does not, since $1/3<0.4$.
>
> The cascade stops at the first node of degree $\ge3$ with a single active neighbour.

![[threshold-activation.png|550]]

> [!definition] Vulnerable node
> Node $i$ is **vulnerable** if a single active neighbour suffices: $\dfrac1{z_i}>q_i$. The probability that a degree-$z$ node is vulnerable is
> $$\rho_z=F\!\left(\tfrac1z\right)=\Pr\!\left(q<\tfrac1z\right).$$
> $\rho_zP(z)$ is the fraction of nodes that have degree $z$ and are vulnerable.

> [!theorem] Cascade condition (lecture)
> A sufficient condition for a global cascade is that the vulnerable nodes form a giant component. In a random graph with degree distribution $P(z)$, applying the Molloy–Reed criterion to the vulnerable nodes gives
> $$\frac{\langle z^2\rangle_{vuln}}{\langle z\rangle_{vuln}}=\frac{\sum_{z\ge1}z^2\rho_zP(z)}{\sum_{z\ge1}z\rho_zP(z)}\ >\ 2 .$$

> [!remark] Precise branching form (refinement)
> Arriving along a random link at a vulnerable node of degree $z$ happens with probability $z\rho_zP(z)/\langle z\rangle$, and gives $z-1$ onward links. The vulnerable cluster percolates when
> $$R_v=\frac{\sum_zz(z-1)\rho_zP(z)}{\langle z\rangle}>1 .$$
> The denominator uses the full $\langle z\rangle$, because a link may lead to a non-vulnerable node. The tutorial computes the moment ratio on the **induced** vulnerable subgraph (internal degrees). Vulnerability is decided with the **original** degrees.

> [!proposition] Monotonicity
> For a fixed graph and seeds, the active set only grows, and the final set does not depend on the (fair) update order. Raising every $q_i$ can only shrink the cascade. Final cascades can exceed the vulnerable cluster, because non-vulnerable nodes can activate with $\ge2$ active neighbours.

> [!remark] Tutorial 11 observations
> - With uniform $q$, vulnerability jumps whenever $q$ crosses some $1/z$. For example, at $q=0.2$, degree-$5$ nodes stop being vulnerable, since $1/5>0.2$ is false.
> - The cascade window in $\langle z\rangle$ is bounded on both sides:
>   - sparse graphs lack paths;
>   - dense graphs have few vulnerable nodes.

![[tutorial-11-cell-36-plot-1.png|600]]

> [!selftest]- Self-test
> 1. Define vulnerable. When is a degree-4 node vulnerable for $q=0.2$? — $1/4>0.2$, yes.
> 2. State the lecture's cascade condition.
> 3. Which model in the trial-exam lists is a dynamical process? — The threshold model (and SIR).

---
Related: [[Binary-state dynamics]] · [[Percolation and robustness]] · [[Configuration model]]
