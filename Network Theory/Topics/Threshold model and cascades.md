---
tags: [data5441, ch11, dynamics]
aliases: [Threshold model, Watts cascade model, Vulnerable nodes, Global cascades]
---
# Threshold model and cascades

> [!abstract] Summary
> The **Watts threshold model** describes innovation or failure spreading: a node adopts when the fraction of its adopting neighbours is **strictly greater** than its threshold. A node is *vulnerable* if one active neighbour suffices. Large connected components of vulnerable nodes provide a mechanism for **global cascades**.
> Chapter: [[Ch11 Cascades and binary models]] · **2026 lecture pp. 148–150** · **Tutorial 11, Section 2** · Jeny pp. 52–53.

## 1. Motivation and definition

Examples from the lecture include **power-grid blackouts**, **adoption of innovations** and **spreading of memes**. The central question is: *Can a small number of initially active nodes trigger a macroscopic response?*

> [!definition] Watts threshold model (2002)
> Start with $\phi_i(0)=0$ for almost all nodes, apart from a small set of **innovators** (seeds). For node $i$, let $k_i$ be its degree and $m_i(t)$ its number of adopting neighbours. Its personal threshold $q_i$ is fixed in time.
> $$\boxed{\phi_i(t+1)=\begin{cases}1,&m_i(t)/k_i>q_i,\\0,&\text{otherwise},\end{cases}}$$
> with the **irreversible-adoption convention** of Tutorial 11: once $\phi_i=1$, it stays 1. A seed is kept active; an isolated non-seed node cannot activate.
>
> In the heterogeneous model, thresholds are sampled independently from a density $f(q)$, with cumulative distribution $F(q)=\Pr(q_i\le q)=\int_0^qf(x)\,dx$.

> [!remark] Two distinct probabilities
> $p$ may denote the **link probability** in an ER graph $G(N,p)$; $q_i$ is a **node's adoption threshold**. Increasing $p$ changes the network. Increasing $q_i$ makes adoption more difficult.

## 2. How a cascade propagates

> [!example] Lecture example: $q_i=0.4$
> - A node with $k_i=2$ and $m_i=1$ adopts because $1/2>0.4$.
> - A node with $k_i=3$ and $m_i=1$ **does not** adopt because $1/3<0.4$.
> - The node of degree 3 can adopt later if **two** neighbours become active, since $2/3>0.4$.
>
> This explains how a cascade may travel along a chain of low-degree nodes and stop at a high-degree node.

![[Assets/w11-threshold-cascade.png|670]]

> [!algorithm] Simulate the threshold model (Tutorial 11)
> 1. Construct a graph and mark an innovator as active.
> 2. Select an inactive node (or compute all candidates for a synchronous step).
> 3. Count its active neighbours $m_i$ and evaluate $m_i/k_i>q_i$.
> 4. If the inequality holds, change $\phi_i$ to 1 **permanently**.
> 5. Continue until **no inactive node is eligible** to adopt. A sweep with no observed changes is not, by itself, proof of completion under random selection.
>
> The output is $\rho(t)=N^{-1}\sum_i\phi_i(t)$ and its final value.

> [!definition] Global cascade
> In the large-network limit, $\rho_\infty>0$ indicates a **global cascade** (a non-vanishing fraction of nodes activated); $\rho_\infty=0$ indicates no macroscopic cascade. For **Exercise 2.1 only**, the notebook operationally calls a *finite* cascade **large** if at least half the nodes activate.

## 3. Vulnerability and the percolation connection

> [!definition] Vulnerable node
> A degree-$k_i>0$ node is **vulnerable** if one adopting neighbour is already sufficient:
> $$\boxed{\frac1{k_i}>q_i.}$$
> The strict inequality matters. For instance, if $q=0.2$, a degree-4 node is vulnerable ($1/4>0.2$), whereas a degree-5 node is **not** ($1/5=0.2$).

> [!proposition] Vulnerability by degree (lecture)
> For a graph with degree distribution $P(k)$, let $\rho_k$ denote the probability that a degree-$k$ node is vulnerable:
> $$\rho_k=\Pr(q_i<1/k)=F(1/k)\quad\text{for a continuous threshold distribution}. $$
> Therefore $\rho_kP(k)$ is the **fraction of all nodes** that are both degree $k$ and vulnerable. Larger $k$ makes the one-neighbour fraction $1/k$ smaller, so vulnerability generally becomes less likely.

