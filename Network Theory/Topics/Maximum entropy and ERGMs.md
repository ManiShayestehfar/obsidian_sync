---
tags: [data5441, ch06, models]
aliases: [ERGM, Exponential random graph model, Maximum entropy, Partition function]
---
---
# Maximum entropy and ERGMs

> [!abstract] Core idea
> To build a random-graph model matching chosen network statistics **on average**, choose the distribution that maximises entropy under those constraints. This yields an **exponential random graph model (ERGM)**:
> $$\boxed{p_{\boldsymbol\beta}(g)=\frac{\exp\!\big(\sum_a\beta_a x_a(g)\big)}{Z(\boldsymbol\beta)}.}$$
> **Metropolis–Hastings** then samples graphs from that distribution; a **separate fitting loop** finds the parameter(s) $\boldsymbol\beta$ that reproduce observed statistics.
>
> Course: **DATA5441 Week 6**, lecture PDF pp. **79–84**, and Tutorial 6, §§2–3. See [[Metropolis–Hastings]] and [[Markov chain Monte Carlo on graphs]].

## 1. The maximum-entropy problem: choose a random-graph law

In the earlier uniform graph models, $p(g)=1/|\Omega|$ gives every allowed graph equal weight. But if the observed network has unusually high clustering, the uniform ensemble may be inadequate. We want a principled distribution that **enforces what we know and does not introduce additional preferences**.

> [!definition] Maximum entropy with soft constraints
> Fix a finite set $\Omega$ of allowed graphs, and statistics $x_1(g),\ldots,x_m(g)$ with prescribed ensemble means $x_1^*,\ldots,x_m^*$. Find probabilities $p(g)$ maximising
> $$H[p]=-\sum_{g\in\Omega}p(g)\ln p(g)$$
> subject to
> $$\sum_{g\in\Omega}p(g)=1,\qquad\sum_{g\in\Omega}p(g)x_a(g)=x_a^*\ \ (a=1,\ldots,m).$$
> Here $x_a^*$ can be the statistic measured on an observed graph $g^*$: $x_a^*=x_a(g^*)$.

**First check: no statistical constraints.** If normalisation is the only condition ($m=0$), maximum entropy gives the **uniform** distribution $p(g)=1/|\Omega|$. This recovers the uniform random-graph ensembles from Week 4.

## 2. Why the exponential form appears

> [!theorem] Maximum entropy $\Longrightarrow$ ERGM
> Provided the specified means are feasible and an interior maximum exists, the entropy-maximising distribution has the form
> $$\boxed{p_{\boldsymbol\beta}(g)=\frac{e^{\boldsymbol\beta\cdot\mathbf x(g)}}{Z(\boldsymbol\beta)},\qquad Z(\boldsymbol\beta)=\sum_{h\in\Omega}e^{\boldsymbol\beta\cdot\mathbf x(h)}.}$$
> - $\mathbf x(g)=(x_1(g),\ldots,x_m(g))$ contains the selected graph statistics.
> - $\boldsymbol\beta=(\beta_1,\ldots,\beta_m)$ controls their preferences.
> - $Z$ is the **partition function**, which makes the probabilities sum to $1$.
>
> The parameters are fitted so that $\mathbb E_{\boldsymbol\beta}[x_a]=x_a^*$.

> [!proof]- Short Lagrange-multiplier derivation
> Introduce multipliers $\lambda,\beta_1,\ldots,\beta_m$:
> $$\mathcal L=-\sum_g p_g\ln p_g+\lambda\left(\sum_g p_g-1\right)+\sum_a\beta_a\left(\sum_g p_gx_a(g)-x_a^*\right).$$
> Differentiating with respect to each $p_g>0$ gives
> $$-\ln p_g-1+\lambda+\sum_a\beta_a x_a(g)=0.$$
> Thus $p_g=e^{\lambda-1}e^{\boldsymbol\beta\cdot\mathbf x(g)}$. Normalisation forces $e^{\lambda-1}=1/Z$, giving the stated formula.
>
> Entropy is strictly concave in $p$, while the feasible constraints are linear; hence the feasible maximum-entropy probability distribution is unique. (If the target means lie on the boundary, some fitted parameters may need to diverge.) $\square$

