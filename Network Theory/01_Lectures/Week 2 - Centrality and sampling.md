---
type: lecture-export
week: 2
source_pages: 13
status: visually-checked-paraphrase
tags: [DATA5441, lecture]
---

# Week 2 - Centrality and sampling

[[00_HOME]] · [[Tutorial 2 - guide]] · [[Newman reading map]] · [[Corrections and caveats]]

Source: `Notes Week 2 - 2026.pdf`; page numbers below refer to this supplied PDF.

Page-by-page mathematical transcription and paraphrase of the supplied handwritten lecture. Equations have been typeset; diagrams and the complete original page are retained in each image. Added explanations, corrections and ambiguities are identified in the text. This is not a verbatim diplomatic transcription.

## Page 01 - What does central mean

The page compares a star, a $3\times3$ nearest-neighbour lattice and Zachary’s Karate Club network. Their drawings motivate the question: which vertices are important? A centre may have many neighbours, short distances to others, or control routes between groups. The measure must match the process being modelled. See [[Centrality and Perron-Frobenius]].

> [!example]- Original page 1
> ![[w2-p01.jpg]]

## Page 02 - Degree, distance and betweenness

1. **Degree:** larger $z_i$ means more direct contacts. A uniformly chosen edge endpoint is more likely to land at high-degree vertices.
2. **Distance:** smaller average distance $d_i$ means easier access to the rest of a connected graph. Closeness commonly uses $1/d_i$.
3. **Betweenness:** vertices are important if many shortest routes pass through them.

Let $\sigma_{st}$ count shortest paths from $s$ to $t$, and $\sigma_{st}(i)$ those with $i$ as an internal vertex. With unordered pairs in an undirected graph,
$$B_i=\sum_{\substack{s<t\\s,t\ne i}}\frac{\sigma_{st}(i)}{\sigma_{st}}.$$
Unreachable pairs contribute zero. The lecture writes a double sum over ordered pairs and discusses division by $N^2$. Normalisations and whether endpoints count vary; specify them before comparing numerical outputs. Ordered-pair counting doubles the undirected unnormalised result.

> [!example]- Original page 2
> ![[w2-p02.jpg]]

## Page 03 - Perron–Frobenius theorem

The next centralities reward connection to already central vertices. For a nonnegative irreducible square matrix $A$, the spectral radius $\rho(A)$ is a real eigenvalue, algebraically simple, with a strictly positive eigenvector unique up to scale. In an undirected network irreducibility means connectivity; in a directed network it means strong connectivity.

A useful bound is
$$\min_i\sum_jA_{ij}\le\rho(A)\le\max_i\sum_jA_{ij}.$$
The source states a weaker lower bound $\min_{ij}A_{ij}$ and describes the Perron eigenvector as real. Positivity is the property that makes it suitable as a centrality.

> [!important] Convergence qualification
> Irreducibility alone does not imply every other eigenvalue has strictly smaller modulus. That stronger property follows from primitivity. A connected bipartite undirected graph has eigenvalues $\rho$ and $-\rho$.

> [!example]- Original page 3
> ![[w2-p03.jpg]]

## Page 04 - Propagation and power iteration

Starting with a vector $x(0)$, propagate
$$x_i(t+1)=\sum_jA_{ij}x_j(t),\qquad x(t)=A^tx(0).$$
For a real symmetric $A$, choose an eigenbasis and write $x(0)=\sum_k a_kv_k$. Then
$$\rho^{-t}x(t)=a_1v_1+\sum_{k\ne1}a_k\left(\frac{\lambda_k}{\rho}\right)^tv_k.$$
If $a_1\ne0$ and $|\lambda_k|<\rho$ for all $k\ne1$, the remaining terms vanish and the direction approaches $v_1$. For a positive initial vector and positive Perron vector, $a_1>0$ in the symmetric case.

