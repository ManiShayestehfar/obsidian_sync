---
tags: [data5441, ch03, models]
aliases: [ER graph, Poisson random graph, G(N,p), Giant component]
---
# Erdős–Rényi graphs

> [!abstract] Summary
> $G(N,p)$ makes every link independent with probability $p$. It has binomial (Poisson in the sparse limit) degrees, clustering $\approx p$, distances $\sim\log N$, and a giant component once $\langle z\rangle>1$. It is the baseline that real networks are compared with.
> Chapter: [[Ch03 Random graph models]]

> [!definition] $G(N,p)$
> Each of the $Y=\binom N2$ node pairs is a link independently with probability $p$. A particular graph $g$ has probability
> $$P(g)=p^{L(g)}(1-p)^{Y-L(g)} .$$
> There is no binomial coefficient: that belongs to the distribution of $L$, not to the probability of one graph.

> [!theorem] Links and degrees
> $$L\sim\mathrm{Bin}(Y,p),\quad \langle L\rangle=pY;\qquad z_i\sim\mathrm{Bin}(N-1,p),\quad \langle z\rangle=p(N-1),\quad \sigma_z^2=(N-1)p(1-p).$$
> Each follows by writing the quantity as a sum of independent Bernoulli$(p)$ link indicators. Degrees of different nodes are weakly dependent, because they share the indicator of the link between them.

> [!proposition] Fitting ER to data
> The maximum-likelihood (and moment-matching) estimate is
> $$\hat p=\frac{L}{Y}=\frac{2L}{N(N-1)},\qquad\text{so that}\quad \langle z\rangle_{ER}=\hat p(N-1)=\frac{2L}{N}.$$
> The fitted ER graph has the **same average degree** as the data.

> [!theorem] Poisson limit (sparse regime)
> If $p=c/(N-1)$ with $c$ fixed, then for each fixed $z\ge0$,
> $$\binom{N-1}{z}p^z(1-p)^{N-1-z}\ \longrightarrow\ e^{-c}\frac{c^z}{z!}\qquad(N\to\infty).$$
> Hence $\sigma_z/\langle z\rangle\to1/\sqrt c$.

> [!proof]-
> $\binom{N-1}{z}\big(\frac c{N-1}\big)^z=\frac{(N-1)(N-2)\cdots(N-z)}{(N-1)^z}\frac{c^z}{z!}\to\frac{c^z}{z!}$, since $z$ is fixed. Also $\big(1-\frac c{N-1}\big)^{N-1-z}\to e^{-c}$. A Poisson$(c)$ variable has variance $c$, so $\sigma_z/\langle z\rangle=\sqrt c/c$. $\square$

> [!definition] Dense vs sparse ER
> - **Fixed $p$:** $\langle z\rangle=p(N-1)\to\infty$, so the graph is dense, and $\sigma_z/\langle z\rangle\to0$.
> - **Fixed $\langle z\rangle=c$:** $p=c/(N-1)\to0$, so the graph is sparse, with Poisson degrees and $C\approx p\to0$.

> [!theorem] Clustering and distances
> $C\approx p=\langle z\rangle/(N-1)$. In the sparse regime with $c>1$, typical distances in the giant component scale as $\ell\approx\dfrac{\log N}{\log\langle z\rangle}$.

> [!proof]- Heuristic for $\ell$
> In a locally tree-like graph, about $\langle z\rangle^d$ nodes lie at distance $d$ from a given node. Setting $\langle z\rangle^\ell\approx N$ gives $\ell\approx\log N/\log\langle z\rangle$.

## Giant component

> [!theorem] Giant component of sparse ER
> Let $\langle z\rangle=c$ be fixed and $N\to\infty$. The fraction $S$ of nodes in the largest component satisfies
> $$S=1-e^{-cS}.$$
> - For $c\le1$, the only solution is $S=0$: there is no giant component.
> - For $c>1$, there is a unique positive solution, which is the physical one.
>
> The transition is at $\langle z\rangle=1$. Near it, $S\approx2(c-1)$ for $c\downarrow1$. Reference values: $S(2)\approx0.797$, $S(3)\approx0.940$.

> [!proof]-
> Let $u$ be the probability that a node is **not** in the giant component. A node is outside it iff each of its neighbours fails to connect it, independently with probability $u$ each in the tree-like limit. Averaging over Poisson$(c)$ degrees gives
> $$u=\sum_z e^{-c}\frac{c^z}{z!}u^z=e^{c(u-1)} .$$
> With $S=1-u$ this is $S=1-e^{-cS}$.
> Let $f(S)=1-e^{-cS}-S$. Then $f(0)=0$, $f'(0)=c-1$, $f''<0$ and $f(1)<0$. If $c\le1$, concavity forces $f<0$ on $(0,1]$, so there is no positive root. If $c>1$, $f$ is positive just above $0$ and negative at $1$, and concavity gives exactly one positive root. $\square$

> [!remark] Giant ≠ connected
> Whole-graph connectivity needs $p\gtrsim\log N/N$, i.e. $\langle z\rangle\gtrsim\log N$. For fixed $c>1$, a positive fraction of nodes stays outside the giant component.

![[er-giant-component.png|600]]

> [!exam] Typical questions
> Trial 1 Q4 and Trial 1 Q6 / Trial 2 Q4 ask for:
> - $p=2L/[N(N-1)]$, $\langle z\rangle=2L/N$, $C\approx p$;
> - "$p=12/N$: sparse or dense?" Sparse, since $\langle z\rangle\to12$.
> - "For which $N$ is the graph complete?" $p=1$.
> - "For which $N$ is $C=0.2$?" $12/N=0.2\Rightarrow N=60$.
> - $\sigma_z/\langle z\rangle\approx1/\sqrt{\langle z\rangle}$.
>
> ER fails to reproduce **high clustering** and **broad degree distributions**.

> [!code]- NetworkX (tutorial 3)
> ```python
> G = nx.erdos_renyi_graph(N, p, seed=13)        # G(N,p)
> G = nx.gnm_random_graph(N, L, seed=13)        # G(N,L)
> S = len(max(nx.connected_components(G), key=len)) / N
> ```

> [!selftest]- Self-test
> 1. Why does the fitted ER graph have the same $\langle z\rangle$ as the data? — Because $\hat p=L/Y$ gives $\langle L\rangle=L$.
> 2. Solve the threshold: at what $\langle z\rangle$ does the giant component appear? — At $\langle z\rangle=1$.
> 3. Why is ER clustering small in sparse graphs? — Because $C\approx p\to0$.

---
Related: [[Random graph ensembles]] · [[Configuration model]] · [[Percolation and robustness]] · [[Small-world networks]]
