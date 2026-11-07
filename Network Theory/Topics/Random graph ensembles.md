---
tags: [data5441, ch03, models]
aliases: [Random graph model, Null model, Ensemble]
---
# Random graph ensembles

> [!abstract] Summary
> A random-graph model is a set of graphs with a probability on each. Choosing what is held fixed ($N$, $L$, the degrees, …) decides which question a null-model comparison answers.
> Chapter: [[Ch03 Random graph models]]

> [!definition] Random graph (ensemble)
> A random graph $\mathcal G$ is a set $\Omega$ of graphs together with probabilities $p(g)\ge0$, $\sum_{g\in\Omega}p(g)=1$. Unless stated otherwise, $\Omega$ consists of **labelled** simple graphs.

> [!proposition] Sizes of graph spaces
> With $Y=\binom N2$:
> $$|\Omega_N|=2^{Y}\quad(\text{all simple graphs on }N\text{ labelled nodes}),\qquad |\Omega_{N,L}|=\binom{Y}{L}\quad(\text{exactly }L\text{ links}).$$

> [!proof]-
> Each of the $Y$ node pairs is independently either a link or not, giving $2^Y$ graphs. A graph with exactly $L$ links is a choice of $L$ pairs from $Y$, giving $\binom YL$ graphs. $\square$

| Model | Fixed | Probability |
|---|---|---|
| Uniform on $\Omega_N$ | $N$ | $2^{-Y}$; links i.i.d. Bernoulli$(1/2)$ |
| $G(N,p)$ (ER/Poisson) | $N,p$ | $p^{L(g)}(1-p)^{Y-L(g)}$ |
| $G(N,L)$ | $N,L$ | $1/\binom YL$ on $\Omega_{N,L}$ |
| Configuration / fixed degrees | every $z_i$ | uniform over admissible graphs |
| ERGM | expected statistics | $e^{\beta\cdot x(g)}/Z$ |
| SBM | blocks $b_i$, $p_{rs}$ | independent links given blocks |

Nesting: $\Omega_{\mathbf z}\subseteq\Omega_{N,L}\subseteq\Omega_N$. Each extra constraint asks a different question: is a pattern surprising given the size, given the density, or given every degree?

> [!theorem] Conditioning ER on $L$ gives $G(N,L)$
> For $0<p<1$, conditioning $G(N,p)$ on $L(g)=\ell$ gives the uniform law on $\Omega_{N,\ell}$.

> [!proof]-
> Every $g$ with $L(g)=\ell$ has the same probability $p^\ell(1-p)^{Y-\ell}$. Dividing by $\Pr(L=\ell)=\binom Y\ell p^\ell(1-p)^{Y-\ell}$ gives $1/\binom Y\ell$. $\square$

> [!remark] Uniform graphs are dense
> Under the uniform law on $\Omega_N$, $L\sim\mathrm{Bin}(Y,1/2)$, with mean $Y/2$ and standard deviation $\sqrt Y/2$. A uniformly random graph is therefore almost surely near density $1/2$. Rejection sampling to obtain a sparse graph would almost never succeed. This motivates MCMC on constrained spaces; see [[Markov chain Monte Carlo on graphs]].

> [!example] Trial Exam 2, Q2
> On $\Omega_N$, consider $p_1(g)=1/|\Omega|$, $p_2(g)=L(g)^2/Z$ and $p_3(g)=e^{\beta L(g)}/Z_\beta$.
> - $|\Omega|=2^Y$.
> - $\langle L\rangle_2>\langle L\rangle_1$, because $p_2$ up-weights graphs with many links.
> - $\langle L\rangle_3=\langle L\rangle_1$ iff $\beta=0$.
> - For the empty graph: $p_1=2^{-Y}$, $p_2=0$, $p_3=1/Z_\beta$.

> [!remark] How to compare a network with a null model
> Generate many independent draws from the fitted ensemble. Compare the observed statistic with the **ensemble distribution** (its spread), not with the standard error of the ensemble mean. Matching one statistic, such as $L$, does not mean the model explains the others.

---
Related: [[Erdos-Renyi graphs]] · [[Configuration model]] · [[Maximum entropy and ERGMs]] · [[Stochastic block models]]
