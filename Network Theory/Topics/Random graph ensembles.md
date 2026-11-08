---
tags: [data5441, ch03, models]
aliases: [Random graph model, Null model, Ensemble]
---

---
# Random graph ensembles

> [!abstract] Summary
> A **random graph** is a probability distribution over possible graphs. Its **sample space** specifies which graphs are allowed; its **probabilities** specify how likely they are. We use ensembles as null models to ask whether an observed network property can be explained by specified constraints alone.
> Chapter: [[Ch03 Random graph models]] · Lecture: **Week 3, pp. 30–35**

## 1. Why introduce random graphs?

A single graph describes an observed network. A **random-graph model** describes many possible networks generated under chosen assumptions. It lets us predict typical properties and compare observations against a baseline.

The central modelling choice is **what to preserve and what to randomise**: the number of nodes, the number of links, the degree sequence, or other properties.

> [!definition] Random-graph ensemble
> An ensemble is a pair $(\Omega,p)$, where $\Omega$ is a set of admissible graphs and
> $$p(g)\ge0,\qquad \sum_{g\in\Omega}p(g)=1.$$
> A random graph $G$ is drawn from this distribution. Throughout, graphs are **labelled, simple and undirected**, unless otherwise specified.

## 2. Observables and ensemble averages

A **network observable** is a numerical quantity $X:\Omega\to\mathbb R$, such as the number of links, clustering coefficient or largest-component size. It varies between graph realisations.

> [!definition] Ensemble expectation and variance
> $$\mathbb E[X]=\sum_{g\in\Omega}p(g)X(g), \qquad \sigma_X^2(X)= \langle X^2 \rangle - \langle X\rangle^2$$
> For a discrete value $x$, its probability is
> $$\Pr(X=x)=\sum_{g\in\Omega:\,X(g)=x}p(g).$$

The **ensemble mean** is not the value of $X$ in every sampled graph. Its standard deviation measures graph-to-graph fluctuations. Whether an observable concentrates near its mean for large $N$ depends on the model and observable; it is **not automatic**.

## 3. Counting admissible graphs

For $N$ labelled vertices, let $Y=\binom N2=N(N-1)/2$ be the number of possible undirected edges.

> [!proposition] Two basic sample spaces
> - **Fixed $N$:** $\Omega_N$ contains all simple graphs on these vertices:
>   $$\boxed{|\Omega_N|=2^Y.}$$
> - **Fixed $N,L$:** $\Omega_{N,L}$ contains graphs with exactly $L$ links:
>   $$\boxed{|\Omega_{N,L}|=\binom YL.}$$
> **Reason:** each potential edge is present or absent in $\Omega_N$; specifying $L$ edges instead means choosing $L$ of the $Y$ possible pairs.

### Uniform does not mean uniform in the number of edges

If every graph in $\Omega_N$ is equally likely, $p(g)=2^{-Y}$. Then a particular $g$ has probability $2^{-Y}$, but the event **$L(g)=\ell$** includes $\binom Y\ell$ different graphs:
$$
\boxed{\Pr(L=\ell)=\binom Y\ell\,2^{-Y},\qquad L\sim\mathrm{Bin}(Y,1/2).}
$$
Consequently,
$$
\mathbb E[L]=\frac Y2,\qquad \operatorname{Var}(L)=\frac Y4,
\qquad \operatorname{Var}\!\left(\frac LY\right)=\frac1{4Y}.
$$
As $N\to\infty$, $L/Y\to1/2$ in probability. Thus a **typical uniformly chosen graph is dense**, with about half of all possible edges, even though sparse graphs belong to $\Omega_N$.

