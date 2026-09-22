---
type: study-note
tags: [DATA5441]
---

# Tutorial 6 - guide

[[00_HOME]]

[[Tutorial 6 - source export]]


Read [[MCMC and detailed balance]] and [[Maximum entropy and ERGMs]].

| Exercise / source cells | Target or task | Analytic / conceptual check |
| --- | --- | --- |
| 1.1, 14 | Sample $p(x)=2x$ on $[0,1]$ with a narrow periodic proposal | Small proposals can yield high acceptance but slow mixing |
| 1.2, 15 | Estimate the mean | $\mathbb E[X]=\int_0^1 2x^2dx=2/3$ |
| 1.3, 17 | Change unnormalised target | $3x$ normalises to $2x$; $x^2$ normalises to $3x^2$ with mean $3/4$ |
| 2.1, 22 onwards | Degree-four graphs on 50 nodes, weighted by $1$, $C$ or $C^{10}$ | The target is over graphs, not uniformly over possible $C$ values |
| 3.1, 43 onwards | Fit a clustering ERGM on the November 17 degree sequence | Match mean clustering, then compare maximum betweenness |

For $p(x)\propto x$, acceptance between positive points is $\min(1,x'/x)$. The multiplying constant cancels. Proposing near a boundary by wrapping on a circle is different from clipping an interval proposal; clipping may create atoms or asymmetry. Derive the actual proposal rather than assuming all “local moves” are symmetric.

For the regular-graph example, clustering one is possible without connectivity: ten disjoint complete graphs $K_5$ have 50 vertices, degree four and clustering one. A target proportional to $C$ or $C^{10}$ excludes all zero-clustering graphs, so initialise in its support and examine whether the allowed moves connect the support.

Week 6 cell 42 supplies a single-attempt degree-preserving proposal; invalid attempts return the same graph. This supports an exact symmetric proposal argument. Cell 41 claims the successful-swap correction is small for the considered families; no quantified bound is supplied, so do not treat that magnitude claim as established.

For the fitted ERGM: choose a grid of $\beta$, run chains, estimate $\mathbb E_\beta[C]$ with uncertainty, refine around the observed $C$, then simulate again at the fitted value. Comparing observed maximum betweenness requires taking the maximum over vertices in every sampled graph. A fitted clustering constraint is in expectation; individual sampled graphs need not have exactly the observed clustering.


The cell references above use one-based notebook order, matching the source-export headings. These guides provide derivations and checks; the full long-running notebooks were not re-executed when preparing this vault.
