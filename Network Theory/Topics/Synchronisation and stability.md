---
tags: [data5441, ch12, dynamics]
aliases: [Synchronisation, Kuramoto model, Linear stability, Diffusion on networks, Consensus]
---
# Synchronisation and stability

> [!abstract] Summary
> For continuous dynamics coupled through links, linearising about a homogeneous fixed point decouples the perturbation into **Laplacian eigenmodes**. Each mode $r$ grows or decays at rate $a-b\lambda_r$. Diffusion converges to the average. Kuramoto oscillators synchronise when coupling dominates.
> Chapter: [[Ch12 Epidemics and games on networks]]

> [!warning] Source
> Covered in 2026 lectures, but there is no written page in the 2026 lecture-notes PDF. This note is based on Jeny's notes from the previous year. Check notation against your own lecture recording or slides.

> [!definition] Coupled dynamics on a network
> Each node $i$ carries a state $x_i(t)$ obeying
> $$\dot x_i=f(x_i)+\sum_jA_{ij}\,g(x_i,x_j).$$
> If $f(x^*)=0$ and $g(x^*,x^*)=0$, then $x_i\equiv x^*$ is a homogeneous fixed point.

> [!theorem] Linear stability via the Laplacian
> Let $g(x,y)=\beta[h(y)-h(x)]$ with $\beta\ge0$, and set $a=f'(x^*)$, $b=\beta h'(x^*)$. Perturbations $\epsilon_i=x_i-x^*$ satisfy, to first order,
> $$\dot\epsilon=(aI-b\mathbf L)\epsilon,\qquad\mathbf L=D-A .$$
> In the eigenbasis of $\mathbf L$ (eigenvalues $\lambda_r$), $c_r(t)=c_r(0)e^{(a-b\lambda_r)t}$. The fixed point is locally asymptotically stable if $a-b\lambda_r<0$ for **all** $r$, and unstable if any rate is $>0$.

> [!proof]-
> Taylor expansion gives $f(x^*+\epsilon_i)\approx a\epsilon_i$ and $g(x^*+\epsilon_i,x^*+\epsilon_j)\approx b(\epsilon_j-\epsilon_i)$. Then $\sum_jA_{ij}(\epsilon_j-\epsilon_i)=-(\mathbf L\epsilon)_i$.
> $\mathbf L$ is symmetric, so it has an orthonormal eigenbasis $\{v_r\}$. Writing $\epsilon=\sum_rc_rv_r$ decouples the system into $\dot c_r=(a-b\lambda_r)c_r$. $\square$
> Since $\lambda_1=0$, mode $1$ (uniform shift) has rate $a$. Stability needs $a<0$ **and** $a-b\lambda_N<0$, the latter automatic when $b\ge0$.

> [!theorem] Diffusion / consensus
> For $\dot x=-\beta\mathbf Lx$ with $\beta>0$ on a connected graph,
> $$x(t)\to\Big(\frac1N\sum_ix_i(0)\Big)\mathbf1,$$
> with slowest decay rate $\beta\lambda_2$. The mean is conserved because $\mathbf1^\top\mathbf L=0$.

![[diffusion-to-consensus.png|600]]

> [!definition] Kuramoto model
> $$\dot\theta_i=\omega_i+K\sum_jA_{ij}\sin(\theta_j-\theta_i),\qquad re^{\mathrm i\psi}=\frac1N\sum_je^{\mathrm i\theta_j}.$$
> The order parameter $r\in[0,1]$ satisfies $r=1$ iff all phases coincide. For independent uniform phases, $\mathbb E[r^2]=1/N$, so $r$ is small but non-zero when incoherent.

> [!proposition] Identical oscillators
> If $\omega_i=\omega$, work in the rotating frame. Near synchrony $\sin(\theta_j-\theta_i)\approx\theta_j-\theta_i$, so $\dot\delta=-K\mathbf L\delta$. On a connected graph all non-uniform modes decay (rate $\ge K\lambda_2$), and the synchronous state is stable up to a global phase shift.

> [!selftest]- Self-test
> 1. Derive $\dot\epsilon=(aI-b\mathbf L)\epsilon$.
> 2. Which eigenvalue sets the convergence speed of diffusion? — $\lambda_2$.
> 3. What is $r$ for perfect synchrony? — $1$.

---
Related: [[Spectral graph theory]] · [[Binary-state dynamics]]
