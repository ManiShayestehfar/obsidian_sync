---
tags: [data5441, ch06, models]
aliases: [ERGM, Exponential random graph model, Maximum entropy, Partition function]
---
# Maximum entropy and ERGMs

> [!abstract] Summary
> To build a random graph that matches chosen statistics **on average** while assuming nothing else, maximise entropy subject to those constraints. The answer is the exponential random graph model $p(g)=e^{\beta\cdot x(g)}/Z$. ER is the ERGM of $L$. ERGMs are sampled with Metropolis–Hastings.
> Chapter: [[Ch06 ERGMs and Metropolis–Hastings]]

> [!definition] Maximum-entropy problem
> On a graph space $\Omega$, choose $p(g)\ge0$ to maximise $S[p]=-\sum_gp(g)\ln p(g)$ subject to
> $$\sum_gp(g)=1,\qquad\sum_gp(g)\,x_a(g)=x_a^*\quad(a=1,\dots,m),$$
> where the $x_a$ are graph statistics (e.g. $L$, $T$, $C$) and $x_a^*$ their observed values.

> [!theorem] ERGM form
> The maximiser is
> $$p_\beta(g)=\frac{e^{\beta\cdot x(g)}}{Z(\beta)},\qquad Z(\beta)=\sum_{h\in\Omega}e^{\beta\cdot x(h)},$$
> with $\beta$ chosen so that $\langle x_a\rangle_\beta=x_a^*$.

> [!proof]-
> Form the Lagrangian $\mathcal F=-\sum_gp_g\ln p_g+\alpha\big(\sum_gp_g-1\big)+\sum_a\beta_a\big(\sum_gp_gx_a(g)-x_a^*\big)$.
> Setting $\partial\mathcal F/\partial p_g=-\ln p_g-1+\alpha+\beta\cdot x(g)=0$ gives $p_g=e^{\alpha-1}e^{\beta\cdot x(g)}$. Normalisation fixes $e^{1-\alpha}=Z$.
> $S$ is strictly concave and the constraints are linear, so this stationary point is the unique maximum. $\square$

> [!theorem] Moments from $\log Z$
> $$\frac{\partial\ln Z}{\partial\beta_a}=\langle x_a\rangle_\beta,\qquad\frac{\partial^2\ln Z}{\partial\beta_a\partial\beta_b}=\operatorname{Cov}_\beta(x_a,x_b).$$
> Hence $\langle x\rangle_\beta$ is non-decreasing in $\beta$ (one statistic). The maximum-likelihood $\beta$ for one observed graph $g^*$ solves $\langle x\rangle_\beta=x(g^*)$, i.e. moment matching.

> [!proof]-
> Differentiate $Z=\sum_ge^{\beta\cdot x(g)}$: $\partial_aZ=\sum_gx_a(g)e^{\beta\cdot x(g)}$, so $\partial_a\ln Z=\langle x_a\rangle$. Differentiating again gives $\langle x_ax_b\rangle-\langle x_a\rangle\langle x_b\rangle$.
> The log-likelihood is $\ell(\beta)=\beta\cdot x(g^*)-\ln Z$, with gradient $x(g^*)-\langle x\rangle_\beta$. $\square$

> [!example] ER is the ERGM of the link count
> With $x(g)=L(g)$ on $\Omega_N$: $Z=\sum_g e^{\beta L(g)}=(1+e^\beta)^Y$, since the pairs factorise. So
> $$p(g)=\frac{e^{\beta L}}{(1+e^\beta)^Y}=p^L(1-p)^{Y-L},\qquad p=\frac{e^\beta}{1+e^\beta}.$$
> This is $G(N,p)$. If $L$ is already fixed by the space (on $\Omega_{N,L}$), the factor $e^{\beta L}$ is constant and has no effect.

> [!definition] Hard vs soft constraints
> - **Hard:** restrict $\Omega$ (e.g. $\Omega_{N,L}$, fixed degrees). Every sampled graph matches exactly.
> - **Soft:** ERGM weights. The constraint holds only on average.

> [!example] Clustering-biased ensemble (Trial Exam 1, Q7)
> On $\Omega_{N,L}$ with $N=24$, $L=48$: $Y=276$ and $|\Omega_{N,L}|=\binom{276}{48}$. Let $p_\beta(g)=e^{\beta T(g)}/Z_\beta$.
> - At $\beta=0$ the law is uniform on $\Omega_{N,L}$.
> - $\beta>0$ favours triangles (higher clustering).
> - Sample it with edge replacement and $A=\min\{1,e^{\beta\Delta T}\}$; see [[Metropolis–Hastings]].

> [!remark] Tutorial 6 (November 17 network)
> Fix the degrees, add a clustering weight, and fit expected clustering. Then compare a **different** statistic (maximum betweenness) between data and model samples. The tutorial's weights $\propto C$ and $\propto C^{10}$ are not of exponential form; they assign zero probability to graphs with $C=0$.

> [!selftest]- Self-test
> 1. Derive $p(g)\propto e^{\beta\cdot x}$ from maximum entropy.
> 2. Why does $Z$ cancel for MH moves but not when comparing different $\beta$? — It depends on $\beta$, not on $g$.
> 3. Which ERGM is ER? — $x=L$ on $\Omega_N$.

---
Related: [[Metropolis–Hastings]] · [[Random graph ensembles]] · [[Clustering]] · [[Reconstruction from node activity]]