The lecture omits the strict spectral-gap condition. Connected bipartite graphs can oscillate; a generic directed matrix need not even have an eigenbasis. The positive eigenvector remains well-defined under irreducibility, independently of this particular convergence proof.

> [!example]- Original page 4
> ![[w2-p04.jpg]]

## Page 05 - Eigenvector centrality

Define $x$ by
$$Ax=\rho(A)x,\qquad x_i=\frac1{\rho(A)}\sum_jA_{ij}x_j,$$
with a chosen positive normalisation, e.g. $\|x\|_2=1$.

Two limitations motivate refinements. First, a vertex passes its entire score to each neighbour, so high out-degree does not dilute its contribution. Second, directed reducible graphs may assign zero scores to parts of the network. With the lecture’s incoming-edge convention $A_{ij}=1$ for $j\to i$ and $\rho>0$, a vertex with no incoming edges has zero score, as does a vertex whose incoming neighbours all have zero score. The drawing illustrates this propagation of zeros.

This is not a claim that only zero-in-degree vertices can have zero scores. For a directed acyclic graph $\rho=0$, the displayed division by $\rho$ is unavailable.

> [!example]- Original page 5
> ![[w2-p05.jpg]]

## Page 06 - Katz centrality

Add a positive baseline:
$$x(t+1)=\alpha Ax(t)+\beta\mathbf1.$$
For $\beta>0$ and $0\le\alpha<1/\rho(A)$ (when $\rho>0$), the iteration converges to
$$x=\alpha Ax+\beta\mathbf1,\qquad x=\beta(I-\alpha A)^{-1}\mathbf1.$$
The inverse expands as $\sum_{r\ge0}\alpha^rA^r$: Katz centrality counts attenuated walks from every length. $\mathbf1$ is the **all-ones vector**, not a unit-norm vector. Multiplying $\beta$ by a constant rescales the ranking scores.

The lecture introduces a proportionality factor $\gamma$, giving $x=(\beta/\gamma)[I-(\alpha/\gamma)A]^{-1}\mathbf1$; the fixed-point formulation takes $\gamma=1$. The student TeX puts the inverse in the wrong position: it is the entire matrix $I-\alpha A$ that must be inverted.

> [!example]- Original page 6
> ![[w2-p06.jpg]]

## Page 07 - PageRank and the centrality comparison

For incoming-edge adjacency, divide the contribution of vertex $j$ by $z_j^{\mathrm{out}}$:
$$x_i(t+1)=\alpha\sum_j\frac{A_{ij}}{z_j^{\mathrm{out}}}x_j(t)+\beta.$$
This is the lecture’s unnormalised form. A probability-normalised version is
$$x=\alpha Px+(1-\alpha)v,$$
where $0\le\alpha<1$, $v$ is a probability vector, and $P$ is column-stochastic. Replace a dangling vertex’s zero-out-degree column by $v$; otherwise division by zero is undefined. The lecture gives $\alpha=0.85$ and $\beta=1$ as its example.

| Measure | Adds baseline | Divides by sender’s out-degree |
| --- | --- | --- |
| Eigenvector | No | No |
| Katz | Yes | No |
| PageRank | Yes | Yes |

The remaining no-baseline/degree-normalised construction is related to an ordinary random-walk stationary distribution; it is not developed on this page. The lecture’s Newman p. 178 reference may use different pagination; see [[Newman reading map]].

> [!example]- Original page 7
> ![[w2-p07.jpg]]

## Page 08 - Sampling a population

Let $m\in\{1,\ldots,M\}$ label observation types, let $p_m$ be their probabilities and let $u(m)$ be a real-valued measurement. A population expectation is
$$\mathbb E[u]=\sum_{m=1}^M p_mu(m).$$
For $S$ observed samples, $m(s)$ denotes the type of observation $s$. Population sizes and limiting empirical frequencies motivate probabilities on this page; the exact probability-space expectation above avoids confusing population size with sample size. The source’s coloured-ball sketch distinguishes the observed subset from the full population.

