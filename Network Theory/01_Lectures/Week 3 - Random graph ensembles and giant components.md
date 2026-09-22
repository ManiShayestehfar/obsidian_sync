---
type: lecture-export
week: 3
source_pages: 15
status: visually-checked-paraphrase
tags: [DATA5441, lecture]
---

# Week 3 - Random graph ensembles and giant components

[[00_HOME]] · [[Tutorial 3 - guide]] · [[Newman reading map]] · [[Corrections and caveats]]

Source: `Notes Week 3 - 2026.pdf`; page numbers below refer to this supplied PDF.

Page-by-page mathematical transcription and paraphrase of the supplied handwritten lecture. Equations have been typeset; diagrams and the complete original page are retained in each image. Added explanations, corrections and ambiguities are identified in the text. This is not a verbatim diplomatic transcription.

## Page 01 - Why use network models

Weeks 1–2 characterise networks; Week 3 begins modelling them. The lecture gives three purposes: infer how a network could have arisen; simulate possible configurations or scenarios; and construct a **null model** against which to assess empirical observations.

A null model formalises what is retained and what is randomised. A surprising statistic is evidence against that specified model, not proof of a unique alternative mechanism.

> [!example]- Original page 1
> ![[w3-p01.jpg]]

## Page 02 - Deterministic graphs and random graph ensembles

A ring $C_N$ has $z_i=2$, zero degree variance and diameter $\lfloor N/2\rfloor$. Its transitivity is zero for $N\ge4$ (the $N=3$ ring is a triangle).

A random graph model is a probability distribution on a set $\Omega$ of graphs:
$$p(g)\ge0,\qquad\sum_{g\in\Omega}p(g)=1.$$
One may fix selected properties and leave the rest random. For labelled graphs with $N=4$ and $L=3$, there are $\binom63=20$ possibilities, each with probability $1/20$ under the uniform model. The page draws several examples rather than every graph.

> [!example]- Original page 2
> ![[w3-p02.jpg]]

## Page 03 - Statistics of a graph ensemble

For a graph statistic $x:\Omega\to\mathbb R$,
$$\mathbb E_p[x]=\sum_gp(g)x(g),\qquad \sigma_x=\sqrt{\mathbb E_p[x^2]-\mathbb E_p[x]^2},$$
$$\Pr(x(G)=a)=\sum_gp(g)\mathbf1\{x(g)=a\}.$$
The lecture notes that some observables concentrate as $N$ increases. **Qualification:** neither vanishing variance nor concentration holds for arbitrary unnormalised statistics. The next example concentrates in the edge density $L/\binom N2$, while the variance of the raw edge count grows.

> [!example]- Original page 3
> ![[w3-p03.jpg]]

## Page 04 - Uniform graphs with fixed number of vertices

Let $Y=\binom N2$. On all $2^Y$ labelled simple graphs, choose $p(g)=2^{-Y}$. There are $\binom Y\ell$ graphs with $\ell$ edges, so
$$\Pr(L=\ell)=2^{-Y}\binom Y\ell,\quad \mathbb E[L]=Y/2,\quad \operatorname{Var}(L)=Y/4.$$
The mean follows from differentiating $(1+x)^Y$ and setting $x=1$, or by summing the $Y$ Bernoulli edge indicators. Thus $L$ is of order $N^2$ and the typical graph is dense.

**Correction to the page’s concentration statement:** point probabilities tending to zero away from the mean do not by themselves establish concentration. In fact the probability of the most likely individual edge count also tends to zero. Use the scaled edge density and a deviation event.

> [!example]- Original page 4
> ![[w3-p04.jpg]]

## Page 05 - Stirling approximation and large deviations

For $L=\alpha Y$ an integer and $0<\alpha<1$,
$$\Pr(L=\alpha Y)=2^{-Y}\frac{Y!}{(\alpha Y)![(1-\alpha)Y]!}.$$
Using $\log(n!)=n\log n-n+O(\log n)$ gives
$$\log\Pr(L=\alpha Y)=-YI(\alpha)+O(\log Y),$$
$$I(\alpha)=\log2+\alpha\log\alpha+(1-\alpha)\log(1-\alpha).$$
Here $I'(\alpha)=\log[\alpha/(1-\alpha)]$ and $I''(\alpha)=1/\alpha+1/(1-\alpha)>0$. Its unique minimum is $I(1/2)=0$, while $I(\alpha)>0$ for $\alpha\ne1/2$. The endpoints have probability $2^{-Y}$ directly. This explains exponentially small probabilities for edge densities separated from $1/2$.

