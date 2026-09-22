---
type: study-note
tags: [DATA5441]
---

# Maximum entropy and ERGMs

[[00_HOME]]

Sources: Week 6 and Tutorial 6. Newman provides random-graph context in Chapters 11–12; the supplied lecture is the primary derivation for this topic.

Choose a finite support $\Omega$. Maximise $-\sum_gp_g\log p_g$ subject to normalisation and expected statistics $\mathbb E[x_i]=x_i^*$. With Lagrangian
$$\mathcal J=-\sum_gp_g\log p_g+\alpha(\sum_gp_g-1)+\sum_i\beta_i(\sum_gp_gx_i(g)-x_i^*),$$
differentiation gives $-\log p_g-1+\alpha+\sum_i\beta_ix_i(g)=0$. Therefore
$$p_{\beta}(g)=e^{\beta\cdot x(g)}/Z(\beta).$$
The sign of $\beta$ is a convention fixed by the Lagrangian.

Differentiating the partition function gives
$$\nabla\log Z=\mathbb E_\beta[x],\qquad\nabla^2\log Z=\operatorname{Cov}_\beta(x).$$
For an observed graph $g^*$, the parameter log-likelihood is $\beta\cdot x(g^*)-\log Z$. Its score is $x(g^*)-\mathbb E_\beta[x]$. Hence interior maximum-likelihood fitting and moment matching coincide in this exponential family.

On all simple graphs, choosing $x=L$ gives $Z=(1+e^\beta)^Y$ and independent edges with $q=\operatorname{logistic}(\beta)$. On a fixed-degree space, $L$ is already constant, so the same statistic cannot alter the distribution. A clustering statistic can change weights within that constrained space.

Although $Z$ cancels when proposing graph moves at fixed $\beta$, it does **not** cancel when comparing different parameter values. Estimating moments by MCMC is one way to fit parameters without evaluating $Z$ directly.

A target proportional to $C(g)$ is not uniform in the scalar value $C$: many graphs can share one clustering value. Likewise $C(g)^{10}$ and $e^{\beta C(g)}$ are different families. The former excludes zero-clustering states; the latter assigns positive mass on a finite support for finite $\beta$.