> [!tip] Interpret $\beta$ as a preference, not as a probability
> With one statistic $x(g)$,
> $$\frac{p_\beta(g')}{p_\beta(g)}=e^{\beta[x(g')-x(g)]}.$$
> If $\beta>0$, graphs with **higher** $x$ receive greater relative weight; if $\beta<0$, graphs with **lower** $x$ do. At $\beta=0$, the law is uniform on the **specified sample space** $\Omega$.

## 3. Why derivatives of $\log Z$ matter

> [!theorem] Moments, fluctuations and parameter fitting
> For finite $\Omega$,
> $$\boxed{\frac{\partial\ln Z}{\partial\beta_a}=\mathbb E_{\boldsymbol\beta}[x_a],\qquad\frac{\partial^2\ln Z}{\partial\beta_a\partial\beta_b}=\operatorname{Cov}_{\boldsymbol\beta}(x_a,x_b).}$$
> In particular, for one statistic,
> $$\boxed{\frac{d}{d\beta}\mathbb E_\beta[x]=\operatorname{Var}_\beta(x)\ge0.}$$
> Thus increasing its coefficient $\beta$ **cannot decrease its ensemble mean** (though individual samples may fluctuate).

> [!proof]- Derive the $\log Z$ identities
> Differentiate $Z=\sum_g e^{\beta\cdot x(g)}$ term by term:
> $$\frac{\partial\ln Z}{\partial\beta_a}=\frac{\sum_gx_a(g)e^{\beta\cdot x(g)}}{Z}=\mathbb E_\beta[x_a].$$
> Differentiating again gives
> $$\frac{\partial^2\ln Z}{\partial\beta_a\partial\beta_b}=\mathbb E_\beta[x_ax_b]-\mathbb E_\beta[x_a]\mathbb E_\beta[x_b],$$
> exactly the covariance. $\square$

The same equation explains **moment matching** in maximum likelihood: for one observed graph $g^*$,

$$\log p_\beta(g^*)=\beta\cdot x(g^*)-\log Z(\beta),\qquad\frac{\partial\log p_\beta(g^*)}{\partial\beta_a}=x_a(g^*)-\mathbb E_\beta[x_a].$$

A finite interior maximum-likelihood estimate therefore satisfies $\mathbb E_\beta[x_a]=x_a(g^*)$.

## 4. Erdős–Rényi is an ERGM of the number of links

> [!example] Recover $G(N,q)$ exactly
> Take $\Omega_N$, the space of **all** labelled simple graphs on $N$ nodes. Write $Y=\binom N2$ and choose $x(g)=L(g)$.
>
> Each of the $Y$ possible edges contributes either $1$ (absent) or $e^\beta$ (present). Consequently,
> $$Z(\beta)=\sum_{g\in\Omega_N}e^{\beta L(g)}=(1+e^\beta)^Y.$$
> Therefore
> $$p_\beta(g)=\frac{e^{\beta L(g)}}{(1+e^\beta)^Y}=q^{L(g)}(1-q)^{Y-L(g)},\qquad\boxed{q=\frac{e^\beta}{1+e^\beta}}.$$
> This is exactly the **Erdős–Rényi graph** $G(N,q)$, with independent edge probability $q$.

**Crucial contrast:** if the sample space is already $\Omega_{N,L}$, the statistic $L(g)=L$ is fixed. Then $e^{\beta L}$ is the **same for every graph**, so changing $\beta$ cannot change the model. Choose a statistic that can actually vary within $\Omega$.

## 5. Hard versus soft constraints

> [!definition] Two distinct ways to constrain an ensemble
> - **Hard constraint:** restrict $\Omega$. Example: $\Omega_{N,L}$ consists only of graphs with exactly $L$ edges; $\Omega(\mathbf z)$ consists only of graphs with exactly the degree sequence $\mathbf z$.
> - **Soft constraint:** keep eligible graphs in $\Omega$ but weight them by an ERGM. Example: $p_\beta(g)\propto e^{\beta C(g)}$ selects a mean clustering coefficient, not an identical clustering value in every graph.

A sampled graph satisfies **every hard constraint exactly**, whereas its soft-constrained statistics **fluctuate around their fitted expectations**. This distinction is central to Tutorial 6.

![[Assets/graph-proposals.png|800]]