> [!example]- Original page 5
> ![[w3-p05.jpg]]

## Page 06 - What actually concentrates

The drawing shows increasingly narrow distributions of $L/Y$ centred at $1/2$. A direct proof is
$$\mathbb E[L/Y]=1/2,\qquad \operatorname{Var}(L/Y)=1/(4Y),$$
$$\Pr\left(\left|L/Y-1/2\right|>\varepsilon\right)\le\frac1{4Y\varepsilon^2}\longrightarrow0$$
for each fixed $\varepsilon>0$, by Chebyshev’s inequality. This added proof makes the lecture’s sketch precise. It does not claim $L$ itself becomes deterministic.

> [!example]- Original page 6
> ![[w3-p06.jpg]]

## Page 07 - Erdős–Rényi graphs and fitting

For $G(N,q)$, each possible edge is present independently with probability $q$. A particular graph has
$$p(g)=q^{L(g)}(1-q)^{Y-L(g)},\qquad\mathbb E[L]=qY.$$
Fitting an observed graph with $N^*$ vertices and $L^*$ edges gives
$$N=N^*,\qquad \hat q=\frac{L^*}{\binom{N^*}2}=\frac{\langle z\rangle_{\mathrm{obs}}}{N^*-1}.$$
This matches the **expected** edge count; individual samples do not all contain $L^*$ edges. The uniform fixed-edge-count model $G(N,L^*)$ is different. The expression for $p(g)$ contains no binomial coefficient because it describes one labelled graph; the edge-count distribution does contain that coefficient.

> [!example]- Original page 7
> ![[w3-p07.jpg]]

## Page 08 - Degree distribution and dense versus sparse regimes

For a fixed vertex,
$$\Pr(z=k)=\binom{N-1}kq^k(1-q)^{N-1-k},$$
$$\mathbb E[z]=(N-1)q=:c,\qquad \operatorname{Var}(z)=(N-1)q(1-q).$$
- Fixed $q\in(0,1)$ as $N\to\infty$: dense regime, $c$ grows linearly and the coefficient of variation is $\sqrt{(1-q)/c}\to0$.
- $q=c/(N-1)$ with fixed $c>0$: sparse regime, $z$ converges in distribution to $\mathrm{Poisson}(c)$, with mass $e^{-c}c^k/k!$, variance $c$ and coefficient of variation $1/\sqrt c$.

The handwritten variance $c$ is the Poisson-limit result, not the exact binomial variance. Also $1/\sqrt c<1$ only when $c>1$.

> [!example]- Original page 8
> ![[w3-p08.jpg]]

## Page 09 - Clustering and branching intuition

Conditional on a vertex having at least two neighbours, any pair of its neighbours is joined with probability $q$, hence $\mathbb E[C_i\mid z_i\ge2]=q$. If $C_i=0$ for smaller degree, then $\mathbb E[\bar C]=q\Pr(z_i\ge2)$; “$C=q$” needs this convention caveat. Transitivity is typically of order $q$; a ratio of expectations is not automatically its expectation.

For fixed $c$, $q=c/(N-1)\to0$. Neighbourhoods can then be approximated locally by branching processes. In a regular tree of degree $k$, shells have $k(k-1)^{r-1}$ vertices. In sparse ER, the mean **excess degree** is $c$, so the relevant expected shell growth is approximately $c^r$.

The lecture mixes these two heuristics. They agree in spirit but the branching factor must be chosen for the model. See [[Configuration model and excess degree]].

> [!example]- Original page 9
> ![[w3-p09.jpg]]

## Page 10 - Short distances and the largest component

Branching expansion reaches order $N$ after about
$$r\approx\frac{\log N}{\log c},\qquad c>1.$$
This is a leading heuristic for typical distances inside the sparse ER giant component. The lecture uses it for diameter as well, writing an additional constant; do not treat that expression as a general exact diameter theorem. Extremal distances can be affected by long dangling branches. Both typical distances and diameter are of logarithmic order for a fixed strictly supercritical $c$, but their leading constants need not agree.

