---
type: lecture-export
week: 7
source_pages: 16
status: visually-checked-paraphrase
tags: [DATA5441, lecture]
---

# Week 7 - Block models and network inference

[[00_HOME]] · [[Tutorial 7 - guide]] · [[Newman reading map]] · [[Corrections and caveats]]

Source: `Notes Week 7 - 2026.pdf`; page numbers below refer to this supplied PDF.

Page-by-page mathematical transcription and paraphrase of the supplied handwritten lecture. Equations have been typeset; diagrams and the complete original page are retained in each image. Added explanations, corrections and ambiguities are identified in the text. This is not a verbatim diplomatic transcription.

## Page 01 - Mesoscale structure

Degree describes individual vertices; global mean distance and clustering summarise an entire network. Mesoscale structure concerns groups between these levels. Communities have comparatively strong internal connections. The lecture uses the Karate Club and political-blog networks to motivate detecting groups from edges rather than assuming labels in advance.

> [!example]- Original page 1
> ![[w7-p01.jpg]]

## Page 02 - Core–periphery structure

A core can be densely interconnected and well connected to a sparse periphery. This differs from two assortative communities: peripheral vertices may connect mainly to the core rather than to one another. A block model can express both patterns through its probability matrix.

> [!example]- Original page 2
> ![[w7-p02.jpg]]

## Page 03 - Stochastic block model

Partition $N$ labelled vertices into $B$ nonempty groups. Write $b_i\in\{1,\ldots,B\}$ for the group of vertex $i$, and $n_r$ for group sizes. Given the allocation and a symmetric matrix $p_{rs}$, distinct dyads are independent:
$$A_{ij}\mid\mathbf b,p\sim\operatorname{Bernoulli}(p_{b_i b_j}),\qquad i<j.$$
The source’s set-membership notation is interpreted as membership, not subset inclusion. With $B=1$ this is ER. With $B=2$ and $p_{11}=p_{22}=0$, it is a random bipartite graph.

> [!example]- Original page 3
> ![[w7-p03.jpg]]

## Page 04 - Patterns in the block matrix

Large diagonal probabilities and small off-diagonal probabilities encode assortative groups. In a two-group core–periphery example, $p_{11}>p_{12}>p_{22}$ makes group one the core. The model does not force communities: the pattern depends on the fitted probability matrix.

> [!example]- Original page 4
> ![[w7-p04.jpg]]

## Page 05 - Likelihood and Bayes’ rule

For data $D$ and model or parameters $M$,
$$P(M\mid D)=\frac{P(D\mid M)P(M)}{P(D)}.$$
The likelihood $P(D\mid M)$ is a function of $M$ after observing $D$; it need not sum or integrate to one over $M$. Maximum likelihood maximises it. Maximum a posteriori estimation also includes the prior. The evidence normalises the posterior and compares model families only when parameters are appropriately integrated or summed out.

> [!example]- Original page 5
> ![[w7-p05.jpg]]

## Page 06 - Likelihood of a particular graph

For an observed simple graph $A$,
$$\mathcal L(\mathbf b,p;A)=\prod_{i<j}p_{b_i b_j}^{A_{ij}}(1-p_{b_i b_j})^{1-A_{ij}}.$$
The independent observations conditional on parameters are the $Y=\binom N2$ possible dyads, including non-edges, not just the $L$ edges. There is no binomial coefficient in the probability of this particular labelled graph. A coefficient would appear if the data were only aggregated edge counts.

> [!example]- Original page 6
> ![[w7-p06.jpg]]

## Page 07 - Estimating block probabilities

For $r<s$, let $y_{rs}=n_rn_s$; for $r=s$, let $y_{rr}=\binom{n_r}{2}$. Let $l_{rs}$ count observed edges in the corresponding block pair, counting within-group edges once. Then
$$\log\mathcal L=\sum_{r\le s}\{l_{rs}\log p_{rs}+(y_{rs}-l_{rs})\log(1-p_{rs})\},$$
and, when $y_{rs}>0$,
$$\widehat p_{rs}=\frac{l_{rs}}{y_{rs}}.$$
Values zero and one are valid boundary estimates; use the convention $0\log0=0$. If $y_{rs}=0$, there are no dyads and $p_{rs}$ is not identified by the graph.

> [!example]- Original page 7
> ![[w7-p07.jpg]]

## Page 08 - Optimising the partition is hard

Define the profile negative log-likelihood
$$F(\mathbf b)=-\log\mathcal L(\mathbf b,\widehat p(\mathbf b);A).$$
The minus sign applies to the whole log-likelihood sum. Minimising $F$ is equivalent to maximising the profiled likelihood.

There are $S(N,B)$ partitions into $B$ nonempty unlabelled groups, where $S$ is a Stirling number of the second kind. There are $B!S(N,B)$ surjective allocations to labelled groups. Summing $S(N,B)$ over $B$ gives the Bell number. $B^N/B!$ is not an exact count of nonempty partitions because it includes assignments with missing labels before division. Enumeration rapidly becomes impractical.

> [!example]- Original page 8
> ![[w7-p08.jpg]]

