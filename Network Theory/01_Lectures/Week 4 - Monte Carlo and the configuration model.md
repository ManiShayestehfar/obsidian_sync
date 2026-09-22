---
type: lecture-export
week: 4
source_pages: 17
status: visually-checked-paraphrase
tags: [DATA5441, lecture]
---

# Week 4 - Monte Carlo and the configuration model

[[00_HOME]] · [[Tutorial 4 - guide]] · [[Newman reading map]] · [[Corrections and caveats]]

Source: `Notes Week 4 - 2026.pdf`; page numbers below refer to this supplied PDF.

Page-by-page mathematical transcription and paraphrase of the supplied handwritten lecture. Equations have been typeset; diagrams and the complete original page are retained in each image. Added explanations, corrections and ambiguities are identified in the text. This is not a verbatim diplomatic transcription.

## Page 01 - Recap and empirical comparison

A random graph is $(\Omega,p)$ with nonnegative, normalised probabilities. The page compares empirical networks with an ER baseline matched in $N$ and expected $L$.

| Network | Relative degree variability | Distance | Clustering |
| --- | --- | --- | --- |
| US power grid | In range | Larger | Larger |
| Karate Club | Larger | Blank in source | Larger |
| Les Misérables | In range | Slightly larger | Larger |
| Facebook | Larger | Slightly smaller | Larger |
| David Copperfield | Larger | In range | Larger |
| Star Wars | Larger | Larger | Larger |
| Davis Southern Women | Larger | Larger | Smaller |

These are the lecture’s reported comparisons, not newly computed findings. The power-grid row gives $N=4941$, $L=6594$, relative variability about $0.67$, distance about $18.9$ and clustering $0.1032$. Other legible row sizes include Les Misérables $77,252$, David Copperfield $112,425$, Star Wars $111,444$, and Davis Southern Women $32,89$. The Facebook edge-count handwriting is ambiguous and is preserved in the image without an invented number.

> [!example]- Original page 1
> ![[w4-p01.jpg]]

## Page 02 - Monte Carlo on graph space

Goal: sample $g\in\Omega$ with probability $p(g)$. Start at $g_0$, propose/apply a random transformation, measure the current graph and repeat.

Let $W(g\to h)$ denote the complete transition probability, including remaining at $g$. It satisfies $\sum_hW(g\to h)=1$. If $w_g(t)=\Pr(G_t=g)$, then
$$w_h(t+1)=\sum_g w_g(t)W(g\to h).$$
The stochasticity of $W$ is different from the target $p$. A drawing shows a trajectory through graph space. See [[MCMC and detailed balance]].

> [!example]- Original page 2
> ![[w4-p02.jpg]]

## Page 03 - Conditions and detailed balance

For a finite state space, useful sufficient conditions for convergence from every initial state are:

1. Transitions remain in $\Omega$.
2. The chain is irreducible: every state can reach every other.
3. It is aperiodic.
4. The desired $p$ is stationary; one convenient way to ensure this is detailed balance,
$$p(g)W(g\to h)=p(h)W(h\to g).$$

The lecture lists closure, “ergodicity” and detailed balance, but describes ergodicity only as reachability. Aperiodicity must also be checked for convergence of the distribution. Detailed balance is sufficient, not necessary, for stationarity. This correction matters for the pure edge-flip chain below.

> [!example]- Original page 3
> ![[w4-p03.jpg]]

## Page 04 - Why detailed balance gives stationarity

Sum detailed balance over $g$:
$$\sum_gp(g)W(g\to h)=p(h)\sum_gW(h\to g)=p(h).$$
Therefore $p$ is stationary. If $P_{gh}=W(g\to h)$ and probabilities are row vectors, $pP=p$; with column vectors use $P^\top p=p$. The lecture switches between these matrix conventions; the componentwise equation is unambiguous.

A finite irreducible chain has a unique stationary distribution. Aperiodicity then yields convergence to it. Eigenvalue one expresses stationarity; it alone does not rule out oscillations caused by another eigenvalue on the unit circle.

> [!example]- Original page 4
> ![[w4-p04.jpg]]

## Page 05 - Case 1 - fixed N

Let $Y=\binom N2$ and let $\Omega_1$ contain every simple graph on the fixed labelled vertex set. The uniform target is $p(g)=2^{-Y}$.

