---
type: study-note
tags: [DATA5441]
---

# Notation and conventions

[[00_HOME]]

Unless stated otherwise, graphs are labelled, undirected, unweighted and simple: no loops or repeated edges. The vertex set is fixed when comparing graph ensembles.

| Symbol | Meaning |
| --- | --- |
| $N,L,Y=\binom N2$ | Vertices, edges, possible undirected dyads |
| $A_{ij}$ | One if $i$ and $j$ are adjacent |
| $z_i$ or $k_i$ | Degree; $\sum_i z_i=2L$ |
| $\langle z\rangle$ | Empirical mean over vertices, $2L/N$ |
| $\mathbb E$ | Expectation over a probability model; specify which model |
| $C_i,\bar C,C_{net}$ | Local clustering, mean local clustering, transitivity |
| $q$ | ER edge probability; lecturer sometimes uses $p$ |
| $c$ | Sparse ER limiting mean degree, with $q\sim c/N$ |
| $p$ in WS | Rewiring probability, not ER density |
| $p_k$ | Degree probability, not an edge probability |
| $\Omega,p(g)$ | Graph state space and target distribution |
| $\Pi(h\mid g),a(g,h),W(g\to h)$ | Proposal, acceptance, full transition |
| $B,b_i,n_r,p_{rs}$ | Number of blocks, allocation, size, connection probability |
| $F=-\log\mathcal L$ | Negative log-likelihood to minimise |

The course often uses $C_{net}$ for transitivity; do not silently replace it with `average_clustering`. Set $C_i=0$ when $z_i<2$ unless a question excludes these vertices. For disconnected graphs, specify whether distances are over reachable pairs or a chosen component. For directed graphs in these notes, $A_{ij}=1$ means $i\to j$; incoming centrality therefore uses $A^\top$.

$\log$ is natural logarithm unless a base is shown. Distinguish exact finite-$N$ identities, large-$N$ limits, approximations and numerical observations. Newman often writes $n,m,k$ where lectures use $N,L,z$.