> [!example]- Original page 8
> ![[w2-p08.jpg]]

## Page 09 - Empirical frequencies and unbiasedness

Define
$$\hat p_m=\frac1S\sum_{s=1}^S\mathbf1\{m(s)=m\},\qquad \hat u=\frac1S\sum_{s=1}^Su(m(s))=\sum_m\hat p_mu(m).$$
If each observation has marginal distribution $p$, linearity of expectation gives
$$\mathbb E[\hat p_m]=p_m,\qquad \mathbb E[\hat u]=\mathbb E[u].$$
Independence is unnecessary for these unbiasedness statements, but it matters for variance formulas and convergence arguments. “Unbiased” refers to an average over repeated samples; it does not mean a particular sample equals the population value. If sampling favours some types, the same estimator targets that sampling distribution instead.

> [!example]- Original page 9
> ![[w2-p09.jpg]]

## Page 10 - Three different sampling spaces

| What is sampled | States | Measurements |
| --- | --- | --- |
| Within one network | Vertices or edges | Degree, local clustering, betweenness |
| Networks | Graphs $g\in\Omega$ | Transitivity, diameter, other graph statistics |
| Models or labels | Parameters, or $b\in\{1,\ldots,B\}^N$ | Likelihood/posterior and inferred structure |

The later weeks reuse sampling ideas on different spaces. Keep the fixed data and the random state separate: Week 4 randomises graphs, whereas Week 7 randomises block assignments for an observed graph.

> [!example]- Original page 10
> ![[w2-p10.jpg]]

## Page 11 - Friendship paradox

For a uniformly sampled vertex, $\mathbb E_V[z]=\langle z\rangle=2L/N$. If instead one samples uniformly among the $2L$ edge endpoints, vertex $i$ is selected with probability $z_i/(2L)$. Assuming $L>0$,
$$\mathbb E_{\mathrm{end}}[z]=\sum_i\frac{z_i}{2L}z_i=\frac{\langle z^2\rangle}{\langle z\rangle}=\langle z\rangle+\frac{\operatorname{Var}_V(z)}{\langle z\rangle}\ge\langle z\rangle.$$
Equality holds iff all vertex degrees are equal. This is an average statement; it is not true that every person has fewer friends than each of their friends.

**Sampling caveat:** choosing a uniform vertex and then one of its neighbours uniformly generally gives a different distribution. Tutorial 1 uses that two-stage procedure. See [[Sampling and friendship paradox]] for the distinction and its exact formula.

> [!example]- Original page 11
> ![[w2-p11.jpg]]

## Page 12 - How networks are observed

- **Vertex sampling:** select vertices and record relevant edges; clarify whether only edges between sampled vertices are retained.
- **Edge sampling:** select edges and then observe their endpoints.
- **Random-walk sampling:** begin at a vertex and repeatedly choose a neighbour.
- **Snowball sampling:** begin at a seed, add all neighbours, and repeat outwards.

The lecture’s $\langle z\rangle^t$ growth sketch for snowball sampling is a branching heuristic. Backtracking, repeated discoveries and finite size reduce growth; heterogeneous degrees change the branching factor. The page illustrates random-walk and snowball exploration on the Karate Club graph.

> [!example]- Original page 12
> ![[w2-p12.jpg]]

## Page 13 - Sampling bias and practical implications

An induced subgraph formed by sampling a small number of vertices from a large sparse graph can be nearly empty and fragmented. For independent vertex retention with probability $s$, each original edge survives with probability $s^2$, so $\mathbb E[L_{\mathrm{retained}}]=s^2L$ (added derivation of the page’s warning).

Observed network statistics need not equal full-network statistics. A bias may nevertheless be useful when deliberately selecting highly connected people for early-warning or intervention strategies; the lecture lists these as applications, without establishing their effectiveness for a particular setting.

> [!example]- Original page 13
> ![[w2-p13.jpg]]