The lecture proposes choosing a dyad uniformly and flipping its edge indicator. If $g,h$ differ in exactly one dyad, $W(g\to h)=1/Y$; otherwise the off-diagonal transition is zero. This is symmetric and irreducible.

> [!important] Period-two chain
> Pure flipping changes edge-count parity at every step, so the chain is periodic. The source’s alternative—set the chosen indicator to a fresh Bernoulli$(1/2)$ value—adds self-transitions and fixes this. Tutorial 4 uses this dyad-resampling version.

A difference of one in total edge count alone is not sufficient for a one-step transition: the graphs must differ in exactly one possible edge.

> [!example]- Original page 5
> ![[w4-p05.jpg]]

## Page 06 - Why naive filtering fails

One could sample $\Omega_1$ and retain only graphs with $L=L^*$. However, $L\sim\mathrm{Binomial}(Y,1/2)$ concentrates near $Y/2$. If the target empirical graph is sparse, $L^*\ll Y/2$, that event is extremely rare. A valid rejection method can therefore be computationally useless.

This motivates designing moves directly within the constrained sample space, instead of repeatedly generating graphs that violate the desired constraint.

> [!example]- Original page 6
> ![[w4-p06.jpg]]

## Page 07 - Case 2 - fixed N and L

Let $\Omega_2=\{g:L(g)=L^*\}\subset\Omega_1$. Choose an existing edge and a non-edge uniformly, remove the former and add the latter. This preserves $N,L$ and is symmetric on the uniform fixed-$L$ ensemble.

For the lecture’s “choose before removal” version, an allowed replacement has probability $1/[L(Y-L)]$. The notebook instead removes first and samples among the resulting $Y-L+1$ non-edges, permitting the removed edge to be re-added. Its probability is $1/[L(Y-L+1)]$ and it has a self-transition. These are distinct valid kernels; specify which counts one time step. Empty and complete graphs are trivial one-state ensembles.

> [!example]- Original page 7
> ![[w4-p07.jpg]]

## Page 08 - Equilibration, correlation and interpretation

The plotted transitivity starts near the observed graph’s value and decays towards an ensemble baseline. Discard the initial transient before estimating stationary statistics. Successive graphs remain correlated; a longer recording lag may reduce correlation, but does not prove independence.

The lecture suggests characteristic times of order $Y$ for Case 1 and order $L$ for Case 2, and infers that the focus network has unusually high clustering and degree variability relative to the baseline. Treat these times as heuristics for the illustrated observables, not general mixing-time bounds.

Use sample-to-sample standard deviation for graph variability and a correlation-adjusted standard error for uncertainty in the estimated mean. They answer different questions.

> [!example]- Original page 8
> ![[w4-p08.jpg]]

## Page 09 - Empirical comparison revisited

The page repeats the table from p. 1, now alongside a published network-statistics table. The repeated lesson is that a simple ER baseline often reproduces short distances more successfully than high clustering or broad degree variation.

