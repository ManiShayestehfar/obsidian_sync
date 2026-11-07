---
tags: [data5441, ch02, foundations]
aliases: [Friendship paradox, Degree bias, Network sampling]
---
# Sampling and the friendship paradox

> [!abstract] Summary
> How you sample a network changes what you see. Picking a node, picking a link endpoint, and picking a random neighbour of a random node are different experiments. Endpoint sampling is degree-biased: "your friends have more friends than you".
> Chapter: [[Ch02 Centrality measures]]

> [!theorem] Degree-biased sampling (friendship paradox)
> Pick one of the $2L$ link endpoints uniformly at random and let $K$ be the degree of the node reached. Then
> $$\Pr(K=z)=\frac{zP(z)}{\langle z\rangle},\qquad \mathbb E[K]=\frac{\langle z^2\rangle}{\langle z\rangle}=\langle z\rangle+\frac{\sigma_z^2}{\langle z\rangle}\ \ge\ \langle z\rangle ,$$
> with equality iff all degrees are equal.

> [!proof]-
> Node $i$ owns $z_i$ of the $2L$ endpoints, so it is reached with probability $z_i/(2L)$. Summing over the $N_z=NP(z)$ nodes of degree $z$ gives $\Pr(K=z)=zNP(z)/(2L)=zP(z)/\langle z\rangle$.
> Then $\mathbb E[K]=\sum_z z\cdot zP(z)/\langle z\rangle=\langle z^2\rangle/\langle z\rangle$. Finally $\langle z^2\rangle=\langle z\rangle^2+\sigma_z^2$. $\square$

> [!definition] Excess degree
> The number of **other** links of the node reached is $K-1$. Its mean is
> $$\kappa=\frac{\langle z^2\rangle-\langle z\rangle}{\langle z\rangle}=\frac{\langle z^2\rangle}{\langle z\rangle}-1 .$$
> This branching factor drives the giant component, percolation and epidemics; see [[Configuration model]].

> [!proposition] Random neighbour of a random node
> Choose a node uniformly, then one of its neighbours uniformly (assume no isolated nodes). Then
> $$\mathbb E[z_J]=\frac1N\sum_{\{i,j\}\in\mathcal L}\Big(\frac{z_i}{z_j}+\frac{z_j}{z_i}\Big)\ \ge\ \frac{2L}N=\langle z\rangle ,$$
> using $a/b+b/a\ge2$. This is a different law from endpoint sampling, but it shows the same bias.

> [!theorem] Unbiasedness does not need independence
> If each observation $X_s$ has marginal law $p$, then $\hat\mu=\frac1R\sum_{s=1}^R f(X_s)$ satisfies $\mathbb E\hat\mu=\sum_xp(x)f(x)$. This follows from linearity of expectation alone. Correlations between the $X_s$ affect the variance, not the mean.

> [!remark] Other sampling schemes
> - **Induced node sample:** keep each node with probability $s$. Each link survives with probability $s^2$, so a sparse sample can be almost empty.
> - **Random walk:** on a connected undirected graph the stationary probability is $z_i/2L$ (degree-biased), by detailed balance on every link.
> - **Snowball sampling:** repeatedly adds neighbours, so it over-represents well-connected regions.

> [!selftest]- Self-test
> 1. On a star with $N$ nodes, what is the mean degree reached by endpoint sampling? — Half the endpoints are at the hub (degree $N-1$) and half at leaves (degree $1$), so the mean is $N/2$.
> 2. Why does $\langle z^2\rangle/\langle z\rangle$ diverge for heavy tails? — $\langle z^2\rangle$ diverges when $\gamma\le3$; see [[Power laws]].

---
Related: [[Centrality]] · [[Configuration model]] · [[Percolation and robustness]]
