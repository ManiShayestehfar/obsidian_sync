---
tags: [data5441, ch05, models]
aliases: [Barabási–Albert, BA model, Rich get richer]
---
# Preferential attachment (Barabási–Albert)

> [!abstract] Summary
> **Growth + preferential attachment** produces a power-law degree distribution with $\gamma=3$. Old nodes become hubs. $\langle z\rangle\to2m$, and clustering vanishes as $N$ grows.
> Chapter: [[Ch05 Mechanistic models]]

> [!definition] BA model *(formula sheet)*
> Start from a small seed graph. At each step add one node with $m$ links to existing nodes. Each link attaches to node $i$ with probability
> $$\pi_i=\frac{z_i}{\sum_jz_j}=\frac{z_i}{2L}.$$
> After $t$ steps, $N\approx t$ and $L\approx mt$, so $\langle z\rangle=2L/N\to2m$.

> [!theorem] Degree growth and degree distribution (continuum approximation)
> A node born at time $t_i$ with $z_i(t_i)=m$ has
> $$z_i(t)\approx m\sqrt{t/t_i},\qquad P(z)\approx2m^2z^{-3}\quad(\gamma=3).$$
> The exact rate-equation solution is $P(z)=\dfrac{2m(m+1)}{z(z+1)(z+2)}$ for $z\ge m$, which also decays as $z^{-3}$.

> [!proof]-
> Each step adds $m$ links, and node $i$ receives each with probability $z_i/2L\approx z_i/(2mt)$. Hence
> $$\frac{dz_i}{dt}=m\frac{z_i}{2mt}=\frac{z_i}{2t}\ \Rightarrow\ \ln z_i=\tfrac12\ln t+c\ \Rightarrow\ z_i(t)=m\sqrt{t/t_i}.$$
> Arrival times are uniform on $(0,t)$, so
> $$P_>(z)=\Pr\big(z_i(t)\ge z\big)=\Pr\Big(t_i\le\frac{m^2t}{z^2}\Big)=\frac{m^2}{z^2}.$$
> Differentiating, $P(z)=-\dfrac{dP_>}{dz}=2m^2z^{-3}$. $\square$

> [!remark] What BA does and does not explain
> - It produces broad degrees, hubs, and an advantage for early nodes.
> - Its relative variability $\sigma_z/\langle z\rangle$ is much larger than ER's.
> - It does **not** produce high clustering: $C\to0$. For $m=1$ the graph is a tree.
> - The exponent is fixed at $3$. A power law in data does not prove that preferential attachment generated it.

![[preferential-attachment-growth.png|550]]

> [!exam] Matching BA to a network (Trial 1 Q6c / Trial 2 Q4d)
> To match $\langle z\rangle\approx12$, take $2m=12\Rightarrow m=6$. Between ER and BA with equal $\langle z\rangle$, **BA** has the larger $\sigma_z/\langle z\rangle$. This tests whether a real network has hubs and degree heterogeneity beyond Poisson.

> [!code]- NetworkX (tutorial 5)
> ```python
> G = nx.barabasi_albert_graph(N, m, seed=13)
> z = np.array([d for _, d in G.degree()]); z.std()/z.mean()
> ```

> [!selftest]- Self-test
> 1. What is $\langle z\rangle$ of BA as $N\to\infty$? — $2m$.
> 2. Derive $\gamma=3$ in three lines. — See the proof above.
> 3. Does BA reproduce social-network clustering? — No.

---
Related: [[Power laws]] · [[Small-world networks]] · [[Erdos-Renyi graphs]]
