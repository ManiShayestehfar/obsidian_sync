---
tags: [data5441, ch11, dynamics]
aliases: [Threshold model, Watts cascade model, Vulnerable nodes, Global cascades]
---
# Threshold model and cascades

> [!abstract] Summary
> Adoption spreads when the **fraction** of active neighbours exceeds a node-specific threshold. A node is **vulnerable** when **one** active neighbour suffices. Vulnerable nodes can pass activity along paths; if they contain a giant connected component, even a very small seed can trigger a macroscopic cascade with positive probability.
> Chapter: [[Ch11 Cascades and binary models]] · **Week 11**, lecture pp. 148–150; Tutorial 11 §2.

## 1. Mechanism: individual adoption thresholds

> [!definition] Watts threshold model
> Let $\phi_i(t)\in\{0,1\}$ denote whether node $i$ has adopted. Set $m_i(t)=\sum_jA_{ij}\phi_j(t)$ and fix a threshold $q_i\in[0,1]$ for each node. The **permanent-adoption** rule used in the tutorial is
> $$\boxed{\phi_i(t+1)=\phi_i(t)\;\lor\;\mathbf1\!\left\{\frac{m_i(t)}{z_i}>q_i\right\},\qquad z_i>0.}$$
> A small initial seed set (innovators) is active at $t=0$; adopted nodes **stay** adopted. Isolated inactive nodes cannot be activated by neighbours. We study $\rho_\infty=\lim_{t\to\infty}N^{-1}\sum_i\phi_i(t)$.

> [!example] A fixed threshold $q=0.4$
> - Degree $2$, one active neighbour: $1/2>0.4$, so **adopts**.
> - Degree $3$, one active neighbour: $1/3<0.4$, so **does not adopt yet**.
> - Degree $3$, two active neighbours: $2/3>0.4$, so **adopts**.
>
> **High degree can make a node *harder* to activate by one neighbour**, even though it may have many active neighbours in total.

![[Assets/w11-threshold-cascade.png|730]]

> [!remark] Read the example
> The left and right panels have exactly the same graph and initial adopter $0$; only the common threshold changes. Node $2$ has degree $3$. A single adopter in its neighbourhood is enough at $q=0.25$ but insufficient at $q=0.40$, so the latter cascade stops after two nodes.

## 2. Vulnerable nodes

> [!definition] Vulnerability
> A degree-$z$ node is **vulnerable** if a *single* active neighbour would trigger adoption:
> $$\boxed{q_i<\frac1z.}$$
> If thresholds are independent of degrees with cumulative distribution $F(q)$, the degree-dependent vulnerability probability is
> $$v_z=\Pr(q_i<1/z)=F(1/z^-),$$
> where the left limit records the **strict inequality**. For a continuous threshold distribution, this equals $F(1/z)$. The fraction of all nodes both degree $z$ and vulnerable is $P(z)v_z$.

> [!remark] Why one vulnerable node is not enough
> A chain of vulnerable vertices transmits adoption from a single activated neighbour at every step. A **giant vulnerable component** provides the possibility of a **global cascade**, provided the seeds reach it. Non-vulnerable nodes can also activate later from two or more active neighbours, so the final cascade need not equal the vulnerable component.

## 3. Derive the vulnerable-cluster criterion

> [!theorem] Vulnerable branching condition (uncorrelated random graph)
> Suppose the underlying random graph is locally tree-like, and vulnerability depends only on original degree. Following a random edge reaches degree $z$ with probability $zP(z)/\langle z\rangle$; the reached node is vulnerable with probability $v_z$ and offers $z-1$ new edges. Hence
> $$\boxed{R_v=\frac{\sum_z z(z-1)P(z)v_z}{\langle z\rangle}>1}$$
> is the supercritical condition for a giant **vulnerable connected component**, and therefore a route to cascades from rare seeds.

> [!derivation]- Why the denominator matters
> The expected number of *vulnerable onward branches* reached from a random edge is $\sum_z[zP(z)/\langle z\rangle]\,v_z\,(z-1)$. The denominator is the mean degree of the **entire original network**, since the randomly followed edge may lead to a node that is *not vulnerable*.
>
> **Lecture shorthand versus precise formula:** the lecture motivates this using the moment ratio of vulnerable nodes, $\sum z^2v_zP(z)/\sum zv_zP(z)>2$. That ratio treats the original degrees as if they were degrees **inside the induced vulnerable graph** and is not generally the correct site-percolation test. For a measured vulnerable **induced subgraph**, use its *actual internal degrees* to apply a Molloy–Reed approximation; for the original configuration-model ensemble use $R_v>1$ above.

## 4. Why cascades appear only in a window

> [!remark] Sparse versus dense random graphs (Tutorial 11)
> - **Very sparse:** many nodes are easy to activate, but the graph has no large connected structure to carry a cascade.
> - **Intermediate degree:** enough connections exist, and plenty of vertices remain vulnerable — global cascades are possible.
> - **Very dense:** $1/z$ is small, making most nodes **not vulnerable**; a single seed often cannot start a large cascade.
>
> Thus adding more edges can first **help** spreading and then **suppress** single-seed cascades.

> [!algorithm] Simulating permanent threshold adoption
> 1. Choose a fixed graph, thresholds $q_i$, and initial active seeds.
> 2. Examine inactive nodes and compute their **current** active-neighbour fraction $m_i/z_i$.
> 3. Activate those satisfying the strict inequality; never deactivate an adopted node.
> 4. Repeat fairly until a complete pass causes no new adoption. Return $\rho_\infty$.
>
> Synchronous and fair asynchronous updates may have different **trajectories**, but for this monotone fixed-threshold rule they reach the same smallest final active set containing the seeds.

> [!exam] Remember
> **Threshold is a proportion, not a count.** Vulnerable means $1/z>q$; for fixed $q$, vulnerability changes at $q=1/z$. The giant **vulnerable** component explains why a tiny seed can sometimes trigger a macroscopic cascade, not why *every* seed must do so.

> [!selftest]- Check your understanding
> 1. At $q=0.2$, is a degree-$5$ node vulnerable? — **No**, because $1/5>0.2$ is false.
> 2. Why is there no global cascade in an extremely sparse graph, even with many vulnerable nodes? — They are not in a giant connected set.
> 3. Can a non-vulnerable vertex ever activate? — Yes, after multiple neighbours adopt.

---
Related: [[Binary-state dynamics]] · [[Percolation and robustness]] · [[Configuration model]] · [[SI and SIS models]]
