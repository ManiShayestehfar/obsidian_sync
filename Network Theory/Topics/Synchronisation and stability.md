---
tags: [data5441, ch12, dynamics]
aliases: [Synchronisation, Kuramoto model, Linear stability, Continuous-time dynamics]
---
# Synchronisation and stability

> [!abstract] Summary
> Jeny's Week 12 notes extend the course's dynamics discussion from binary states to **continuous-time states**. The network couples each node's differential equation to its neighbours. The two examples are **diffusion-like coupling** and the **Kuramoto oscillator model**; the worked derivation relates stability of a homogeneous fixed point to **Laplacian eigenvalues**.
> Chapter: [[Ch12 Epidemics and games on networks]] · **Jeny pp. 59–62, §§12.3–12.3.2**.

> [!warning] Source and assessment scope
> This material appears in **Jeny's previous-year course notes** but is **not developed in the supplied written 2026 lecture PDF** (which finishes with games on p. 167). It is included because the requested sources include Jeny. The result and derivation below follow her notation as far as possible; a few **sign inconsistencies in her printed formulas are flagged explicitly** rather than silently copied.

## 1. Continuous-time network dynamics

> [!definition] General dynamical system (Jeny §12.3)
> Each node has a time-dependent state $x_i(t)\in\mathbb R^d$. The network-coupled dynamics is
> $$\boxed{\frac{dx_i}{dt}=f_i(x_i)+\sum_{j=1}^{N}A_{ij}g_i(x_i,x_j).}$$
> Here $f_i$ describes the node's **internal dynamics**; $g_i$ describes the **interaction** with its neighbours; and $A_{ij}$ determines which pairs interact.
>
> Jeny then simplifies to **scalar** states ($d=1$), **identical** internal dynamics $f_i=f$, and **coupling vanishing at equal states**, $g(x,x)=0$.

> [!example] Two forms mentioned in the notes
> - **Diffusion-like:** $\dot x_i=\beta\sum_j A_{ij}(x_i-x_j)$ in Jeny's printed convention.
> - **Kuramoto:** oscillating phases $\theta_i\in[0,2\pi]$ interact through sine functions of phase differences.
>
> **Sign convention matters:** the displayed diffusion-like expression equals $+\beta(\mathcal Lx)_i$, where $\mathcal L=D-A$. For $\beta>0$ this does not have the usual smoothing sign. The notes do not specify a universal sign choice; the stability calculation below handles the sign through $\beta$.

## 2. Kuramoto model and phase coherence

> [!definition] Kuramoto oscillator equation (Jeny §12.3.1)
> In the notation printed in Jeny,
> $$\frac{d\theta_i}{dt}=\omega_i+\frac{K}{\langle z\rangle}\sum_{j=1}^{N}A_{ij}\sin(\theta_i-\theta_j).$$
> - $\theta_i(t)$ is node $i$'s **phase**.
> - $\omega_i$ is its **natural frequency**, sampled from a distribution.
> - $K$ controls coupling, and $\langle z\rangle$ is the mean network degree.
>
> The sign of the sine term depends on how the coupling convention is defined; Jeny prints $\sin(\theta_i-\theta_j)$. Be cautious about inferring attractive synchronisation for positive $K$ from this sign alone.

> [!definition] Synchronisation order parameter
> $$\boxed{r(t)e^{\mathrm i\psi(t)}=\frac1N\sum_{j=1}^N e^{\mathrm i\theta_j(t)},\qquad 0\le r(t)\le1.}$$
> Each phase is represented by a unit complex number. Its **average vector length** $r(t)$ measures coherence; $\psi(t)$ is the collective phase.
> - $r=1$: **perfect synchronisation**, all phases the same.
> - $r$ close to $0$: phases spread around the circle, with **weak coherence**.
> - $0<r<1$: **partial synchronisation**.
>
> We study $r_\infty=\lim_{t\to\infty}r(t)$ for large networks. Incoherent phases give a vanishing order parameter in the **large-$N$ idealisation**; a finite configuration need not give exactly zero.

![[Assets/w12-kuramoto-phases.png|640]]

> [!proposition] Dependence on the degree distribution (stated in Jeny)
> Jeny states an onset-of-synchronisation relation of the form
> $$\boxed{K_c^*=K_c\frac{\langle z\rangle}{\langle z^2\rangle},}$$
> where $K_c$ is the reference critical coupling in the notes. Its motivation is the same network **degree-heterogeneity effect** seen elsewhere in the course: the ratio $\langle z\rangle/\langle z^2\rangle$ decreases for broader degree distributions.
>
> **Status:** the formula is **stated, not derived**, in the provided Jeny pages. The parameter normalisation and sign conventions are not developed further there; do not treat this as a general identity for every Kuramoto normalisation.

## 3. Homogeneous fixed point and linear stability

