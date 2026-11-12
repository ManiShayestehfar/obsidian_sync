---
tags: [data5441, ch08, inference]
aliases: [Modularity, Louvain, Kernighan–Lin, Graph partitioning, Girvan–Newman]
---
# Community detection

> [!abstract] Summary
> **Community detection** seeks groups of nodes with more connections *within* groups than *between* them. Different approaches answer different questions: **Kernighan–Lin** reduces a cut with prescribed group sizes; **modularity** compares within-group links to a degree-based null model; **spectral methods** use Laplacian eigenvectors; and **SBMs** infer a generative block structure. These methods are mostly heuristics: the best partition *found* need not be the global optimum.
> Chapter: [[Ch08 Community detection]] · Sources: DATA5441 **Week 8**, lecture pp. 101–112; Tutorial 8.

## 1. Graph partitioning: minimise links across groups

> [!definition] Partition and cut size
> A partition $\mathcal P=\{V_1,\ldots,V_B\}$ consists of disjoint non-empty sets whose union is all $N$ nodes. For a bisection $V=V_1\sqcup V_2$, the **cut size** is
> $$R(V_1,V_2)=\sum_{i\in V_1}\sum_{j\in V_2}A_{ij},$$
> counting the links crossing the two groups **once**. Without a non-triviality/size restriction, minimising $R$ is uninformative: we could put everything in one group. **Kernighan–Lin fixes the two group sizes** (usually a near-balanced split).

> [!algorithm] Kernighan–Lin (KL) bisection — what it actually does
> **Input:** an undirected graph and two groups of prescribed sizes.
> 1. **Initialise:** choose a bisection $V_1,V_2$; mark all nodes *unlocked*.
> 2. **Find a swap:** among unlocked pairs $a\in V_1$, $b\in V_2$, choose the pair offering the **largest reduction in cut size** (or smallest increase). Swap them and lock both nodes for this pass.
> 3. **Continue the pass:** repeat until no unlocked cross-group pair remains, recording the cut after each swap. Individual swaps may temporarily **worsen** the cut.
> 4. **Keep the best prefix:** retain only the first $k$ swaps that gave the best intermediate cut (or revert the pass if there was no improvement).
> 5. **Repeat passes** until no pass decreases the cut.
>
> **Output:** a locally improved *bisection*, not an estimate of $B$ and not a modularity maximum. Fixing group sizes prevents the trivial cut, while temporary uphill swaps can escape simple one-swap traps.

> [!derivation]- Efficient swap gain (optional)
> Write $E_a$ for node $a$'s links to the *other* group and $I_a$ for its links within its *own* group; let $D_a=E_a-I_a$ (similarly for $b$). The cut reduction when swapping $a$ and $b$ is
> $$g(a,b)=D_a+D_b-2A_{ab},\qquad R_{\rm after}=R_{\rm before}-g(a,b).$$
> The correction $-2A_{ab}$ accounts for an edge directly joining $a,b$, which remains a crossing edge after the swap. Choose the largest $g$ among unlocked pairs; the full KL pass then selects its best *cumulative* gain.

![[Assets/w8-kl-cut.png|680]]

## 2. Modularity: more links *inside* than expected by chance

> [!definition] Modularity *(course formula sheet)*
> Let $L$ be the number of links and $z_i=\sum_j A_{ij}$ the degree. For labels $b_i\in\{1,\ldots,B\}$,
> $$\boxed{Q(\mathbf b)=\frac{1}{2L}\sum_{i,j}\left(A_{ij}-\frac{z_iz_j}{2L}\right)\delta_{b_i,b_j}.}$$
> - $A_{ij}$: whether $i,j$ **are** linked.
> - $z_iz_j/(2L)$: **expected** link multiplicity in the configuration-model null approximation.
> - $\delta_{b_i,b_j}$: count only pairs in the **same group**.
>
> Thus $Q=\text{observed internal-link fraction}-\text{expected internal-link fraction}$. Maximising $Q$ searches for unexpectedly *assortative* groups; it is **not** the same as minimising a cut.

> [!theorem] Useful group formula and merge gain
> Let $l_r$ be the actual number of edges inside block $r$, $K_r=\sum_{i\in V_r}z_i$ its total degree, and $l_{rs}$ the number of edges between distinct blocks $r,s$. Then
> $$Q=\sum_r\left[\frac{l_r}{L}-\left(\frac{K_r}{2L}\right)^2\right],\qquad
> \boxed{\Delta Q_{r\cup s}=\frac{l_{rs}}L-\frac{K_rK_s}{2L^2}.}$$
> A positive merge gain means the two blocks have **more links between them than expected** from their degrees, so merging improves modularity.

> [!proof]- Short derivation
> Inside group $r$, $\sum_{i,j\in V_r}A_{ij}=2l_r$ and $\sum_{i,j\in V_r}z_iz_j=K_r^2$. This gives the group formula. On merging $r,s$, the internal edge count increases by $l_{rs}$; the degree-square term changes by $(K_r+K_s)^2-K_r^2-K_s^2=2K_rK_s$. Subtraction yields $\Delta Q$.

> [!remark] Useful reference partitions
> - **One group:** $Q=0$ exactly.
> - **Every node alone:** $Q=-\sum_i (z_i/2L)^2<0$ for $L>0$ (simple graph).
> - **Positive $Q$:** more within-block links than the null expectation, **but not proof** of meaningful planted communities.
> - $Q<1$, and modularity has well-known **resolution** and optimisation limitations.

