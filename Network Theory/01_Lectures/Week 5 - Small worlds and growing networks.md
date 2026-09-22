---
type: lecture-export
week: 5
source_pages: 12
status: visually-checked-paraphrase
tags: [DATA5441, lecture]
---

# Week 5 - Small worlds and growing networks

[[00_HOME]] · [[Tutorial 5 - guide]] · [[Newman reading map]] · [[Corrections and caveats]]

Source: `Notes Week 5 2026.pdf`; page numbers below refer to this supplied PDF.

Page-by-page mathematical transcription and paraphrase of the supplied handwritten lecture. Equations have been typeset; diagrams and the complete original page are retained in each image. Added explanations, corrections and ambiguities are identified in the text. This is not a verbatim diplomatic transcription.

## Page 01 - Why another model?

The comparison of real networks, ER graphs and lattices motivates a model combining short distances and substantial clustering. ER explains short distances but, in its sparse limit, clustering vanishes. A fixed-dimensional lattice retains local structure but has much longer distances. Neither generally explains the broad degree variation of empirical networks. The plotted survey of 18 networks is retained below; individual plotted observations are not presented as freshly computed results.

> [!example]- Original page 1
> ![[w5-p01.jpg]]

## Page 02 - Small-world observations

The lecture discusses Milgram’s acquaintance-chain experiment (1967), the email experiment of Dodds, Muhamad and Watts (2003), and a Facebook report (2016). The handwritten distance summaries are approximately 5.9, a median of 7, and 4.5 with an adjacent “+1” annotation. These studies use different populations, sampling and counting conventions; they are illustrations, not directly comparable estimates of one population quantity.

The course seeks graphs with bounded mean degree as $N$ grows, short characteristic distances (typically logarithmic in $N$), and clustering that remains appreciable. “Small world” in the narrower textbook usage describes short distances; high clustering is the additional feature that motivates Watts–Strogatz.

> [!example]- Original page 2
> ![[w5-p02.jpg]]

## Page 03 - Watts–Strogatz construction

Place $N$ vertices on a ring and join each vertex to its $Q$ nearest neighbours in each direction. Initially $z_i=2Q$, $L=NQ$. Randomly rewire edges with probability $p$, preserving simplicity. The page describes variants that rewire one endpoint or both endpoints; specify the variant in any experiment. Rewiring generally preserves $L$, not every degree.

**Added exact baseline:** when $N>3Q$ (so there are no extra wrap-around triangles), the local clustering is
$$C(0)=\frac{3(Q-1)}{2(2Q-1)}.$$
It is zero for $Q=1$ and approaches $3/4$ as $Q$ grows. See [[Small worlds and preferential attachment]].

> [!example]- Original page 3
> ![[w5-p03.jpg]]

## Page 04 - Clustering and distance as rewiring begins

A triangle in the original lattice survives if its three edges survive rewiring. This motivates
$$C(p)\approx C(0)(1-p)^3.$$
This is an approximation: rewiring can create new triangles and change local degree denominators. At $p=0$, the ring distance is proportional to $N/Q$; its diameter is $\lceil\lfloor N/2\rfloor/Q\rceil$. A long-range edge can shorten many routes without destroying most local triangles.

> [!example]- Original page 4
> ![[w5-p04.jpg]]

## Page 05 - The small-world regime

There are $NQ$ original edges, so the expected number selected for rewiring is $pNQ$. The lecture sketches a rapid drop in characteristic distance while clustering stays close to its lattice value. A useful crossover intuition is
$$pNQ\gg1,\qquad p\ll1.$$

**Qualification:** these inequalities describe a broad finite-size regime. They do not, by themselves, prove logarithmic distance for every sequence $p=p(N)$. State which quantities remain fixed in an asymptotic claim. For fixed positive rewiring probability and fixed degree parameter, shortcuts can give short distances while appreciable local clustering remains.

> [!example]- Original page 5
> ![[w5-p05.jpg]]

## Page 06 - Embedded reading - Kleinberg on navigation

This page reproduces Kleinberg’s *Navigation in a small world* (Nature, 2000). The full supplied page is preserved in the image. This paragraph is a content summary, not a verbatim transcription of the embedded article.

Having a short path does not mean a person using only local information can find it. Kleinberg considers a lattice with local contacts and long-range contacts whose probability decreases as a power of lattice distance. In a $d$-dimensional lattice, the navigable case weights a destination at distance $r$ proportionally to $r^{-d}$, with normalisation over destinations. In the two-dimensional model, the matching exponent permits expected greedy delivery time of order $(\log n)^2$, where $n$ is the lattice side length. Other exponents incur polynomial lower bounds in that model. Local links, number of shortcuts and the information available to the routing rule are part of the assumptions. Do not confuse this distance exponent with the degree exponent below.