> [!definition] Fixed point (Jeny §12.3.2)
> Consider the scalar system
> $$\dot x_i=f(x_i)+\sum_jA_{ij}g(x_i,x_j),\qquad g(x,x)=0.$$
> If $f(x^*)=0$, then $x_i(t)=x^*$ for every $i$ is a **homogeneous fixed point**: both the internal term and the network coupling vanish.

> [!theorem] Linearisation with difference coupling (Jeny pp. 61–62)
> Choose the form $g(x_i,x_j)=h(x_i)-h(x_j)$ and define
> $$\alpha=f'(x^*),\qquad\beta=h'(x^*),\qquad\mathcal L=D-A.$$
> Writing $x_i=x^*+\varepsilon_i$, first-order perturbations satisfy
> $$\boxed{\frac{d\boldsymbol\varepsilon}{dt}\approx(\alpha I+\beta\mathcal L)\boldsymbol\varepsilon.}$$
> If $\mathcal Lv_r=\lambda_r v_r$ and $\boldsymbol\varepsilon=\sum_r c_rv_r$, then
> $$\boxed{\dot c_r=(\alpha+\beta\lambda_r)c_r.}$$
> Thus a **linear stability condition** is $\alpha+\beta\lambda_r<0$ for **every** Laplacian eigenvalue $\lambda_r$.

> [!proof]- Derivation exactly at the level of Jeny's notes
> Expand the internal dynamics: $f(x^*+\varepsilon_i)\approx f(x^*)+f'(x^*)\varepsilon_i=\alpha\varepsilon_i$.
>
> Expand the difference coupling: $h(x^*+\varepsilon_i)-h(x^*+\varepsilon_j)\approx\beta(\varepsilon_i-\varepsilon_j)$.
>
> Therefore
> $$\dot\varepsilon_i\approx\alpha\varepsilon_i+\beta\sum_jA_{ij}(\varepsilon_i-\varepsilon_j)=\alpha\varepsilon_i+\beta\sum_j\mathcal L_{ij}\varepsilon_j.$$
> In vector form this is $(\alpha I+\beta\mathcal L)\boldsymbol\varepsilon$. Applying the operator to an eigenvector $v_r$ gives $(\alpha+\beta\lambda_r)v_r$, so each eigenmode evolves independently at that linear rate.

> [!remark] The role of the largest eigenvalue
> Since the graph Laplacian has $0=\lambda_1\le\cdots\le\lambda_N$, the uniform mode has rate $\alpha$. When $\beta\ge0$, the **largest** mode growth rate is $\alpha+\beta\lambda_N$; stability therefore requires
> $$\boxed{\alpha+\beta\lambda_N<0\qquad (\beta\ge0).}$$
> In particular $\alpha<0$ is necessary. If $\beta>0$, one may write $\beta<-\alpha/\lambda_N$ when $\lambda_N>0$. This is the **network-dependent condition** highlighted by Jeny.

> [!warning] Sign slips in Jeny's p. 62
> Page 61 derives $\alpha I+\beta\mathcal L$. Page 62 then prints $\alpha I-\beta\mathcal L$ in a proposition but attributes to it eigenvalues $\alpha+\beta\lambda_r$; it also prints a **$>0$** inequality in one stability sentence. These statements cannot all hold simultaneously. The notes here keep the **explicitly derived** operator $\alpha I+\beta\mathcal L$ and the corresponding **negative growth rate** condition $\alpha+\beta\lambda_r<0$.

## 4. What to remember

> [!exam] Core ideas from Jeny's section
> 1. **Network dynamical equation:** internal evolution + coupling through $A_{ij}$.
> 2. **Kuramoto order parameter:** $r$ measures coherence of oscillator phases.
> 3. **Degree heterogeneity:** Jeny states an onset relation involving $\langle z\rangle/\langle z^2\rangle$.
> 4. **Stability:** perturb around $x_i=x^*$, linearise, and express the result using $\mathcal L=D-A$.
> 5. **Modes:** the eigenvalues $\lambda_r$ shift growth rates to $\alpha+\beta\lambda_r$.

> [!selftest]- Quick checks
> 1. Why is $x_i\equiv x^*$ a network fixed point when $f(x^*)=g(x^*,x^*)=0$? — Every term in $\dot x_i$ is zero.
> 2. What does $r(t)=1$ mean? — All oscillator phases coincide.
> 3. If $\alpha=-2$, $\beta=0.2$, and $\lambda_N=8$, is the linearisation stable? — Yes: $-2+0.2(8)=-0.4<0$.
> 4. Why do we inspect $\lambda_N$ when $\beta>0$? — It gives the largest mode growth rate.

---
Related: [[Spectral graph theory]] · [[Binary-state dynamics]] · [[SIR model and epidemic threshold]]