> [!proof]- Why the edge density concentrates
> For any $\varepsilon>0$, Chebyshev's inequality gives
> $$\Pr\!\left(\left|\frac LY-\frac12\right|\ge\varepsilon\right)\le\frac1{4Y\varepsilon^2}\longrightarrow0.$$
> The lecture also gives a stronger large-deviation estimate: for $0<\alpha<1$ and $\ell=\alpha Y$ an integer,
> $$\log\Pr(L=\ell)=-Y I(\alpha)+O(\log Y),$$
> $$I(\alpha)=\log2+\alpha\log\alpha+(1-\alpha)\log(1-\alpha).$$
> Here $I(\alpha)\ge0$, with equality only at $\alpha=1/2$; densities away from $1/2$ are exponentially unlikely.

## 4. Which ensemble is the appropriate null model?

| Ensemble | What is fixed? | Distribution within the admissible space |
|---|---|---|
| Uniform on $\Omega_N$ | $N$ | Every graph has probability $2^{-Y}$ |
| **Erdős–Rényi** $G(N,p)$ | $N$ and link parameter $p$ | Each potential edge is independently present with probability $p$; **$L$ fluctuates** |
| $G(N,L)$ | $N$ and **exactly** $L$ | Uniform on $\Omega_{N,L}$ |
| Fixed degree sequence | $N$ and each $z_i$ | Can be uniform over *simple* realisations of that sequence |
| SBM | Block labels and link probabilities $p_{rs}$ | Independent edges conditional on blocks |
| ERGM | Parameters controlling expected statistics | $p_\beta(g)\propto e^{\beta\cdot X(g)}$ |

The admissible spaces satisfy
$$\Omega_{\boldsymbol z}\subseteq\Omega_{N,L}\subseteq\Omega_N,\qquad \sum_i z_i=2L.$$
More constraints mean **fewer admissible graphs**, but the probability distribution still needs to be specified. For the configuration model, ordinary random stub pairing allows self-loops and parallel edges; **conditioning on simplicity** gives a uniform distribution over labelled simple graphs with the prescribed degrees.

> [!proposition] Conditioning $G(N,p)$ on the edge count
> For $0<p<1$, the law of $G(N,p)$ given $L=\ell$ is precisely $G(N,\ell)$:
> $$\Pr(G=g\mid L=\ell)=\frac{p^\ell(1-p)^{Y-\ell}}{\binom Y\ell p^\ell(1-p)^{Y-\ell}}=\boxed{\frac1{\binom Y\ell}}.$$
> Hence the distinction is **fixed $L$ versus fluctuating $L$**; even though links are independent in $G(N,p)$, they are *not* independent after conditioning on their total count.

## 5. Using an ensemble as a null model

Suppose an observed graph $g^*$ has a statistic $X(g^*)$. To ask whether it is unusual:
1. **Select constraints** that the model should preserve (e.g. $N$ or both $N,L$).
2. **Specify and fit** the probability law $p(g)$.
3. **Calculate or sample** the null distribution of $X(G)$.
4. **Compare** $X(g^*)$ with the null distribution and its fluctuations.

A fitted null model may match the number of edges by construction without matching clustering, path lengths or community structure. Compare with the **distribution of $X(G)$**, not just the uncertainty in the estimated mean. MCMC draws may be correlated; see [[Markov chain Monte Carlo on graphs]].

> [!exam] Essential distinctions
> - $p(g)$ = probability of **one particular graph**; $\Pr(L=\ell)$ = probability of **all graphs** with $\ell$ links.
> - Uniform over $\Omega_N$ means $G(N,1/2)$, **not** a uniform distribution over $L$.
> - $|\Omega_N|=2^{\binom N2}$ and $|\Omega_{N,L}|=\binom{\binom N2}{L}$.
> - A graph with atypically few links is rare under the uniform $\Omega_N$ model; use an appropriately constrained or sparse model instead.
> - Trial Exam 2, Q2 compares $p_1(g)=2^{-Y}$, $p_2(g)\propto L(g)^2$, and $p_3(g)\propto e^{\beta L(g)}$. The latter two alter probabilities **within the same graph space**; $\beta=0$ recovers the uniform model.

---
Related: [[Erdos-Renyi graphs]] · [[Configuration model]] · [[Maximum entropy and ERGMs]] · [[Stochastic block models]]
