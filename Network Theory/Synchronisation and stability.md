---
tags: [dynamics]
---

# Synchronisation and stability

> [!definition] Coupled dynamics
> Associate a state $x_i(t)\in\mathbb R^d$ with each vertex:
> $$\dot x_i=f_i(x_i)+\sum_jA_{ij}g_{ij}(x_i,x_j).$$
> For identical scalar dynamics use $f_i=f$ and $g_{ij}=g$. If $f(x^*)=0$ and $g(x^*,x^*)=0$, the homogeneous configuration $x_i=x^*$ is a fixed point.

## Laplacian linearisation
Suppose $g(x,y)=\beta[h(y)-h(x)]$, where $\beta\ge0$ and $f,h$ are continuously differentiable near $x^*$. Put $a=f'(x^*)$, $b=\beta h'(x^*)$ and $\mathcal L=D-A$.

> [!theorem] Linear modes and local stability
> The linearised perturbation satisfies
> $$\dot\epsilon=(aI-b\mathcal L)\epsilon.$$
> On an undirected graph its modal rates are $a-b\lambda_r$. If all are strictly negative, the nonlinear fixed point is locally asymptotically stable. A positive rate implies instability; zero real parts require further nonlinear analysis.

> [!proof]
> Taylor expansion gives $f(x^*+\epsilon_i)=a\epsilon_i+o(|\epsilon_i|)$ and coupling $b(\epsilon_j-\epsilon_i)$ at first order. Summing produces $-b\mathcal L\epsilon$. In an orthonormal Laplacian eigenbasis each mode obeys $\dot c_r=(a-b\lambda_r)c_r$, hence $c_r(t)=c_r(0)e^{(a-b\lambda_r)t}$. The strict-sign conclusions for the nonlinear system follow from the linearisation theorem.

If the coupling is instead $g(x,y)=h(x)-h(y)$, the matrix is $aI+h'(x^*)\mathcal L$. Use its **plus** sign consistently and require all $a+h'(x^*)\lambda_r<0$ for strict linear stability. The source mixes this convention with the opposite eigenvalue sign.

## Diffusion
For $\dot x=-\beta\mathcal Lx$ with $\beta>0$, the mean is conserved because $\mathbf1^\top\mathcal L=0$. On a connected undirected graph, positive modes decay and the zero mode remains:
$$x(t)\longrightarrow\left(N^{-1}\sum_i x_i(0)\right)\mathbf1.$$
The slowest nonconstant decay rate is $\beta\lambda_2$. This is convergence to a manifold of equilibria, not asymptotic stability of one predetermined constant vector against mean-changing perturbations.

## Phase synchronisation
> [!definition] Kuramoto convention
> For phases modulo $2\pi$, intrinsic frequencies $\omega_i$ and attractive coupling $K>0$, use
> $$\dot\theta_i=\omega_i+K\sum_jA_{ij}\sin(\theta_j-\theta_i),\qquad re^{\mathrm i\psi}=\frac1N\sum_je^{\mathrm i\theta_j}.$$
> Then $0\le r\le1$ and $r=1$ exactly when all phases agree modulo $2\pi$. Normalising the coupling by $N$, degree or mean degree defines different parameter conventions. The reversed sine sign is repulsive for positive $K$.

For independent **uniform** phases, $\mathbb E[r^2]=1/N$: expanding $N^{-2}\sum_{ij}e^{\mathrm i(\theta_i-\theta_j)}$ leaves only diagonal terms. Thus a finite incoherent configuration does not have exactly zero order parameter, and independence without uniformity is insufficient.

With identical frequencies, pass to a rotating frame. Near equal phases, $\sin(\theta_j-\theta_i)\approx\theta_j-\theta_i$, giving $\dot\delta=-K\mathcal L\delta$: nonconstant modes decay on a connected graph. A global phase shift is a neutral mode. Heterogeneous frequencies, global basins and onset thresholds require additional assumptions; no universal degree-moment threshold is asserted here.

> [!code] Integrate phases and compute coherence
> ```python
> import networkx as nx
> import numpy as np
> from scipy.integrate import solve_ivp
>
> G = nx.cycle_graph(12)
> A = nx.to_numpy_array(G, weight=None)
> rng = np.random.default_rng(5441)
> initial = rng.normal(0.0, 0.1, len(G))  # near synchrony
> omega, K = np.zeros(len(G)), 1.0
>
> def rhs(t, theta):
>     differences = theta[None, :] - theta[:, None]
>     return omega + K * (A * np.sin(differences)).sum(axis=1)
>
> solution = solve_ivp(rhs, (0, 20), initial, rtol=1e-7, atol=1e-9)
> assert solution.success
> coherence = np.abs(np.exp(1j * solution.y).mean(axis=0))
> print(coherence[0], coherence[-1])
> ```

For vector-valued oscillators, perturbations around a synchronous trajectory lead to mode-dependent time-varying variational equations rather than a single scalar eigenvalue test. This is the setting of the master-stability approach. [[Spectral graph theory]] supplies the network eigenmodes; the local dynamics supplies each mode’s stability.

> [!reference]- Sources
> Jenny’s notes Week 12, with corrected diffusion, sine and stability signs and finite-N coherence statement. Newman §§17.1–17.5, especially §17.2.1 and §17.5. Scalar and phase calculations above are explicit derivations. Current-course lecture/tutorial coverage after Week 7 was not supplied.
