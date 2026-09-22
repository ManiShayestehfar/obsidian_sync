---
type: study-note
tags: [DATA5441]
---

# SBM inference and model selection

[[00_HOME]]

Sources: Week 7; Tutorial 7; Newman §14.4. The course starts from a Bernoulli SBM; the textbook also uses Poisson and degree-corrected formulations. Do not interchange their likelihoods.

For known allocation $b$, count $l_{rs}$ edges among $y_{rs}$ possible dyads, where $y_{rr}=n_r(n_r-1)/2$ and $y_{rs}=n_rn_s$ for $r<s$. Maximise
$$\ell(b,p)=\sum_{r\le s}[l_{rs}\log p_{rs}+(y_{rs}-l_{rs})\log(1-p_{rs})]$$
to obtain $\widehat p_{rs}=l_{rs}/y_{rs}$. There are no combinatorial coefficients because the observation is a particular graph. When $y=0$ the block-pair contributes zero and its parameter is unidentified.

**Worked block pair:** $n_1=3,n_2=2$, with $l_{11}=2,l_{12}=1,l_{22}=0$. Then $\widehat p_{11}=2/3$, $\widehat p_{12}=1/6$ and $\widehat p_{22}=0$. The fitted negative log-likelihood is
$$-[2\log(2/3)+\log(1/3)+\log(1/6)+5\log(5/6)]\approx4.6129.$$
The last within-group non-edge contributes $\log1=0$.

For two groups there are $S(N,2)=2^{N-1}-1$ unlabelled nonempty partitions. Greedy moves find a local minimum of $F=-\ell(b,\widehat p)$; Metropolis with $\min(1,e^{-\beta\Delta F})$ can cross uphill barriers. Neither a short run nor a single greedy start certifies a global optimum.

At $B=N$, every dyad can be fitted independently and $F=0$. Comparing raw maximum likelihood across $B$ therefore overfits. The tutorial uses $F+\log[B!S(N,B)]$ for labelled nonempty allocations, with a uniform prior on $B$. This is a best-partition profile-likelihood score. It is not the full evidence, which sums over allocations and integrates block probabilities.

**Added textbook-style Bayesian extension:** with independent Beta$(a,b)$ priors on block probabilities, each block pair contributes
$$\frac{\mathrm B(l_{rs}+a,y_{rs}-l_{rs}+b)}{\mathrm B(a,b)}$$
to the graph’s integrated likelihood at fixed allocation. The sum over allocations still remains. This formula follows by integrating the Bernoulli likelihood against the Beta density; it does not require adding a binomial coefficient.

When comparing two allocations, account for label permutations. In the binary case the number of changed memberships is $\min(d,N-d)$, where $d$ is the raw Hamming distance. A visual mismatch of colours need not be a different partition.
