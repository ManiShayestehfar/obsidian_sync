---
tags: [data5441, ch03, models]
aliases: [ER graph, Poisson random graph, G(N,p), Giant component]
---
---
# Erdős–Rényi graphs

> [!abstract] Summary
> In $G(N,p)$, each possible edge is present **independently** with probability $p$. Degrees are binomial (Poisson in the sparse limit), clustering is governed by $p$, and the appearance of a giant component is controlled by the expected degree $\langle z\rangle$. The model is a fundamental null model for real networks.
> Chapter: [[Ch03 Random graph models]] · Lecture: **Week 3, pp. 36–44**

## 1. Definition and fitting

> [!definition] Erdős–Rényi model $G(N,p)$
> Take $N$ labelled vertices, with $Y=\binom N2$ possible undirected edges. Include each edge independently with probability $p\in[0,1]$.
>
> For a **particular** graph $g$ with $L(g)$ edges,
> $$\boxed{\Pr(G=g)=p^{L(g)}(1-p)^{Y-L(g)}.}$$
> There is **no binomial coefficient**: this is the probability of one graph, not the probability of having a particular number of edges.

Since the $Y$ edge indicators are independent Bernoulli$(p)$ variables,
$$\mathbb E[L]=pY=\frac{pN(N-1)}2,\qquad \boxed{\langle z\rangle=(N-1)p.}$$

**Fitting to data.** For an observed network $g^*$ with $N$ vertices and $L^*$ edges, the maximum-likelihood estimate is
$$\boxed{\widehat p=\frac{L^*}{Y}=\frac{2L^*}{N(N-1)}.}$$
It matches the observed average degree **in expectation**:
$$\boxed{\langle z\rangle=(N-1)\widehat p=\frac{2L^*}{N}.}$$
Other measures, such as clustering, are **not** matched automatically.

## 2. Number of links and degree distribution

> [!proposition] Exact finite-$N$ distributions
> $$\boxed{L\sim\operatorname{Bin}(Y,p),\qquad \mathbb E[L]=Yp,\qquad \sigma_L^2=Yp(1-p).}$$
> Each vertex has $N-1$ potential neighbours, so
> $$\boxed{z_i\sim\operatorname{Bin}(N-1,p),\qquad \langle z\rangle=(N-1)p,\qquad \sigma_z^2=\langle z\rangle(1-p).}$$
>
> These follow by summing independent edge indicators. Degrees of **different** vertices are not independent, because they share the indicator for their mutual edge.

### Dense versus sparse limits

| Regime                           | Choice of $p$ as $N\to\infty$                          | Expected degree                    | Expected links                               |
| -------------------------------- | ------------------------------------------------------ | ---------------------------------- | -------------------------------------------- |
| **Dense**                        | $p\in(0,1)$ fixed                                      | $\langle z\rangle=p(N-1)\to\infty$ | $\mathbb E[L]=\Theta(N^2)$                   |
| **Sparse** (bounded mean degree) | $\langle z\rangle>0$ fixed, $p=\langle z\rangle/(N-1)$ | $\langle z\rangle=\text{constant}$ | $\mathbb E[L]=N\langle z\rangle/2=\Theta(N)$ |

> [!theorem] Poisson limit in the sparse regime
> Fix $\langle z\rangle>0$ and let $p=\langle z\rangle/(N-1)$. For each fixed integer $z\ge0$,
> $$\boxed{\Pr(z_i=z)=\binom{N-1}{z}p^z(1-p)^{N-1-z}\longrightarrow e^{-\langle z\rangle}\frac{\langle z\rangle^z}{z!}.}$$
> Thus the limiting degree distribution is $\operatorname{Poisson}(\langle z\rangle)$, with mean and variance both equal to $\langle z\rangle$.

> [!proof]- Short derivation
> For fixed $z$,
> $$\binom{N-1}{z}\left(\frac{\langle z\rangle}{N-1}\right)^z\longrightarrow\frac{\langle z\rangle^z}{z!},$$
> $$\left(1-\frac{\langle z\rangle}{N-1}\right)^{N-1-z}\longrightarrow e^{-\langle z\rangle}.$$
> Multiply the limits.

**Relative degree variability.** The *exact* finite-$N$ expression is
$$\boxed{\frac{\sigma_z}{\langle z\rangle}=\sqrt{\frac{1-p}{\langle z\rangle}}.}$$
Therefore,
$$\frac{\sigma_z}{\langle z\rangle}\longrightarrow\begin{cases}
0,&p\in(0,1)\text{ fixed (dense)},\\[3pt]
1/\sqrt{\langle z\rangle},&\langle z\rangle\text{ fixed (sparse)}.
\end{cases}$$
Dense ER degrees become relatively homogeneous; sparse ER retains nonzero relative degree fluctuations.

## 3. Clustering and distances

### Clustering

For a vertex $i$ with at least two neighbours, each possible edge between its neighbours exists independently with probability $p$. Hence
$$\boxed{\mathbb E[C_i\mid z_i\ge2]=p.}$$
The expected closure probability and the usual large-network approximation for global clustering is
$$\boxed{C_{\mathrm{net}}\approx p=\frac{\langle z\rangle}{N-1}.}$$
It remains of constant order in the dense regime, but tends to $0$ like $1/N$ in the sparse regime.

> [!remark] Local versus global clustering
> $\langle C\rangle=\frac1N\sum_i C_i$ and $C_{\mathrm{net}}$ are **different averages**. If $C_i=0$ for $z_i<2$, then $\mathbb E[C_i]=p\Pr(z_i\ge2)$, not necessarily $p$. Thus $\langle C\rangle\approx C_{\mathrm{net}}\approx p$ is a useful course-level approximation, **not an exact identity** in sparse graphs.

