---
tags: [data5441, ch12, dynamics]
aliases: [Synchronisation, Kuramoto model, Linear stability, Diffusion on networks, Consensus]
---
# Synchronisation and stability

> [!abstract] Summary
> For **continuous node states**, coupling through links creates collective dynamics. The Laplacian $\mathcal L=D-A$ separates small disturbances into eigenmodes: fast-decaying modes smooth differences, while the **uniform mode** behaves differently. Diffusion leads to consensus on a connected graph; the Kuramoto model describes synchronisation of oscillators.
> Chapter: [[Ch12 Epidemics and games on networks]] · **Supplementary**: Jeny's notes §§12.3–12.3.2. This material is **not present as a written derivation in the 2026 lecture-notes PDF**, whose Week 12 pages focus on SIR and games.

## 1. Continuous dynamics on a graph

> [!definition] Coupled differential equations
> Each node has a real state $x_i(t)$ and evolves according to
> $$\dot x_i=f(x_i)+\sum_jA_{ij}g(x_i,x_j).$$
> The function $f$ describes **local dynamics**; $g$ describes **coupling through edges**. If $f(x^*)=0$ and $g(x^*,x^*)=0$, then $x_i=x^*$ for all $i$ is a **homogeneous fixed point**.

> [!example] Attractive diffusion
> With coupling $g(x_i,x_j)=\beta(x_j-x_i)$, $\beta>0$,
> $$\boxed{\dot x_i=\beta\sum_jA_{ij}(x_j-x_i),\qquad\dot x=-\beta\mathcal Lx,\quad\mathcal L=D-A.}$$
> A node above its neighbours' average tends to decrease, and a node below it tends to increase. **Sign matters:** $+\beta\sum_jA_{ij}(x_i-x_j)=+\beta\mathcal Lx$ would instead be *anti-diffusion* for positive $\beta$.

## 2. Why Laplacian eigenvalues control stability

> [!theorem] Linearised stability of a homogeneous state
> Suppose $g(x_i,x_j)=\beta[h(x_j)-h(x_i)]$. Write
> $$a=f'(x^*),\qquad b=\beta h'(x^*),\qquad\epsilon_i=x_i-x^*.$$
> To first order the perturbation obeys
> $$\boxed{\dot\epsilon=(aI-b\mathcal L)\epsilon.}$$
> For Laplacian eigenpairs $\mathcal Lv_r=\lambda_rv_r$ with $0=\lambda_1\le\cdots\le\lambda_N$, an eigenmode amplitude evolves as
> $$\boxed{c_r(t)=c_r(0)e^{(a-b\lambda_r)t}.}$$
> All perturbations decay exponentially if $a-b\lambda_r<0$ for **every** mode. If $b\ge0$ on a connected graph, the largest growth rate is the **uniform mode** $a$; thus $a<0$ is sufficient and necessary for exponential linear stability. Zero growth rates need a higher-order analysis.

> [!derivation]- Expand, then diagonalise
> Expand $f(x^*+\epsilon_i)\simeq f(x^*)+a\epsilon_i$ and $h(x^*+\epsilon_j)-h(x^*+\epsilon_i)\simeq h'(x^*)(\epsilon_j-\epsilon_i)$. Since $f(x^*)=0$,
> $$\dot\epsilon_i=a\epsilon_i+b\sum_jA_{ij}(\epsilon_j-\epsilon_i)=a\epsilon_i-b(\mathcal L\epsilon)_i.$$
> Symmetry of $\mathcal L$ gives an orthonormal eigenbasis; write $\epsilon=\sum_rc_rv_r$ and compare coefficients. The linear system separates into $\dot c_r=(a-b\lambda_r)c_r$.

## 3. Diffusion and consensus

> [!theorem] Convergence to the initial average
> On a **connected** undirected graph, $\dot x=-\beta\mathcal Lx$, $\beta>0$, satisfies
> $$\boxed{x(t)\longrightarrow\overline{x(0)}\,\mathbf1,\qquad \overline{x(0)}=\frac1N\sum_ix_i(0).}$$
> The mean is preserved because $\mathbf1^\top\mathcal L=0$. All non-uniform eigenmodes decay, and the slowest rate is $\beta\lambda_2$ (**algebraic connectivity**). For a disconnected graph, each component converges to **its own** starting mean.

![[Assets/w12-diffusion-synchronisation.png|780]]

> [!remark] Reading the figure
> The left panel shows identical **diffusion dynamics** starting from different node values and approaching their common average. The right panel is a separate numerical illustration of **identical-frequency Kuramoto** oscillators on a connected path; coupling makes their phase-coherence parameter rise towards $1$. These are model-generated figures, not extracted 2026 lecture results.

## 4. Kuramoto oscillators

> [!definition] Phases, natural frequencies and order parameter
> Each node carries a phase $\theta_i\in\mathbb R/(2\pi\mathbb Z)$. A standard **attractive-coupling convention** is
> $$\boxed{\dot\theta_i=\omega_i+K\sum_jA_{ij}\sin(\theta_j-\theta_i),\qquad K\ge0.}$$
> Here $\omega_i$ is the natural frequency of oscillator $i$. Phase coherence is quantified by
> $$\boxed{re^{\mathrm i\psi}=\frac1N\sum_{j=1}^Ne^{\mathrm i\theta_j},\qquad0\le r\le1.}$$
> - $r=1$: perfect phase alignment.
> - Small $r$: phases spread around the circle; for independent uniform phases, $\mathbb E[r^2]=1/N$.
> - $0<r<1$: partial coherence.

> [!proposition] Identical oscillators near synchrony
> If all $\omega_i=\omega$, move to a frame rotating with angular speed $\omega$. Near a synchronised state, $\sin(\theta_j-\theta_i)\simeq\theta_j-\theta_i$, giving
> $$\dot\delta\simeq-K\mathcal L\delta.$$
> On a connected network, every **non-uniform** small phase perturbation decays. Uniform phase shifts remain neutral ($\lambda_1=0$), because rotating all phases by the same amount changes no relative phase.

> [!warning] Source and convention check
> The supplementary notes use different **signs/normalisations** for coupling in places. The equations above use the physically standard **attractive** sign (neighbours draw states/phases together). Numerical values of critical Kuramoto coupling depend on whether $K$ is divided by $\langle z\rangle$ and on the frequency distribution; no universal value is asserted here.

> [!exam] Remember
> - $\mathcal L=D-A$, and $\mathcal L\mathbf1=0$.
> - **Stability rates:** $a-b\lambda_r$.
> - **Diffusion:** $-\beta\mathcal Lx$ smooths; $\lambda_2$ controls the slowest non-uniform relaxation.
> - **Kuramoto:** $r=1$ indicates perfect synchronisation; the uniform phase mode is neutral.

> [!selftest]- Check your understanding
> 1. What happens if a diffusion network has two connected components? — Each approaches its own mean.
> 2. Why does $\lambda_2$ matter for diffusion? — It is the smallest positive Laplacian eigenvalue and hence the slowest decay rate.
> 3. Can a linear mode with exponent exactly $0$ be declared asymptotically stable from linearisation alone? — No.

---
Related: [[Spectral graph theory]] · [[Binary-state dynamics]] · [[SIR model and epidemic threshold]]