*For MH sampling, the proposal must preserve the hard constraints defining $\Omega$: edge replacement for fixed $N,L$, or degree-preserving double-edge swaps for fixed $\mathbf z$.*

## 6. Metropolis–Hastings **for an ERGM**

The ERGM specifies **which graphs should be common**, while MH lets us **sample them** without calculating $Z$.

> [!proposition] Acceptance rule for an ERGM
> If $p_\beta(g)=e^{\beta x(g)}/Z(\beta)$ and the proposal is symmetric, then
> $$\begin{aligned}
> A(g\to g')&=\min\left\{1,\frac{p_\beta(g')}{p_\beta(g)}\right\}\\
> &=\min\left\{1,\frac{e^{\beta x(g')}/Z}{e^{\beta x(g)}/Z}\right\}\\
> &=\boxed{\min\{1,e^{\beta\Delta x}\}},\quad\Delta x=x(g')-x(g).
> \end{aligned}$$
> **Several statistics:** $A=\min\{1,e^{\sum_a\beta_a\Delta x_a}\}$.
>
> For a **non-symmetric** proposal, multiply the exponential ratio by $\Pi(g'\to g)/\Pi(g\to g')$ before taking the minimum.

This gives an immediate interpretation:

| Parameter and proposed change | Acceptance (symmetric proposal) |
|---|---|
| $\beta>0$, $\Delta x>0$ | $1$ — the favoured statistic increases |
| $\beta>0$, $\Delta x<0$ | $e^{\beta\Delta x}<1$ |
| $\beta<0$, $\Delta x<0$ | $1$ — the favoured statistic decreases |
| $\beta=0$ | $1$ — uniform on the permitted graph space |

> [!example] Trial Exam 1, Q7: triangle-biased fixed-$L$ graphs
> Let $N=24$, $L=48$ and $Y=\binom{24}{2}=276$. Then
> $$|\Omega_{24,48}|=\binom{276}{48},\qquad p_\beta(g)=\frac{e^{\beta T(g)}}{Z(\beta)}.$$
> Use the symmetric edge-replacement proposal from [[Metropolis–Hastings]]. For a proposal creating $2$ triangles ($\Delta T=2$) with $\beta>0$, accept surely; for one destroying $2$ triangles, accept with $e^{-2\beta}$.
>
> **Note:** on $\Omega_{N,L}$, a higher triangle count does *not* always imply proportionally higher transitivity, since $\sum_i\binom{z_i}{2}$ may change. On a **fixed-degree** graph space the denominator is constant and $C(g)=3T(g)/\sum_i\binom{z_i}{2}$, so a triangle bias and a transitivity bias are equivalent after rescaling $\beta$.

### Fitting $\beta$ is a separate sampling loop

The lecture (pp. 83–84) prescribes **two stages**:
1. **Fit:** for several trial $\beta$ values, run MH long enough to estimate $\widehat{\mathbb E_\beta[x]}$; find $\beta^*$ where it matches the observed $x(g^*)$.
2. **Sample the fitted model:** fix $\beta=\beta^*$, equilibrate again, then collect graph samples to estimate other properties and their fluctuations.

In symbols,
$$\boxed{\widehat{\mathbb E_{\beta^*}[x]}\approx x(g^*),\qquad\widehat{\mathbb E_{\beta^*}[y]}=\frac1S\sum_{s=1}^S y(g_s).}$$
The first statistic $x$ is used to **fit**; the second statistic $y$ tests what the model **predicts beyond its fitting constraints**.

![[Assets/ergm-parameter-fitting.png|850]]


> [!warning] Why fitting can be computationally hard
> $Z(\beta)$ is usually too large to sum directly, so each point on the fitting curve requires an MCMC estimate. **Burn-in and correlation times may depend on $\beta$**; large positive or negative biases can make exploration slow. Tutorial 6 uses increasing and decreasing $\beta$ sweeps as a check: disagreement may indicate poor equilibration, rather than two different correct equilibrium curves.

## 7. Tutorial 6: clustering of the November 17 network

The tutorial studies an observed association network $G$ and asks: *Is its clustering, and then its unusually high maximum betweenness, explained by an appropriate random-graph model?*

> [!example] Model, sampling and test
> **Hard constraint:** keep the observed degrees $\mathbf z(G)$ exactly:
> $$\Omega=\Omega(\mathbf z(G)).$$
> **Soft constraint:** weight graphs by transitivity:
> $$\boxed{p_\beta(g)=\frac{e^{\beta C(g)}}{Z(\beta)},\quad g\in\Omega(\mathbf z(G)).}$$
> **MH move:** make a degree-preserving double-edge swap, and (for a symmetric single-attempt proposal) accept with
> $$\boxed{A=\min\{1,e^{\beta[C(g')-C(g)]}\}.}$$
>
> The exercise progresses as follows:
> 1. **$\beta=0$:** sample uniformly among graphs with the observed degrees; compare their mean $C$ with $C(G)$. Is the degree sequence alone sufficient?
> 2. **Vary $\beta$:** estimate $C_{RG,\beta}=\mathbb E_\beta[C]$ and find $\beta^*$ satisfying $C_{RG,\beta^*}\approx C(G)$.
> 3. **Validate:** generate fresh samples at $\beta^*$ and check their mean clustering against $C(G)$.
> 4. **Predict another quantity:** compute the distribution of maximum betweenness $B_{\max}$ among fitted-model samples; compare the observed $B_{\max}(G)$ with that distribution.
> 5. **Investigate dependence:** vary $\beta$ and examine how ensemble-average $B_{\max}$ changes with ensemble-average $C$.

**Why is the last test interesting?** Matching degrees and clustering does **not** automatically match maximum betweenness. A large discrepancy would indicate network structure not captured by these constraints alone.

> [!remark] Tutorial 6: other clustering weights (Exercise 2.1)
> In a fixed-degree $k$-regular graph space, the tutorial also compares $w(g)=1$, $w(g)=C(g)$, and $w(g)=C(g)^{10}$:
> - Uniform sampling gives no clustering preference.
> - $C$ and especially $C^{10}$ favour higher-clustering graphs relative to lower-clustering ones **when both have positive $C$**.
> - These weights **are not ERGMs with statistic $C$**, since $C^r$ is not $e^{\beta C}$ for a fixed $\beta$; they assign zero weight to $C=0$ graphs. Use MH on the target's positive-probability support.
>
> A 4-regular graph with clustering $1$ exists: take the disjoint union of ten copies of $K_5$ ($N=50$), illustrating that *possible* high clustering need not be *typical* under uniform sampling.

## 8. Exam essentials

| Situation | Correct conclusion |
|---|---|
| No soft constraints ($\beta=0$) | Uniform distribution on the **chosen** $\Omega$ |
| $x=L$ on $\Omega_N$ | Exactly the Erdős–Rényi $G(N,q)$ law |
| $x=L$ on $\Omega_{N,L}$ | No effect: $L$ is already fixed |
| $\beta>0$ for $x=T$ | Graphs with more triangles receive more relative weight |
| $\beta>0$ for $x=C$ | Graphs with greater transitivity receive more relative weight |
| MH samples at fixed $\beta$ | Estimate expectations without evaluating $Z(\beta)$ |
| Fit $\beta$ | Match **ensemble-average** statistics, not each sample exactly |

> [!question]- Self-test
> 1. **What does maximum entropy choose?** The least preferential probability law consistent with normalisation and the given mean-statistic constraints (relative to the specified graph space).
> 2. **Why does an ERGM involve $e^{\beta x}$?** It follows from the Lagrange-multiplier first-order condition.
> 3. **Why is $\beta=0$ special?** All graph weights become $1$; the law is uniform on $\Omega$.
> 4. **What does $\partial_\beta\log Z$ measure?** The ensemble mean of the constrained statistic.
> 5. **Why is $\mathbb E_\beta[x]$ non-decreasing in $\beta$?** Its derivative is $\operatorname{Var}_\beta(x)\ge0$.
> 6. **What is the MH acceptance for $p_\beta\propto e^{\beta C}$ and symmetric swaps?** $\min\{1,e^{\beta\Delta C}\}$.
> 7. **Why compare $B_{\max}$ after fitting clustering?** It is an out-of-fit statistic that tests whether the selected constraints explain other structural features.

---
Related: [[Metropolis–Hastings]] · [[Random graph ensembles]] · [[Clustering]] · [[Reconstruction from node activity]]