## Page 09 - What an ordinary SBM may discover

A supplied Karate Club example compares the known split with random and alternative allocations. A split between high-degree and low-degree vertices can score well under the ordinary SBM because vertices in the same block have the same expected connection pattern. Do not assume the best likelihood recovers the social labels.

Degree correction adds vertex-specific propensities. Newman’s common formulation is Poisson, with expected edge multiplicity proportional to $\theta_i\theta_j\omega_{b_i b_j}$. This quantity is an intensity, not automatically a Bernoulli probability. A raw product such as $z_i z_j\lambda_{rs}$ can exceed one and must not silently be used as a probability. The course’s basic SBM above is Bernoulli.

> [!example]- Original page 9
> ![[w7-p09.jpg]]

## Page 10 - Greedy optimisation

Start from an allocation. Evaluate permitted one-vertex group changes, accept an improvement, and continue until no allowed change strictly improves $F$. Keep groups nonempty if that is the chosen state space. The result is a local optimum with respect to those moves, not a certificate of global optimality. Multiple random starts help reveal different optima. The lecture mentions other inference approaches but does not derive them here.

> [!example]- Original page 10
> ![[w7-p10.jpg]]

## Page 11 - MCMC on allocations

A symmetric proposal selects a vertex and a different group uniformly. With a target proportional to the profile likelihood, the acceptance probability is
$$a(\mathbf b,\mathbf b')=\min\{1,e^{-\Delta F}\},\qquad\Delta F=F(\mathbf b')-F(\mathbf b).$$
Better moves have $\Delta F<0$ and are accepted. Invalid moves that empty a required group should be rejected while retaining the current state. See [[SBM inference and model selection]].

> [!example]- Original page 11
> ![[w7-p11.jpg]]

## Page 12 - Temperature parameter

A tempered target $\pi_\beta(\mathbf b)\propto e^{-\beta F(\mathbf b)}$ gives acceptance $\min\{1,e^{-\beta\Delta F}\}$. At $\beta=0$, every valid proposal is accepted. At $\beta=1$, it samples the specified likelihood-weighted allocation target. As $\beta\to\infty$, only moves with $\Delta F\le0$ are accepted, including ties.

This finite-state target is mathematically well defined. When $F$ uses fitted block probabilities, it is a profile-likelihood target; it is not automatically the Bayesian posterior obtained by integrating uncertain block probabilities.

> [!example]- Original page 12
> ![[w7-p12.jpg]]

## Page 13 - Local barriers and simulated annealing

Greedy search cannot cross a barrier requiring a temporary increase in $F$. Finite-temperature Metropolis moves can. Simulated annealing progressively increases $\beta$ to reduce the probability of worse moves. A finite practical cooling schedule does not guarantee the global optimum. Record the schedule, starts and best values; distinguish optimisation from sampling a fixed target.

> [!example]- Original page 13
> ![[w7-p13.jpg]]

## Page 14 - Choosing the number of groups

Unpenalised maximum likelihood favours excessive flexibility. If each vertex has its own group ($B=N$), every dyad can be fitted exactly with $p_{ij}=A_{ij}$, giving likelihood one and $F=0$. Thus minimising the fitted $F$ over $B$ cannot provide a sensible complexity trade-off by itself.

Bayes’ rule in logs is
$$\log P(M\mid D)=\log P(D\mid M)+\log P(M)-\log P(D).$$
The evidence term has a minus sign. The page’s sign should not be carried into a normalised posterior formula.

> [!example]- Original page 14
> ![[w7-p14.jpg]]

## Page 15 - A prior over partitions

The lecture takes a uniform prior on $B\in\{1,\ldots,N\}$ and a uniform allocation conditional on $B$. For **labelled nonempty allocations**,
$$P(B)=1/N,\qquad P(\mathbf b\mid B)=\frac1{B!S(N,B)}.$$
Combining this with the profile likelihood produces the proxy score
$$F(\mathbf b)+\log[B!S(N,B)]+\log N.$$
If using unlabelled partitions instead, the count is $S(N,B)$: the state space and prior must agree. This counting penalty need not increase monotonically all the way to $B=N$. A maximum joint score and a marginal posterior for $B$ are different quantities.

> [!example]- Original page 15
> ![[w7-p15.jpg]]

## Page 16 - Interpreting the tutorial’s model-selection plot

The illustrated tutorial calculation compares optimised penalised scores across $B$ and finds a preferred value around three for its example. Treat this as the output of that heuristic and its runs, not a universal ground truth.

A full Bayesian calculation instead has the structure
$$P(B\mid A)\propto P(B)\sum_{\mathbf b}P(\mathbf b\mid B)\int P(A\mid\mathbf b,p)P(p\mid B)\,dp.$$
Replacing the integral by maximisation over $p$, and replacing the sum by the best allocation, changes the calculation. The notebook’s profile-likelihood optimisation plus counting prior is useful to study but is not exact Bayesian evidence. See [[Tutorial 7 - guide]] and [[Corrections and caveats]].

> [!example]- Original page 16
> ![[w7-p16.jpg]]

