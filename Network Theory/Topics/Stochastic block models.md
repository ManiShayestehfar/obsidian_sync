---
tags: [data5441, ch07, inference]
aliases: [SBM, Block model, Assortative, Disassortative, Core-periphery]
---
# Stochastic block models

> [!abstract] Summary
> An SBM assigns each node to a block. Links are independent, with a probability that depends only on the two blocks. For a fixed partition the maximum-likelihood $p_{rs}$ is simply (observed links)/(possible links). Finding the partition is a hard optimisation or sampling problem.
> Chapter: [[Ch07 SBMs and statistical inference]]

> [!definition] Stochastic block model *(formula sheet)*
> Nodes are partitioned into $B$ non-empty, mutually exclusive blocks, with $b_i\in\{1,\dots,B\}$. Conditional on $\mathbf b$, links are independent with
> $$\Pr(A_{ij}=1\mid b_i=r,b_j=s)=p_{rs}.$$
> $P=(p_{rs})$ is the connectivity matrix (symmetric for undirected graphs). $B=1$ recovers ER.

> [!definition] Meso-scale structures
> - **Assortative (communities):** $p_{rr}>p_{rs}$ for $r\ne s$.
> - **Disassortative:** links mostly between blocks, e.g. bipartite with $p_{rr}=0$.
> - **Core–periphery:** $p_{cc}>p_{cp}>p_{pp}$.

![[sbm-block-structure.png|550]]

> [!definition] Counts
> Let $n_r$ be the size of block $r$, and $l_{rs}$ the number of links between blocks $r$ and $s$ (within-block links counted once). The number of possible links is:
> - undirected: $y_{rr}=\binom{n_r}{2}$ and $y_{rs}=n_rn_s$ for $r\ne s$;
> - directed, no self-links: $y_{rr}=n_r(n_r-1)$ and $y_{rs}=n_rn_s$.

> [!theorem] Likelihood and MLE for a fixed partition
> $$\ln P(A\mid\mathbf b,P)=\sum_{r\le s}\Big[l_{rs}\ln p_{rs}+(y_{rs}-l_{rs})\ln(1-p_{rs})\Big],\qquad \hat p_{rs}=\frac{l_{rs}}{y_{rs}}.$$
> Values $0$ and $1$ are valid boundary estimates. If $y_{rs}=0$, $p_{rs}$ is not identified.

> [!proof]-
> Block pair $(r,s)$ contributes $l_{rs}$ link factors $p_{rs}$ and $y_{rs}-l_{rs}$ non-link factors $1-p_{rs}$. For $0<l<y$, setting $\dfrac{d}{dp}\big[l\ln p+(y-l)\ln(1-p)\big]=\dfrac lp-\dfrac{y-l}{1-p}=0$ gives $p=l/y$, and the second derivative is negative. For $l=0$ or $l=y$ the function is monotone, so the maximum is at the boundary. $\square$

> [!exam] SBM computations (all four trial SBM questions follow this pattern)
> **Bipartite authorship** (Trial 2, Q6): $200$ articles, $40$ authors, $3$ authors per article.
> - $L=600$.
> - $p_{11}=p_{22}=0$ and $p_{12}=600/(200\cdot40)=3/40$.
> - The structure is **disassortative**.
> - $\Pr(a,b$ both wrote article $B)=p_{12}^2=9/1600$, because links are independent in the SBM.
> - Real data have **more** repeated co-authorships than this.
>
> **Directed classes** (Trial 2, Q5): $3$ classes of $30$; entries are mean named friends per student.
> - $p_{aa}=5/29$, since $30\cdot5$ links out of $30\cdot29$ possible.
> - $p_{bc}=30\cdot1/(30\cdot30)=1/30$.
> - Expected reciprocal $b$–$c$ pairs $=30\cdot30\cdot p_{bc}p_{cb}=1$.
> - Real networks have **more** reciprocity than the SBM predicts.
>
> **Five planted groups** (Trial 1, Q1b): $p_{rr}=\dfrac{l_{rr}}{\binom92}=\dfrac{32}{36}=\dfrac89$ (there are $L=45\cdot8/2=180$ links, of which $\binom52\cdot2=20$ are between groups, leaving $160/5=32$ inside each group) and $p_{rs}=\dfrac{2}{81}$, from $2$ links over $9\times9$ pairs.

> [!definition] Profile objective
> For a partition $\mathbf b$, define $F(\mathbf b)=-\ln P\big(A\mid\mathbf b,\hat P(\mathbf b)\big)$ (minus the maximised log-likelihood). Fitting the SBM means minimising $F$ over partitions.

> [!algorithm] Searching partitions
> - **Greedy:** try every single-node block change, take the best strict improvement, and stop when none exists. It can get trapped in **local minima**, so use several starts.
> - **Metropolis:** propose a random single-node move and accept with $\min\{1,e^{-\beta\Delta F}\}$. At $\beta=1$ this samples $\propto e^{-F}$. Increasing $\beta$ (simulated annealing) turns it into an optimiser, without a guarantee of the global optimum.
>
> Compare partitions only **up to relabelling** of blocks.

> [!remark] Degree correction
> An ordinary SBM groups nodes with similar connectivity patterns, so it may separate hubs from non-hubs rather than recover social groups. The degree-corrected SBM uses intensities $\theta_i\theta_j\omega_{b_ib_j}$ to factor out degrees.

> [!code]- NetworkX (tutorial 7)
> ```python
> G = nx.stochastic_block_model([20, 50], [[0.15, 0.01], [0.01, 0.20]], seed=13)
> # fitted p_rs = l_rs / y_rs for a given partition b
> ```

> [!selftest]- Self-test
> 1. Give $\hat p_{rs}$ for undirected and directed SBMs.
> 2. Why do SBM-predicted repeated co-authorships underestimate real data? — Real links are correlated (teams), not independent.
> 3. Why can greedy search fail? — Local minima.

---
Related: [[Statistical inference and model selection]] · [[Community detection]] · [[Link prediction]] · [[Erdos-Renyi graphs]]
