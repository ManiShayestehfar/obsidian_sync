---
tags: [data5441, ch05, models]
aliases: [Scale-free, Fat tails, Heavy tails, Natural cutoff]
---
# Power laws and fat tails

> [!abstract] Summary
> Many real degree distributions are broad: $P(z)\sim z^{-\gamma}$, usually with $2<\gamma<3$. Then the mean is finite but $\langle z^2\rangle$ diverges with $N$. This drives the absence of epidemic thresholds and robustness to random failure.
> Chapter: [[Ch05 Mechanistic models]]

> [!definition] Power-law (scale-free) degree distribution
> $P(z)\simeq Az^{-\gamma}$ for large $z$, with $\gamma>1$. The complementary cumulative distribution then satisfies $P_>(z)=\Pr(Z\ge z)\sim z^{-(\gamma-1)}$.
> On log–log axes the histogram has slope $-\gamma$ and the CCDF has slope $-(\gamma-1)$. Plot the CCDF: it is less noisy.

> [!theorem] Which moments are finite
> For an (infinite-support) power-law tail with exponent $\gamma$, the $n$-th moment $\langle z^n\rangle$ is finite iff $\gamma>n+1$.
> In particular, for $2<\gamma\le3$ the mean is finite and $\langle z^2\rangle=\infty$.

> [!proof]-
> Compare $\sum_z z^n z^{-\gamma}$ with $\int^\infty z^{n-\gamma}dz$, which converges iff $n-\gamma<-1$. Finitely many small-$z$ terms do not affect convergence. $\square$

> [!theorem] Natural cutoff (largest degree)
> In a sample of $N$ independent degrees, the largest degree $z_{max}$ is set by expecting about one node at or above it:
> $$N\,P_>(z_{max})\approx1\ \Longrightarrow\ z_{max}\sim N^{1/(\gamma-1)} .$$
> Consequently the finite-$N$ second moment grows: $\langle z^2\rangle\sim z_{max}^{3-\gamma}\sim N^{(3-\gamma)/(\gamma-1)}$ for $2<\gamma<3$.

> [!remark] Precision
> - Every finite graph has finite moments, since $z_i\le N-1$. "Diverging $\langle z^2\rangle$" means growth with $N$.
> - A straight-looking log–log plot is not proof of a power law. A broad (fat-tailed) distribution need not be a power law.

![[power-law-tails.png|600]]

> [!example] $\gamma=2.5$
> Here $z_{max}\sim N^{2/3}$ and $\langle z^2\rangle\sim N^{1/3}\to\infty$. Consequences:
> - $\langle z^2\rangle/\langle z\rangle\to\infty$, so the failure threshold $q_c\to1$ (see [[Percolation and robustness]]);
> - the SIR threshold $\lambda/\mu\to0$ (see [[SIR model and epidemic threshold]]).

> [!selftest]- Self-test
> 1. For $\gamma=2.5$, which moments are finite? — Only $\langle z\rangle$ (and $\langle z^0\rangle$).
> 2. What is the log–log slope of the CCDF? — $-(\gamma-1)$.

---
Related: [[Preferential attachment]] · [[Configuration model]] · [[Percolation and robustness]] · [[SIR model and epidemic threshold]]