The page then asks how the fraction $K_1$ in the largest component varies with $c$. The following pages show a phase transition rather than a smooth increase from $c=0$.

> [!example]- Original page 10
> ![[w3-p10.jpg]]

## Page 11 - Self-consistency for the giant component

Order component sizes and let $K_a$ be each size divided by $N$, so $\sum_aK_a=1$. Let $u=1-K_1$ be the fraction outside the largest component.

In the large sparse limit, approximate $u$ by the probability that a vertex does not reach the giant component. For a potential neighbour $j$, failure through $j$ occurs either because there is no edge (probability $1-q$), or because there is an edge but it does not lead to the giant (probability approximately $qu$). This produces the branching/independence approximation on the next page; it is not an exact finite-$N$ identity.

> [!example]- Original page 11
> ![[w3-p11.jpg]]

## Page 12 - Deriving the giant-component equation

The self-consistency approximation is
$$u\approx(1-q+qu)^{N-1}=\left[1-\frac{c(1-u)}{N-1}\right]^{N-1}.$$
For fixed $c$, take $N\to\infty$ using $\log(1-\varepsilon)=-\varepsilon+O(\varepsilon^2)$:
$$u=e^{-c(1-u)},\qquad S:=1-u=1-e^{-cS}.$$
The appropriate solution corresponds to the smallest extinction probability $u\in[0,1]$, hence the largest solution $S\in[0,1]$. The finite graph’s random $K_1$ approaches this limiting giant fraction under the sparse ER model.

> [!example]- Original page 12
> ![[w3-p12.jpg]]

## Page 13 - Threshold at mean degree one

Compare $f(S)=1-e^{-cS}$ with $S$. Always $S=0$ is a solution. Since $f'(0)=c$ and $f''(S)=-c^2e^{-cS}<0$ for $c>0$:

- For $0<c\le1$, $f(S)<S$ for all $S>0$, so there is no positive solution.
- For $c>1$, $f(S)>S$ immediately to the right of zero, whereas $f(1)<1$. Strict concavity gives exactly one positive solution.

The phase transition occurs at $c=1$. The zero limiting fraction at or below the threshold does not say that finite graphs have no components. A positive giant fraction above it does not say the graph is connected. See [[Giant components and finite graphs]].

> [!example]- Original page 13
> ![[w3-p13.jpg]]

## Page 14 - Comparing observed networks with a null model

The page is a blank comparison table with columns for degree variability $\sigma_z/\langle z\rangle$, distance (mean or diameter), and clustering ($\bar C$ or $C_{\mathrm{net}}$).

For an empirical graph, fit the chosen baseline, sample multiple graph realisations and compare like-for-like statistics, including the same component and weighting conventions. Tutorial 3 supplies a two-standard-deviation compatibility rule; it is a heuristic, not a universal calibrated hypothesis test.

> [!example]- Original page 14
> ![[w3-p14.jpg]]

## Page 15 - Comparing model families

The page summarises lattices, regular random graphs, and dense/sparse ER graphs. A qualified version is:

| Family | Relative degree variation | Typical distance | Clustering |
| --- | --- | --- | --- |
| Fixed-range $d$-dimensional lattice | Zero if regular; boundary effects may vanish | Order $N^{1/d}$ | Depends on neighbourhood; positive with suitable diagonal/range edges |
| Fixed $k$-regular random graph, $k\ge3$ | Zero | Order $\log N$ | Tends to zero |
| ER, fixed $q\in(0,1)$ | Tends to zero | Bounded for large $N$ | Order $q$ |
| ER, fixed $c>1$ | Approximately $1/\sqrt c$ | Order $\log N$ within giant | Tends to zero |

The source’s “lattice has positive clustering” refers to a lattice with triangles, as in Tutorial 2’s diagonal-neighbour lattice. A nearest-neighbour square lattice has none. Random regular degree two requires separate treatment: it is a union of cycles, not the usual branching case.

> [!example]- Original page 15
> ![[w3-p15.jpg]]

