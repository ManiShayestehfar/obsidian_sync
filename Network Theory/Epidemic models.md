---
tags: [dynamics]
---

# Epidemic models

These are mathematical spreading models. The transition rules, contact process and approximation determine their thresholds.

> [!definition] SI, SIS and SIR
> Infections occur across susceptible–infected edges at rate $\lambda>0$. Recovery, when present, has rate $\mu>0$.
>
> - **SI:** $S\to I$; no recovery.
> - **SIS:** $S\to I\to S$; recovered vertices can be reinfected.
> - **SIR:** $S\to I\to R$; removed/recovered vertices remain unavailable for reinfection in this model.
>
> In SIR let $s,i,r$ denote population fractions, with $s+i+r=1$. They are not the same as individual infection probabilities conditional on a realised network history.

## Homogeneous mean-field SIR
With average degree $c$ and uniformly mixed states, use
$$\dot s=-\lambda csi,\qquad\dot i=\lambda csi-\mu i,\qquad\dot r=\mu i.$$
Their sum is zero, preserving total mass. The early growth condition is $\lambda c s_0>\mu$; replacing $s_0$ by one is a small-initial-infection approximation.

> [!theorem] Final-size relation within this closure
> For initial $r_0=0$,
> $$s_\infty=s_0e^{-(\lambda c/\mu)r_\infty},\qquad r_\infty=1-s_0e^{-(\lambda c/\mu)r_\infty}.$$

> [!proof]
> While infection is present, divide the first equation by the third: $ds/dr=-(\lambda c/\mu)s$. Integrate from $(s_0,0)$ to get $s=s_0e^{-(\lambda c/\mu)r}$. In this closed SIR model $i_\infty=0$, so $s_\infty+r_\infty=1$. Keep $s_0$ unless explicitly taking the vanishing-seed limit. The nonzero root in that limit concerns an introduced small infection; the exactly infection-free initial state remains infection-free.

## Degree and adjacency closures
For uncorrelated degree-based SIS, a common closure is
$$\dot i_k=-\mu i_k+\lambda k(1-i_k)\Theta,\qquad\Theta=\frac{\sum_k kp_ki_k}{\langle k\rangle}.$$
Linearisation predicts $\lambda/\mu>\langle k\rangle/\langle k^2\rangle$. A node-based independence closure instead has Jacobian $\lambda A-\mu I$ at zero and predicts instability when $\lambda\rho(A)>\mu$. These are closure predictions, not interchangeable exact thresholds for every finite stochastic network.

A corresponding degree-based **SIR** closure is $\dot s_k=-\lambda k s_k\Theta$, $\dot i_k=\lambda k s_k\Theta-\mu i_k$ and $\dot r_k=\mu i_k$, with the same edge-weighted $\Theta$ and classwise conservation $s_k+i_k+r_k=1$. It retains degree heterogeneity but still neglects state correlations. Its early linearisation at $s_k\approx1$ has the same moment threshold as the stated degree-based SIS closure; this does not replace the transmission/excess-degree calculation for an exact network process.

> [!warning] Finite SIS eventually becomes extinct
> On a finite closed network with positive recovery rate and no external infections, the all-susceptible state is absorbing and reachable from every state. The stochastic SIS process becomes extinct almost surely. A long-lived “endemic” regime describes metastability or a limiting/conditioned model, not permanent survival on that finite graph.

## Transmission and percolation
If infectious duration is fixed at $\tau$ and contacts on an edge form a Poisson process of rate $\lambda$, edge transmissibility is $T=1-e^{-\lambda\tau}$. If duration is exponential with recovery rate $\mu$, averaging gives $T=\lambda/(\lambda+\mu)$, approximately $\lambda/\mu$ only when that ratio is small.

On a locally tree-like configuration network, early branching suggests $T\kappa>1$. Independent edge transmissibilities produce the bond-percolation correspondence. Shared random recovery time can correlate a vertex’s outgoing transmissions, so a single $T$ does not make every SIR observable identical to independent bond percolation. A supercritical process still has a positive chance of dying out from a small seed.

> [!code] Integrate the stated mean-field model
> ```python
> import numpy as np
> from scipy.integrate import solve_ivp
>
> lam, mu, c = 0.3, 1.0, 5.0
>
> def rhs(t, state):
>     s, i, r = state
>     incidence = lam * c * s * i
>     return [-incidence, incidence - mu*i, mu*i]
>
> solution = solve_ivp(rhs, (0, 60), [0.999, 0.001, 0.0],
>                      rtol=1e-8, atol=1e-10)
> assert solution.success
> assert np.allclose(solution.y.sum(axis=0), 1.0)
> print(solution.y[:, -1])
> ```
> This integrates the deterministic closure; it does not simulate a stochastic epidemic on a graph.

See [[Percolation and robustness]] for the branching factor and [[Binary dynamics and cascades]] for the general degree-based closure.

> [!reference]- Sources
> Jenny’s notes Week 11, with corrected rate/transmissibility and finite-size qualifications. Newman §§16.1–16.3 and 16.6–16.7. Formula derivations state the precise model being used. Current-course lecture/tutorial coverage after Week 7 was not supplied.