> [!example]- Original page 6
> ![[w5-p06.jpg]]

## Page 07 - Power-law degrees and moments

A degree distribution has a power-law tail if $p_k\sim Ak^{-\gamma}$ as $k\to\infty$. The moment comparison is
$$\mathbb E[Z^r]\sim A\sum_k k^{r-\gamma}.$$
It converges at the upper end precisely when $\gamma>r+1$. Thus the mean is finite for $\gamma>2$, and the second moment is finite for $\gamma>3$. At equality the divergence is logarithmic. For $2<\gamma\le3$, an ideal infinite-tail distribution has finite mean and infinite variance.

Every finite graph has bounded degrees and finite empirical moments. “Divergent variance” concerns a limit of distributions or graph sequences. See [[Power laws and finite-size cutoffs]].

> [!example]- Original page 7
> ![[w5-p07.jpg]]

## Page 08 - Finite-size cutoff - correction to the source

The handwritten argument sets $p(z_{\max})\sim1/N$, obtaining $z_{\max}\sim N^{1/\gamma}$ and a second-moment estimate proportional to $N^{(3-\gamma)/\gamma}$. This uses a probability mass at a single value where an exceedance probability is required.

**Corrected natural-cutoff heuristic:** for approximately independent samples with a power-law tail,
$$\Pr(Z\ge k)\asymp k^{1-\gamma},\qquad N\Pr(Z\ge k_{\max})\asymp1,$$
so
$$k_{\max}\asymp N^{1/(\gamma-1)}.$$
For $2<\gamma<3$, truncating at this cutoff gives $\mathbb E[Z^2]\asymp N^{(3-\gamma)/(\gamma-1)}$; for $\gamma=3$ it grows logarithmically. These are sampling heuristics, not universal laws for dependent graph degrees. Simplicity constraints and model-specific structural cutoffs can change the result.

> [!example]- Original page 8
> ![[w5-p08.jpg]]

## Page 09 - Interpreting broad degree distributions

The page distinguishes claims of increasing strength: some higher moment grows with size; relative degree variation grows; or the tail follows a specified power law. These are different statements. A heavy or broad tail need not be a pure power law, and an approximately straight portion of a log–log plot is insufficient evidence.

When comparing models, ask which feature is actually measured: tail exponent, finite-size variability, maximum degree or a moment. A plausible generative story does not establish a fitted distribution. Newman Chapter 10 supplies the statistical context.

> [!example]- Original page 9
> ![[w5-p09.jpg]]

## Page 10 - Barabási–Albert growth rule

Start with a seed graph. At each time step add one vertex and connect it to $m$ old vertices, with probability proportional to their current degrees. Specify how repeated selections and seed vertices are handled. With one new vertex per step,
$$N(t)=N_0+t,\qquad L(t)=L_0+mt,\qquad \sum_i z_i(t)=2L(t).$$
A connected seed remains connected when each new vertex has at least one link. In a continuum approximation, the expected growth of a vertex born at time $t_i$ is
$$\frac{dz_i}{dt}\approx\frac{mz_i}{2mt}=\frac{z_i}{2t},\qquad z_i(t_i)=m.$$
Seed corrections are negligible only for sufficiently large $t$.

> [!example]- Original page 10
> ![[w5-p10.jpg]]

## Page 11 - Deriving the degree exponent

Solving the continuum equation gives $z_i(t)\approx m\sqrt{t/t_i}$. Since arrival times of non-seed vertices are approximately uniform on $(0,t)$,
$$\Pr(Z\ge k)\approx\Pr\!\left(t_i\le\frac{m^2t}{k^2}\right)\approx\frac{m^2}{k^2}.$$
Consequently the continuous density approximation is
$$p(k)=-\frac{d}{dk}\Pr(Z\ge k)\approx 2m^2k^{-3}.$$
The minus sign is necessary when differentiating the survival function. This gives exponent $\gamma=3$. Individual degrees are random; the continuum trajectory is not an exact vertex-by-vertex law. The exact discrete limiting distribution has the same exponent but differs at small degrees.

> [!example]- Original page 11
> ![[w5-p11.jpg]]

## Page 12 - Strengths and limitations of preferential attachment

Growth with degree-based attachment explains a broad degree tail and an advantage, in expectation, for older vertices. With a connected seed the network remains connected. The basic model has exponent three, so it does not freely fit arbitrary empirical exponents. It also does not generally retain nonzero clustering as $N\to\infty$.

The lecture sketches clustering decay as a negative power of size. Treat this as a qualitative sketch, not a universal exact exponent. In particular, $m=1$ with a tree seed gives a tree and clustering exactly zero. Extensions include ageing, modified attachment rules and triadic closure. Distinguish a modification’s mechanism from a claim that it fits a particular dataset.

> [!example]- Original page 12
> ![[w5-p12.jpg]]

