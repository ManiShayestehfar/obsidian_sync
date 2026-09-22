---
type: lecture-export
week: 6
source_pages: 11
status: visually-checked-paraphrase
tags: [DATA5441, lecture]
---

# Week 6 - Metropolis-Hastings and exponential random graphs

[[00_HOME]] · [[Tutorial 6 - guide]] · [[Newman reading map]] · [[Corrections and caveats]]

Source: `Notes Week 6 - 2026.pdf`; page numbers below refer to this supplied PDF.

Page-by-page mathematical transcription and paraphrase of the supplied handwritten lecture. Equations have been typeset; diagrams and the complete original page are retained in each image. Added explanations, corrections and ambiguities are identified in the text. This is not a verbatim diplomatic transcription.

## Page 01 - Beyond uniform constrained ensembles

The lecture reviews the spaces of simple labelled graphs with (1) fixed $N$, (2) fixed $N,L$, and (3) fixed degree sequence. It asks how to reproduce additional observed statistics, such as clustering, when an exactly preserving graph move is hard to construct. The November 17 network is used as an example with observed clustering around $0.53$ and a betweenness statistic to compare against a fitted model.

The next step is to change probabilities on a graph space rather than impose every observed statistic as an exact hard constraint.

> [!example]- Original page 1
> ![[w6-p01.jpg]]

## Page 02 - Non-uniform sampling

Let $x(g)$ be a graph statistic and $x^*$ its observed value. Seek a distribution satisfying
$$\sum_{g\in\Omega}p(g)x(g)=x^*.$$
This is an expectation constraint: individual sampled graphs can have $x(g)\ne x^*$. A non-uniform target can make otherwise rare graphs more common. Once graphs are sampled from that target, ordinary averages estimate its expectations; multiplying again by $p(g)$ would change the estimand.

> [!example]- Original page 2
> ![[w6-p02.jpg]]

## Page 03 - Proposals and acceptance

Decompose an off-diagonal transition into proposal and acceptance:
$$W(g\to h)=\Pi(h\mid g)a(g,h),\quad h\ne g.$$
The remaining probability is assigned to staying at $g$. Detailed balance asks for
$$p(g)\Pi(h\mid g)a(g,h)=p(h)\Pi(g\mid h)a(h,g).$$
Rejections count as Markov-chain steps. The proposal distribution and target distribution are separate objects. See [[MCMC and detailed balance]].

> [!example]- Original page 3
> ![[w6-p03.jpg]]

## Page 04 - Metropolis–Hastings acceptance

For a proposed move with the relevant denominator positive, define
$$R(g,h)=\frac{p(h)\Pi(g\mid h)}{p(g)\Pi(h\mid g)},\qquad a(g,h)=\min\{1,R(g,h)\}.$$
The reverse ratio is $1/R$ when both directions have positive mass, which verifies detailed balance by considering $R\le1$ and $R>1$. If the proposal is symmetric, the proposal probabilities cancel and $a=\min\{1,p(h)/p(g)\}$. An unknown common normalising constant also cancels.

> [!example]- Original page 4
> ![[w6-p04.jpg]]

## Page 05 - Sampling algorithm

Choose an initial state in the target support. Repeatedly propose $h$, draw $U\sim\mathrm{Uniform}(0,1)$, accept if $U<a(g,h)$ and otherwise retain $g$. Record the current state or statistic, including repeats. Allow burn-in and assess correlation.

The lecture uses positive target probabilities to simplify ratios. More generally zero-probability states require explicit support handling; irreducibility must hold on the support actually being sampled. A high acceptance rate alone does not demonstrate rapid exploration.

> [!example]- Original page 5
> ![[w6-p05.jpg]]

## Page 06 - Several constraints do not determine a distribution

For observables $x_1,\ldots,x_m$ impose
$$\sum_gp(g)=1,\qquad\sum_gp(g)x_i(g)=x_i^*,\quad i=1,\ldots,m.$$
Usually there are vastly more graph probabilities than equations. An additional principle is needed to select a distribution. Some collections of desired moments may be infeasible on the chosen graph space.

> [!example]- Original page 6
> ![[w6-p06.jpg]]

## Page 07 - Maximum entropy

For a finite labelled graph space with counting measure, maximise
$$S[p]=-\sum_gp(g)\log p(g),\qquad 0\log0:=0.$$
With normalisation alone, differentiating the Lagrangian gives a constant probability for every graph, hence $p(g)=1/|\Omega|$. Uniformity depends on what is counted as a state; uniform labelled graphs and uniform isomorphism classes are different ensembles.

> [!example]- Original page 7
> ![[w6-p07.jpg]]

## Page 08 - Deriving the exponential family

Using multipliers $\beta_i$ with the lecture’s positive-sign convention, stationarity yields
$$p_{\boldsymbol\beta}(g)=\frac{\exp[\sum_i\beta_i x_i(g)]}{Z(\boldsymbol\beta)},\qquad Z(\boldsymbol\beta)=\sum_{h\in\Omega}\exp[\sum_i\beta_i x_i(h)].$$
Choose the multipliers to reproduce the desired expectations. Entropy is strictly concave on the probability simplex, so a feasible maximum distribution is unique, though redundant statistics can make the parameters non-unique. Boundary constraints may require limiting infinite parameters. Other texts write a minus sign in the exponent; change the multiplier sign consistently.

> [!example]- Original page 8
> ![[w6-p08.jpg]]

## Page 09 - Exponential random graph models

An ERGM specifies the graph space, sufficient statistics and parameters. The edge-count example on all simple labelled graphs has
$$p_\beta(g)=\frac{e^{\beta L(g)}}{(1+e^\beta)^Y},\qquad Y=\binom N2.$$
Thus edges are independent with
$$q=\frac{e^\beta}{1+e^\beta},\qquad \beta=\log\frac q{1-q}.$$
This is $G(N,q)$. On a space where $L$ is already fixed, a term $\beta L$ is constant and changes no relative probabilities. Hard constraints and expectation constraints are not interchangeable. See [[Maximum entropy and ERGMs]].

> [!example]- Original page 9
> ![[w6-p09.jpg]]

## Page 10 - Fitting a multiplier by simulation

For a symmetric proposal, ERGM acceptance is
$$a(g,h)=\min\{1,\exp[\boldsymbol\beta\cdot(\mathbf x(h)-\mathbf x(g))]\}.$$
The partition function cancels at fixed parameters. Simulate at several trial values of $\beta$ and locate where the estimated mean statistic matches $x^*$. The lecture illustrates this with a grid and an interpolated intersection.

**Added explanation:** in a one-statistic model,
$$\frac{d\log Z}{d\beta}=\mathbb E_\beta[x],\qquad\frac{d\mathbb E_\beta[x]}{d\beta}=\operatorname{Var}_\beta(x)\ge0.$$
A noisy estimated curve need not appear monotone when simulations mix poorly or are short.

> [!example]- Original page 10
> ![[w6-p10.jpg]]

## Page 11 - Using the fitted ensemble

After choosing a fitted parameter, sample the fitted model and compare another observable with its empirical value. Match the definition of the observable, including whether betweenness means a named vertex’s value or the maximum over all vertices.

Burn-in and correlation times depend on the fitted parameter. Values suitable for a uniform ensemble may be inadequate after strongly weighting clustering. Report Monte Carlo uncertainty and inspect multiple starting states where possible. A poorly mixing chain can appear stable while remaining in only one region of graph space. See [[Simulation and uncertainty]] and [[Tutorial 6 - guide]].

> [!example]- Original page 11
> ![[w6-p11.jpg]]