### Shortest-path distances

For sparse ER with $\langle z\rangle>1$, exploration of the giant component is approximately a branching process: the number of reached vertices grows initially like $\langle z\rangle^d$. Setting this to order $N$ gives
$$\boxed{d_{\mathrm{diam}}\approx\frac{\log N}{\log\langle z\rangle}\qquad(\langle z\rangle>1),}$$
## 4. Giant-component phase transition

A **giant component** contains a positive fraction of all vertices as $N\to\infty$. In the sparse regime, let $S$ denote the limiting fraction of vertices in the largest component, and set $U=1-S$.

> [!theorem] Giant component in sparse $G(N,p)$
> Keep $\langle z\rangle>0$ fixed and take $p=\langle z\rangle/(N-1)$. The limiting giant-component fraction satisfies
> $$\boxed{S=1-e^{-\langle z\rangle S}.}$$
> - If $\langle z\rangle\le1$, then $S=0$: **no giant component**.
> - If $\langle z\rangle>1$, there is a **unique positive solution** $S\in(0,1)$: the largest component contains approximately $SN$ vertices.
>
> Thus $\boxed{\langle z\rangle_{\mathrm{critical}}=1.}$ The equation always has the trivial solution $S=0$; above the threshold, select the positive solution.

### Derivation of the self-consistency equation

1. For a potential neighbour $j$ of a node $i$, either there is **no edge** ($1-p$), or there is an edge but $j$ does **not** lead to the giant component (approximately $pU$).
2. Using the locally tree-like approximation, all $N-1$ potential neighbours must fail to connect $i$ to the giant component:
   $$U\approx(1-p+pU)^{N-1}.$$
3. Substitute $p=\langle z\rangle/(N-1)$ and let $N\to\infty$:
   $$U=e^{-\langle z\rangle(1-U)}.$$
4. Since $S=1-U$,
   $$\boxed{S=1-e^{-\langle z\rangle S}.}$$

**Why the threshold is $1$.** The curve $F(S)=1-e^{-\langle z\rangle S}$ has slope $F'(0)=\langle z\rangle$. A positive intersection with the line $S$ appears precisely when this slope exceeds $1$.

![[er-giant-component.png|650]]

> [!important] Giant component $\ne$ connected graph
> For every fixed $\langle z\rangle>1$, the giant fraction satisfies $S<1$, so the graph is **not fully connected** with high probability. Full connectivity occurs at the higher scale $p\sim(\log N)/N$, corresponding to $\langle z\rangle\sim\log N$.

## 5. Summary: ER properties across regimes

### Dense versus sparse ER

| Property                    | **Dense:** $p\in(0,1)$ fixed                | **Sparse:** $\langle z\rangle>0$ fixed, $p=\langle z\rangle/(N-1)$              |
| --------------------------- | ------------------------------------------- | ------------------------------------------------------------------------------- |
| Expected edges              | $\Theta(N^2)$                               | $N\langle z\rangle/2=\Theta(N)$                                                 |
| Expected degree             | $\langle z\rangle\sim pN\to\infty$          | Constant                                                                        |
| Degree law                  | $\operatorname{Bin}(N-1,p)$                 | $\longrightarrow\operatorname{Poisson}(\langle z\rangle)$                       |
| Relative degree variability | $\sigma_z/\langle z\rangle\to0$             | $\to1/\sqrt{\langle z\rangle}$                                                  |
| Clustering                  | $\approx p$, nonzero                        | $\approx\langle z\rangle/N\to0$                                                 |
| Typical distances           | Bounded; diameter $2$ with high probability | $\sim\log N/\log\langle z\rangle$ **if $\langle z\rangle>1$**, within the giant |
| Connectivity                | Connected with high probability             | Not connected with high probability for fixed $\langle z\rangle$                |

### Component structure within the sparse regime

| Expected degree | Largest component | Network behaviour |
|---|---|---|
| $\langle z\rangle<1$ | $O(\log N)$ | **Subcritical:** no giant component |
| $\langle z\rangle=1$ | Order $N^{2/3}$ | **Critical:** onset of the phase transition; still no positive giant fraction |
| $\langle z\rangle>1$ | $\approx SN$, where $S=1-e^{-\langle z\rangle S}>0$ | **Supercritical:** a giant component, but not full connectivity |


> [!exam] Remember
> - **Fit:** $\widehat p=2L^*/[N(N-1)]$ and $\langle z\rangle=2L^*/N$.
> - **Exact laws:** $L\sim\operatorname{Bin}(Y,p)$ and $z_i\sim\operatorname{Bin}(N-1,p)$.
> - **Sparse Poisson limit:** $p=\langle z\rangle/(N-1)$ with $\langle z\rangle$ fixed.
> - **Clustering:** $C_{\mathrm{net}}\approx p$; it vanishes in sparse ER.
> - **Giant threshold:** $\langle z\rangle=1$; **connectivity scale:** $\langle z\rangle\sim\log N$.
> - **Typical distances:** logarithmic only in the sparse **supercritical** giant component; do not confuse the estimate with an exact diameter formula.

> [!code]- NetworkX (interpretation)
> ```python
> G = nx.erdos_renyi_graph(N, p, seed=13)  # Independent edges: G(N,p)
> H = nx.gnm_random_graph(N, L, seed=13)   # Exactly L edges: G(N,L)
> ```

---
Related: [[Random graph ensembles]] · [[Configuration model]] · [[Percolation and robustness]] · [[Small-world networks]]
