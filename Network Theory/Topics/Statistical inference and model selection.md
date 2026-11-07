---
tags: [data5441, ch07, inference]
aliases: [Bayesian inference, Model selection, Choosing B, Overfitting, Stirling numbers]
---
# Statistical inference and model selection

> [!abstract] Summary
> The best-fitting model is not the best model: an SBM with $B=N$ fits any graph perfectly. Bayesian model comparison penalises flexibility by counting, or integrating over, the many partitions and parameters a large $B$ allows.
> Chapter: [[Ch07 SBMs and statistical inference]]

> [!definition] Bayes' theorem for models
> For data $D$ (the observed graph), model $B$ and parameters $\theta$ (partition $\mathbf b$ and probabilities $P$),
> $$p(\theta,B\mid D)=\frac{p(D\mid\theta,B)\,p(\theta\mid B)\,p(B)}{p(D)} .$$
> - **Likelihood** $p(D\mid\theta,B)$: a function of $\theta$; it need not integrate to $1$ over $\theta$.
> - **MLE** maximises the likelihood. **MAP** maximises the posterior, so it includes the prior.
> - **Evidence:** $p(D\mid B)=\int p(D\mid\theta,B)p(\theta\mid B)d\theta$.

> [!theorem] Raw likelihood overfits
> With $B=N$ blocks, set $\hat p_{ij}=A_{ij}$. Then $P(A\mid\cdot)=1$ and $F=0$, the best possible. Maximum likelihood over $B$ therefore always prefers more blocks.

> [!definition] Counting partitions
> - $S(N,B)$ (Stirling number of the 2nd kind): partitions of $N$ labelled nodes into $B$ non-empty **unlabelled** blocks.
> - $B!\,S(N,B)$: surjective assignments to $B$ **labelled** blocks.
> - Bell number $\sum_BS(N,B)$: all partitions.
>
> The count $B^N$ includes empty blocks.

> [!theorem] Stirling recurrence
> $$S(N,B)=B\,S(N-1,B)+S(N-1,B-1),\qquad S(0,0)=1,\ S(N,0)=0\ (N>0),\qquad S(N,2)=2^{N-1}-1 .$$

> [!proof]-
> Consider node $N$. Either it joins one of the $B$ blocks of a partition of the other $N-1$ nodes into $B$ blocks ($B\,S(N-1,B)$ ways), or it forms a block alone, with the others partitioned into $B-1$ blocks ($S(N-1,B-1)$ ways).
> For $B=2$: there are $2^N-2$ non-trivial binary labellings, and swapping the labels identifies them in pairs, giving $2^{N-1}-1$. $\square$
>
> For Karate Club ($N=34$): $S(34,2)=2^{33}-1\approx8.6\times10^9$, so exhaustive search is impossible.

> [!definition] Penalised objective (tutorial 7)
> With a uniform prior $p(B)=1/N$ and uniform labelled partitions $1/[B!\,S(N,B)]$, select $B$ by minimising
> $$F(\hat{\mathbf b})+\ln\big[B!\,S(N,B)\big].$$
> The counting term grows with $B$ and penalises complexity. This is an approximation: it optimises over $\mathbf b$ and $P$ instead of integrating, so it is not the exact evidence.

> [!proposition] Integrating out $p_{rs}$
> With independent Beta$(a,b)$ priors on each $p_{rs}$,
> $$p(A\mid\mathbf b,B)=\prod_{r\le s}\frac{\mathrm B(l_{rs}+a,\ y_{rs}-l_{rs}+b)}{\mathrm B(a,b)} .$$
> This follows from $\int_0^1p^{l}(1-p)^{y-l}\dfrac{p^{a-1}(1-p)^{b-1}}{\mathrm B(a,b)}dp$.

> [!remark] Variational inference (background)
> Approximate the posterior by a tractable $q$ by maximising the ELBO, $\ln p(D)=\text{ELBO}(q)+\mathrm{KL}(q\,\|\,p(\theta\mid D))$, with $\mathrm{KL}\ge0$.

> [!selftest]- Self-test
> 1. Why can't we pick $B$ by maximum likelihood? — $B=N$ always wins.
> 2. What does $\ln[B!S(N,B)]$ represent? — The description length of the partition under a uniform prior.

---
Related: [[Stochastic block models]] · [[Community detection]] · [[Link prediction]]
