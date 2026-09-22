---
type: study-note
tags: [DATA5441]
---

# Sampling and friendship paradox

[[00_HOME]]

Sources: Weeks 1–2; Tutorial 1; Newman §§7.2, 12.2. State the sampling experiment before computing an expectation.

For a uniformly chosen vertex, degree has distribution $p_k$ and mean $\langle k\rangle$. For the endpoint of a uniformly chosen oriented edge,
$$\Pr(K=k)=\frac{kp_k}{\langle k\rangle},\qquad \mathbb E[K]=\frac{\langle k^2\rangle}{\langle k\rangle}=\langle k\rangle+\frac{\operatorname{Var}(k)}{\langle k\rangle}.$$
This is degree-biased sampling. Equality with the vertex mean holds for a regular graph.

Tutorial 1 instead first chooses a vertex uniformly and then chooses one of its neighbours uniformly. If all vertices have positive degree, the probability of returning $j$ is
$$\Pr(J=j)=\frac1N\sum_{i\sim j}\frac1{k_i}.$$
This is generally not $k_j/(2L)$. Its mean neighbour degree is
$$\frac1N\sum_{\{i,j\}\in E}\left(\frac{k_j}{k_i}+\frac{k_i}{k_j}\right)\ge\frac{2L}{N}.$$
The inequality follows from $a/b+b/a\ge2$. Isolated vertices require a rule for failed neighbour selections. Neither average statement says that every individual has lower degree than their own neighbours.

**Worked contrast:** for a star with $N$ vertices, random-edge endpoint mean degree is $N/2$. Uniform-vertex-then-neighbour mean degree is $[(N-1)^2+1]/N$. These differ sharply; both exceed the uniform-vertex mean $2(N-1)/N$ for $N>2$.

For independent observations, the standard error of a sample mean is estimated by $s/\sqrt R$. Sampling without replacement introduces finite-population correction; MCMC introduces autocorrelation. Averaging a sequence of running means does not recover the final sample mean.
