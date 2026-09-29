---
tags: [inference]
---

# Statistical inference and model selection

Network inference must distinguish observed data, latent structure and fitted parameters. In graph-space MCMC the graph is random; in block-allocation MCMC the observed graph is fixed and the labels are random.

> [!definition] Likelihood, posterior and evidence
> For observed data $D$, model index $B$ and parameters $\theta$,
> $$p(\theta,B\mid D)=\frac{p(D\mid\theta,B)p(\theta\mid B)p(B)}{p(D)}.$$
> The likelihood is a function of parameters with data fixed; it need not integrate to one over parameters. Maximum likelihood maximises $p(D\mid\theta,B)$; MAP also includes the prior. Evidence integrates over parameters, $p(D\mid B)=\int p(D\mid\theta,B)p(\theta\mid B)\,d\theta$.

Taking logarithms gives **minus** log evidence in log posterior. Changing a continuous parameterisation changes density values, so MAP depends on the parameterisation and reference measure.

## How many partitions?
There are $S(N,B)$ partitions into $B$ nonempty unlabelled groups, and $B!S(N,B)$ surjective assignments to $B$ labelled groups. The Bell number $\sum_BS(N,B)$ counts all unlabelled partitions. $B^N$ includes empty groups and $B^N/B!$ is not the exact count.

> [!proof] Stirling recurrence
> Place vertex $N$ into one of the $B$ existing groups of a partition of $N-1$ vertices, or place it alone after partitioning the others into $B-1$ groups:
> $$S(N,B)=B S(N-1,B)+S(N-1,B-1).$$
> Use $S(0,0)=1$, $S(N,0)=0$ for $N>0$, and zero outside $0\le B\le N$. For two groups, nontrivial binary assignments pair under label exchange, so $S(N,2)=2^{N-1}-1$; at $N=34$ this is $8{,}589{,}934{,}591$.

> [!warning] Best fit is not evidence
> In the Bernoulli SBM, $B=N$ fits every dyad with $p_{ij}=A_{ij}$, giving likelihood one and profile negative log-likelihood zero. Raw best fit therefore favours excess flexibility.
>
> With uniform $p(B)=1/N$ and uniform nonempty **labelled** allocations, the tutorial uses the proxy $F(b)+\log[B!S(N,B)]$ and minimises over $b$. It replaces both integration over probabilities and summation over allocations by optimisation. It is not exact Bayesian evidence. The counting penalty is not monotone across all $B$.

For unlabelled partitions the uniform conditional prior is $1/S(N,B)$ instead. These are different prior specifications on different state spaces; keep labels and their multiplicities consistent. At fixed $B$, optimising the proxy is the same as optimising $F$ because its counting term is constant.

> [!theorem] Integrating SBM probabilities
> With independent Beta$(a,b)$ priors, $a,b>0$, on block probabilities, the integrated probability of a particular graph at fixed allocation is
> $$p(A\mid\mathbf b,B)=\prod_{r\le s}\frac{\mathrm B(l_{rs}+a,y_{rs}-l_{rs}+b)}{\mathrm B(a,b)}.$$
> Multiply the Bernoulli factors by the Beta density and integrate each $p_{rs}$ over $[0,1]$ to obtain this identity. Full evidence still sums over allocations; no binomial coefficient is inserted for a particular graph.

> [!code] Count partitions without overflowing intermediate floats
> ```python
> import math
>
> def stirling_second(n, k):
>     if n < 0 or k < 0:
>         raise ValueError('n and k must be nonnegative')
>     row = [0] * (k + 1)
>     row[0] = 1
>     for _ in range(n):
>         row = [0] + [j * row[j] + row[j-1] for j in range(1, k+1)]
>     return row[k]
>
> N, B = 34, 2
> count = stirling_second(N, B)
> log_counting_penalty = math.lgamma(B + 1) + math.log(count)
> print(count, log_counting_penalty)
> ```

## Variational inference
Choose a tractable family $q(\theta)$ and minimise $\mathrm{KL}(q\|p(\theta\mid D))$, where
$$\mathrm{KL}(q\|p)=\mathbb E_q[\log q-\log p]\ge0,$$
assuming $q$ is absolutely continuous with respect to $p$. The identity
$$\log p(D)=\underbrace{\mathbb E_q[\log p(D,\theta)-\log q(\theta)]}_{\mathrm{ELBO}}+\mathrm{KL}(q\|p(\theta\mid D))$$
shows that maximising the evidence lower bound is equivalent. A mean-field family factors across parameter groups; this is an approximation to posterior dependence, not a fact about the true parameters. The student notes’ KL comparison to an unnormalised likelihood is not the correct posterior objective.

Sampling, optimisation and approximation answer different questions. A local optimum or short annealing run is not proof of a global optimum; a good in-sample score is not a held-out prediction result. See [[Stochastic block models]] and [[Network reconstruction]].

> [!reference]- Sources
> Lecture Week 7; Jenny’s notes Weeks 7–9. Tutorial 7, model-comparison discussion and explicit evidence qualification. Newman §14.4. Beta integration, Stirling proof and ELBO identity are explanatory derivations of the stated models.