All repeated rows are transcribed on [[Week 4 - Monte Carlo and the configuration model#Page 01 - Recap and empirical comparison]]. The small reference table and its dataset-specific numbers remain available in the page image. They are illustrative source material, not a set of uniform measurements recomputed under common conventions.

> [!example]- Original page 9
> ![[w4-p09.jpg]]

## Page 10 - Model comparison with a degree constraint

The comparison table repeats the Week 3 families and adds the configuration model, whose degree sequence is fixed. Degree variability is then imposed, rather than predicted from $N,L$ alone.

This suggests a nested null-model question: does unexpectedly high clustering under an ER baseline remain unexpected after controlling for every vertex’s degree? See [[Random graph ensembles]] and [[Configuration model and excess degree]]. The source leaves several cells blank; they should not be interpreted as zero.

> [!example]- Original page 10
> ![[w4-p10.jpg]]

## Page 11 - What the simple models miss

The lecture summarises three empirical features: degree variability often exceeds ER; distances remain relatively short; clustering often exceeds ER.

The proposed next steps separate two questions:

- **Constraints:** can a random-graph ensemble incorporate degree heterogeneity and clustering? Configuration models and later ERGMs address this.
- **Mechanisms:** what processes could create these features? Small-world rewiring and preferential attachment address this in Week 5.

A mechanism and a fitted null model serve different inferential purposes, even if both generate similar statistics.

> [!example]- Original page 11
> ![[w4-p11.jpg]]

## Page 12 - Configuration model construction

Choose nonnegative integer degrees $(z_1,\ldots,z_N)$ with even sum $2L$. Attach $z_i$ labelled stubs to each vertex and pair all stubs uniformly at random. The resulting multigraph has the prescribed degrees, counting a self-loop twice. Parallel edges and self-loops are allowed.

For distinct $i,j$, each of $i$’s stubs meets one of $j$’s stubs with probability $z_j/(2L-1)$, so
$$\mathbb E[M_{ij}]=\frac{z_iz_j}{2L-1}\approx\frac{z_iz_j}{2L}.$$
This is the expected edge multiplicity, only approximately an edge-existence probability when multiple edges are rare. The lecture writes it as a probability. Given two edges from a focal vertex to neighbours $j,k$, their remaining-stub connection factor is approximately $(z_j-1)(z_k-1)/(2L)$.

> [!example]- Original page 12
> ![[w4-p12.jpg]]

## Page 13 - Configuration-model limits and qualifications

The page gives vanishing clustering and logarithmic-distance heuristics for sparse, locally tree-like graphs. With suitable bounded-moment assumptions,
$$C\approx\frac{(\langle z^2\rangle-\langle z\rangle)^2}{N\langle z\rangle^3},\qquad \kappa=\frac{\langle z^2\rangle-\langle z\rangle}{\langle z\rangle}.$$
The distance branching factor is $\kappa$, rather than generally $\langle z\rangle$. Heavy tails can invalidate these simple approximations.

Not every degree sequence is graphical as a simple graph; the lecture cites the Erdős–Gallai criterion. Pairing stubs only needs an even sum for a multigraph.

**Correction:** the claim “almost all configuration graphs are not simple as $N\to\infty$” is not universal. For all degrees equal to one, every pairing is simple. Under bounded second moments, the expected number of defects can stay bounded while their fraction vanishes; that does not imply their presence has probability tending to one. Deleting defects alters the prescribed degrees.

> [!example]- Original page 13
> ![[w4-p13.jpg]]

## Page 14 - Case 3 - fixed vertex-specific degrees

Let
$$\Omega_3=\{g\text{ simple on }V:z_i(g)=z_i^*\ \forall i\}\subseteq\Omega_2\subseteq\Omega_1.$$
The illustrated example has $N=6$, $L=7$ and degree sequence $(2,3,2,2,3,2)$. Reconnecting edges can change triangles and distances while retaining every vertex’s degree. Unlike unconstrained stub pairing, the state space contains only simple graphs.

> [!example]- Original page 14
> ![[w4-p14.jpg]]

## Page 15 - Degree-preserving switches

Given edges $\{i,j\}$ and $\{r,s\}$, a switch replaces them by $\{i,r\}$ and $\{j,s\}$ (or the other cross-pairing), provided it creates neither loops nor parallel edges. Every involved vertex loses and gains one edge.

For an exact symmetric proposal, choose an edge pair and one cross-pairing with state-independent rules; if invalid, stay at the current graph and count that attempt. Add explicit laziness if needed. The uniform simple fixed-degree target then satisfies detailed balance.

The source says “choose an acceptable swap” and assumes symmetry. Conditioning proposals on successful swaps can introduce a graph-dependent factor. NetworkX’s successful-swap count is not automatically a count of this single-attempt kernel. See [[MCMC and detailed balance]] and Tutorial 6’s supplied correction. Degree preservation does not imply connectivity preservation.

> [!example]- Original page 15
> ![[w4-p15.jpg]]

## Page 16 - Estimating ensemble expectations

After burn-in, record states at chosen times $t_1,\ldots,t_S$ and estimate
$$\widehat{\mathbb E_p[x]}=\frac1S\sum_{a=1}^Sx(G_{t_a}).$$
Repeated states must be counted with their multiplicities; the sample is a sequence, not a set of distinct graphs. The page sketches burn-in and a larger recording interval, and suggests a timescale of order $L$ for switches.

Assess actual traces and autocorrelation. A flat-looking trace from one initial state does not establish exploration of all relevant regions of graph space. See [[Simulation and uncertainty]].

> [!example]- Original page 16
> ![[w4-p16.jpg]]

## Page 17 - Blank source page

This final page contains only the background grid. No lecture text, formula or diagram is present.

> [!example]- Original page 17
> ![[w4-p17.jpg]]

