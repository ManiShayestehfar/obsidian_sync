---
type: study-note
tags: [DATA5441]
---

# Power laws and finite-size cutoffs

[[00_HOME]]

Sources: Week 5 pp.7–9; Newman §10.4, especially printed pp.327–328 (PDF pp.340–341).

If $p_k\sim Ak^{-\gamma}$, the survival tail satisfies $\Pr(K\ge k)\asymp k^{1-\gamma}$ for $\gamma>1$. Thus a probability-mass log–log slope is $-\gamma$, while a survival-plot slope is $-(\gamma-1)$.

The moment integral is
$$\int_{k_{min}}^{k_{max}} k^{r-\gamma}\,dk.$$
It remains bounded as $k_{max}\to\infty$ if $\gamma>r+1$, grows as $\log k_{max}$ at equality, and as $k_{max}^{r+1-\gamma}$ below equality. Finite graphs always have finite empirical moments.

For independent tail samples, estimate the natural maximum by $N\Pr(K\ge k_{max})\approx1$, obtaining $k_{max}\asymp N^{1/(\gamma-1)}$. The lecture’s substitution of $p(k_{max})$ gives the wrong exponent. For $\gamma=2.5$, the natural cutoff scales as $N^{2/3}$, and the truncated second moment as $N^{1/3}$. The source’s mass-based argument would incorrectly give $N^{2/5}$ and $N^{1/5}$.

In a sparse simple graph, keeping pairwise quantities $k_i k_j/(2L)$ small motivates a structural scale around $\sqrt N$ when the mean degree is bounded. The natural cutoff can exceed that scale for $2<\gamma<3$, signalling that an uncorrelated simple-graph approximation needs care. This does not forbid a simple graph from having a degree larger than $\sqrt N$.

To study a dataset, distinguish a degree histogram from a survival plot, indicate the fitted tail range, and compare alternative distributions. A straight-looking plot alone does not establish a power law.
