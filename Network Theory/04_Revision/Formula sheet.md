---
type: study-note
tags: [DATA5441]
---

# Formula sheet

[[00_HOME]]

Use [[Notation and conventions]] and the linked concept notes for assumptions. This sheet covers the supplied Weeks 1–7.

| Topic | Formula | Condition / interpretation |
| --- | --- | --- |
| Edge count | $L=\tfrac12\sum_i k_i$ | Undirected; loops counted twice in degree |
| Simple graph count | $2^{\binom N2}$ | Labelled vertices, no loops |
| Triangles | $T=\operatorname{tr}(A^3)/6$ | Simple undirected graph |
| Transitivity | $C=3T/\sum_i\binom{k_i}2$ | Denominator nonzero |
| Katz | $x=(I-\alpha A)^{-1}\mathbf1$ | $0\le\alpha<1/\rho(A)$ |
| Edge-endpoint mean | $\mathbb E[K]=\langle k^2\rangle/\langle k\rangle$ | Uniform oriented edge, positive mean degree |
| ER degree | $K\sim\mathrm{Binomial}(N-1,q)$ | Independent dyads |
| ER fitted density | $\widehat q=2L/[N(N-1)]$ | Fit expected edge count |
| ER sparse degree | $K\Rightarrow\mathrm{Poisson}(c)$ | $q\sim c/N$, fixed $c$ |
| ER giant | $S=1-e^{-cS}$ | Sparse large-$N$ limit, physical largest root |
| Excess degree | $\kappa=(\langle k^2\rangle-\langle k\rangle)/\langle k\rangle$ | Endpoint-biased arrival |
| Configuration giant | $\kappa>1$ | Suitable locally tree-like random-graph limit |
| MH | $a=\min(1,\pi(h)Q(g\mid h)/[\pi(g)Q(h\mid g)])$ | Valid support and proposal ratio |
| WS ring | $C(0)=3(Q-1)/[2(2Q-1)]$ | $2Q$ neighbours, $N>3Q$ |
| Power-law moment | $\mathbb E[K^r]<\infty\iff\gamma>r+1$ | Infinite pure tail, lower cutoff positive |
| Natural cutoff | $k_{max}\asymp N^{1/(\gamma-1)}$ | Independent-tail sampling heuristic |
| BA continuum | $k_i(t)\approx m\sqrt{t/t_i}$ | Large-time approximation |
| ERGM | $p_\beta(g)=e^{\beta\cdot x(g)}/Z(\beta)$ | Specified graph support |
| ERGM moment | $\partial_{\beta_i}\log Z=\mathbb E[x_i]$ | Finite support |
| Bernoulli SBM MLE | $\widehat p_{rs}=l_{rs}/y_{rs}$ | $y_{rs}>0$ |
| Profile NLL | $F=-\sum_{r\le s}[l\log(l/y)+(y-l)\log(1-l/y)]$ | Zero terms handled by limits |
| Nonempty partitions | $S(N,B)$ unlabelled; $B!S(N,B)$ labelled | Do not substitute $B^N/B!$ as an identity |
| Tempered search | $a=\min(1,e^{-\beta\Delta F})$ | Symmetric allocation proposal |

Useful limiting checks: an empty graph has no triangles; a complete graph with $N\ge3$ has clustering one; a tree has zero clustering; $q=0,1$ give deterministic ER extremes; $B=1$ is ER; $B=N$ saturates the fitted Bernoulli SBM.