> [!remark] Why percolation enters
> A connected component made of vulnerable nodes can propagate activation **from a single activated entry point**: each vulnerable node needs only one active neighbour. Hence a *giant vulnerable component* is a **sufficient mechanism for a global cascade**, provided an initial innovator reaches it.
>
> This does **not** mean a large vulnerable component guarantees a cascade from *every* innovator. Adoption can also spread beyond the vulnerable set once non-vulnerable nodes receive several active neighbours.

## 4. Course's moment-ratio test and how the tutorial uses it

> [!proposition] Lecture's degree-moment comparison
> Writing $\rho_kP(k)$ for vulnerable-node frequencies, the Week 11 lecture relates the vulnerable-node test to Week 10's giant-component criterion and displays
> $$\frac{\langle k^2\rangle_{\mathrm{vuln}}}{\langle k\rangle_{\mathrm{vuln}}}=\frac{\sum_k k^2\rho_kP(k)}{\sum_k k\rho_kP(k)}>2.$$
> **Read this as the lecture's heuristic comparison.** The $k$ in the displayed sum is the **original degree**; by itself, this expression is **not** the internal-degree moment ratio of the network remaining after removing non-vulnerable nodes.

> [!algorithm] Operational test in Tutorial 11, Exercise 2.2
> 1. On the **original graph**, find every vulnerable node using its **original** degree $k_i$ and $1/k_i>q$.
> 2. Remove the non-vulnerable nodes; retain the **induced subgraph** on vulnerable nodes.
> 3. Recompute the degrees $k'_i$ **inside this induced subgraph**.
> 4. Calculate its largest component size $K_1/N$, normalised by the **original** $N$.
> 5. Calculate $\langle (k')^2\rangle/\langle k'\rangle$ from these **new degrees**, compare with the reference value 2, and compare the result to actual simulated cascades.
>
> **Do not interchange the two degree conventions.** The tutorial's computed quantity and the lecture's weighted original-degree expression are not automatically equal.

![[Assets/w11-vulnerable-subgraph.png|710]]

> [!remark] Why the plots jump with $q$
> For common threshold $q$, node $i$ changes from vulnerable to non-vulnerable at $q=1/k_i$. Degrees are integers, so the vulnerable set changes in **steps**, not continuously. Removing a few key vulnerable nodes can abruptly split a large component.

## 5. What Tutorial 11 asks you to investigate

> [!exam] Exercise 2.1 — simulation
> The notebook uses an ER graph $G(N,p)$ with $N=500$ and a small set of innovators (in the supplied code, **one** innovator). Investigate:
> - fixed $p=0.01$: whether a cascade is large at $q=0.15$;
> - what happens as $q$ increases, and where a large cascade disappears;
> - at fixed $q$, how changing $p$ changes cascade size (the notebook suggests $0\le p\le0.03$).
>
> **Interpretation:** Raising $q$ inhibits adoption. Raising $p$ can initially aid spreading by adding connections but can also reduce vulnerability by raising degrees. Do not assume larger $p$ always causes a larger cascade.

> [!exam] Exercise 2.2 — vulnerability versus actual cascades
> Vary $q$ over $0<q<0.3$ on the same graph. Compare the final active fraction, $K_1/N$ of the vulnerable graph, and its internal-degree moment ratio. The threshold $\langle(k')^2\rangle/\langle k'\rangle=2$ is the **reference**, not a promise that every finite sample changes sharply at exactly that point.

> [!selftest]- Quick checks
> 1. $q=0.2$ and $k=5$: vulnerable? — **No**, because $1/5=0.2$ does not satisfy a strict $>$.
> 2. What is a global cascade? — A positive fraction of nodes ultimately adopts as $N\to\infty$.
> 3. Why does $K_1/N$ sometimes jump at a specific $q$? — Vulnerability changes at the discrete values $q=1/k$.
> 4. Which degree is used to decide vulnerability? Which for the tutorial's moment ratio? — **Original** degree; then **induced-subgraph** degree.

---
Related: [[Binary-state dynamics]] · [[Percolation and robustness]] · [[SI and SIS models]] · [[Configuration model]]
