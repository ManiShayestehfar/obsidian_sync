---
tags: [data5441, exam]
aliases: [Exam formula sheet]
---
# Formula sheet (provided in the exam)

> [!info] Context
> This is the last page of both trial papers. Format: closed book, 2 h writing, non-programmable calculator; the short-answer and extended-answer parts are worth 50% each.
> Convention: undirected simple graph, adjacency $A$, $z_i=\sum_jA_{ij}$, $\sum_iz_i=2L$.

> [!definition] Degree distribution and variability
> $$P(z)=\frac{N_z}{N}=\frac1N\sum_{i=1}^N\delta_{z,z_i},\qquad\langle z^n\rangle=\sum_zz^nP(z)=\frac1N\sum_iz_i^n,\qquad\sigma_z=\sqrt{\langle z^2\rangle-\langle z\rangle^2}.$$
> See [[Graphs and representations]].

> [!definition] Clustering
> $$C_i=\frac{T_i}{\binom{z_i}2}=\frac{2T_i}{z_i(z_i-1)}\ (z_i\ge2),\ C_i=0\ (z_i<2);\qquad C_{net}=\frac{3T}{\sum_i\binom{z_i}2},\qquad\langle C\rangle=\frac1N\sum_iC_i.$$
> See [[Clustering]].

> [!definition] Laplace matrix
> $\mathbf L=D-A$, $\mathbf L_{ij}=z_i\delta_{ij}-A_{ij}$. See [[Spectral graph theory]].

> [!definition] Eigenvector and PageRank centrality
> $$x_i(t+1)=\sum_jA_{ij}x_j(t);\qquad x_i(t+1)=\alpha\sum_jA_{ij}\frac{x_j(t)}{z_j^{out}}+\beta .$$
> See [[Centrality]].

> [!definition] Barabási–Albert
> One new node with $m$ links per step; attachment probability $\pi_i=z_i/\sum_jz_j=z_i/2L$. See [[Preferential attachment]].

> [!definition] SBM
> $\Pr(A_{ij}=1\mid b_i=r,b_j=s)=p_{rs}$, with connectivity matrix $P=(p_{rs})$. See [[Stochastic block models]].

> [!definition] Modularity
> $$Q=\frac1{2L}\sum_{i,j}\Big(A_{ij}-\frac{z_iz_j}{2L}\Big)\delta_{b_i,b_j}.$$
> See [[Community detection]].

> [!definition] Breakdown under link deletion
> Deleting links independently with probability $q$ breaks the network when $q>q_c$, where
> $$q_c=1-\frac{1}{\langle z^2\rangle/\langle z\rangle-1}.$$
> See [[Percolation and robustness]].

> [!warning] Not on the sheet — memorise these
> - **ER:** $p=2L/[N(N-1)]$, $C\approx p$, $S=1-e^{-\langle z\rangle S}$.
> - **Giant component:** $\langle z^2\rangle/\langle z\rangle>2$.
> - **Graph-space sizes:** $2^Y$ and $\binom YL$.
> - **Metropolis–Hastings:** the acceptance rule.
> - **Max entropy:** the ERGM form $p(g)=e^{\beta\cdot x(g)}/Z$.
> - **SBM:** the MLE $\hat p_{rs}=l_{rs}/y_{rs}$.
> - **Small world:** the three conditions.
> - **BA:** $\langle z\rangle\to2m$ and $\gamma=3$.
> - **Power laws:** $z_{max}\sim N^{1/(\gamma-1)}$.
> - **Cascades:** the vulnerable-node condition.
> - **Epidemics:** the SIR ODEs and the thresholds $1/\langle z\rangle$ and $\langle z\rangle/\langle z^2\rangle$.

---
Up: [[00 Home]] · Related: [[Exam patterns]]