## 3. Algorithms that maximise modularity

> [!algorithm] Greedy agglomerative (bottom-up)
> 1. Start with **$B=N$ single-node groups**.
> 2. Compute $\Delta Q$ for every eligible pair of groups.
> 3. **Merge the pair with the largest $\Delta Q$**, record the new $(B,Q)$, and recompute gains.
> 4. Continue until one group remains; **return the partition with largest $Q$ along the path**, not necessarily the final partition.
>
> Early merges cannot be undone. Efficient implementations exploit community adjacency and sparse data structures.

> [!algorithm] Greedy divisive (top-down; Tutorial 8 / Trial 1)
> 1. Start with **$B=1$**, all nodes together.
> 2. For each splittable current group, propose a **KL bisection** of its induced subgraph.
> 3. Evaluate the **whole-network modularity** of the proposed new partition (not merely its cut).
> 4. Accept the split giving the largest resulting $Q$ and repeat; retain the best $(B,Q)$ found.
>
> Unlike agglomeration, previous splits are not subsequently recombined.

> [!algorithm] Louvain: local moves + aggregation
> 1. Start with one community per node. Move each node into a neighbouring community **if** doing so increases $Q$; repeat until no favourable local move remains.
> 2. **Coarsen:** replace each community by a super-node, retaining edge weights and internal self-loops so modularity is preserved.
> 3. Repeat local optimisation and coarsening until modularity stops improving.
>
> **Intuition:** optimise at several scales rather than committing to only one sequence of merges or splits. Louvain is a **heuristic**, not a proof of optimality.

![[Assets/w8-community-search.png|680]]

## 4. Other community-detection perspectives

| Approach | What it uses / optimises | Important distinction |
|---|---|---|
| **Graph partitioning (KL)** | Cut size $R$, for prescribed group sizes | Does **not** infer $B$ or maximise $Q$ |
| **Modularity (greedy, Louvain)** | Excess internal connectivity relative to degree null | Can detect chance fluctuations |
| **Centrality (Girvan–Newman)** | Repeatedly removes edges with high **edge betweenness** | Reveals bridges between groups; recompute betweenness |
| **Dynamical (label propagation)** | Propagation of local labels through connections | Fast but seed/order-dependent |
| **Spectral** | Small Laplacian eigenvalues/eigenvectors | Relaxed partitioning; see [[Spectral graph theory]] |
| **Inferential (SBM)** | Fit a probabilistic generative block model | Can represent disassortative/core–periphery patterns; see [[Stochastic block models]] |

> [!remark] A method finding groups is not evidence that real communities exist
> Two separate tasks are: (i) **find** the best partition according to an objective and (ii) **test** whether that structure is stronger than a suitable random/null model. Maximising over many partitions can yield high modularity even for random data.

## 5. Exam interpretation and tutorial lessons

> [!exam] Trial 1, Q8 — why algorithms disagree
> On the Karate Club network, the supplied solutions report best $B=3$ for all four methods, but different modularities: **greedy agglomerative $0.435$; greedy divisive $0.412$; NetworkX greedy $0.411$; Louvain $0.418$**. Each method visits different partitions and is **path dependent**. The largest observed value is not necessarily the global maximum.

> [!exam] Trial 2, Q8 — Louvain finds 44 communities in an ER graph
> With $N=1000$, expected degree $4$, Louvain returned **44 groups, $Q=0.523$**. The graph has *no planted blocks*: optimisation selects a partition exploiting random finite-sample edge-density fluctuations. Since the one-group partition has $Q=0$, a higher-scoring partition is favoured. **Do not equate large $Q$ with genuine social communities.**

> [!example] Assortative versus disassortative SBM (Tutorial 8)
> In a five-block example, $p_{rr}=0.2-q$ and $p_{rs}=q$ ($r\ne s$).
> - $q<0.1$: within-block links are more likely (**assortative**).
> - $q=0.1$: all pair probabilities are $0.1$ (no block signal; **ER**).
> - $q>0.1$: between-block links are more likely (**disassortative**).
>
> Modularity explicitly rewards **assortative** partitions; it need not recover the planted blocks in the last case. Community labels can always be permuted without changing the partition.

> [!code]- Core NetworkX calls (Tutorial 8)
> ```python
> from networkx.algorithms import community
> part_KL = community.kernighan_lin_bisection(G, seed=13)
> part_greedy = list(community.greedy_modularity_communities(G))
> part_louvain = community.louvain_communities(G, seed=13)
> Q = community.modularity(G, part_louvain)
> ```

> [!selftest]- Self-test
> 1. **KL versus modularity?** — KL minimises the cut under fixed sizes; modularity maximises excess internal links against a degree-based null.
> 2. **Why keep the best prefix in KL?** — Some individual swaps worsen the cut, but a later combination may improve it.
> 3. **Why might Louvain detect groups in ER?** — Selecting the best partition from many candidate partitions exploits random fluctuations.
> 4. **Which methods explicitly optimise modularity?** — Greedy agglomerative/divisive (as defined here) and Louvain; KL alone does not.

---
Related: [[Spectral graph theory]] · [[Stochastic block models]] · [[Configuration model]] · [[Centrality]] · [[Link prediction]]
