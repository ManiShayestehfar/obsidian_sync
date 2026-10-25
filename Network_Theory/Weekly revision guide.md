---
tags: [revision]
---

# Weekly revision guide

Use this guide to revise in the course’s teaching order while keeping the notes organised by topic. Read each week’s main chapters first, then reconstruct the key argument and interpret one tutorial example. A chapter can span several weeks: study only the indicated sections when making a first pass.

| Week | Main content | Main chapters |
| --- | --- | --- |
| 1 | Graph representations, paths, components, degree and clustering | [[Graphs and representations]] · [[Paths and components]] · [[Clustering]] |
| 2 | Centrality and sampling | [[Centrality]] · [[Sampling and friendship paradox]] |
| 3 | Random ensembles, ER, sparse limits and giant components | [[Random graph ensembles]] · [[Erdos-Renyi graphs]] |
| 4 | Graph-space MCMC and degree-constrained models | [[Monte Carlo sampling]] · [[Configuration model]] |
| 5 | Small worlds, broad degrees and network growth | [[Small-world networks]] · [[Power laws]] · [[Preferential attachment]] |
| 6 | Metropolis–Hastings, maximum entropy and ERGMs | [[Monte Carlo sampling]] · [[Maximum entropy and ERGMs]] |
| 7 | SBM likelihood, allocation search and model selection | [[Stochastic block models]] · [[Statistical inference and model selection]] |
| 8 | Community algorithms and spectral clustering | [[Community detection]] · [[Spectral graph theory]] |
| 9 | Missing-link prediction and inference from states | [[Network reconstruction]] · [[Reconstruction from node activity]] · [[Spectral graph theory]] |
| 10 | Percolation, random failures and attacks | [[Percolation and robustness]] |
| 11 | Update rules, majority dynamics, cascades, SI and SIS | [[Binary dynamics and cascades]] · [[Threshold cascades]] · [[Epidemic models]] |
| 12 | Awaiting lecturer’s notes and tutorial | See the scope note at the end |

## Week 1 — describe the graph before measuring it

Read **Graphs and representations**, then **Paths and components**, then **Clustering**. Understand simple/directed/weighted/bipartite representations, handshaking, walks versus paths, adjacency powers, distance conventions and triangle closure. Author–paper projections illustrate why representation changes information and can create triangles.

- [ ] Derive $\sum_i k_i=2L$, the walk-count identity and the triangle/transitivity formulas.
- [ ] Compute the two clustering averages on the hub-with-two-triangles example.
- [ ] Explain how disconnectedness, missing isolates and duplicate edge-list entries affect a calculation.

**Tutorial focus:** build/load a graph and interpret measurements. The sampling examples introduce ideas developed more fully in Week 2.

## Week 2 — choose what “important” and “random” mean

Read **Centrality** and **Sampling and friendship paradox**. Study degree, distance and betweenness first, then eigenvector, Katz and PageRank. Follow the distinction between a uniform vertex, a uniform edge endpoint and a random neighbour chosen in two stages.

- [ ] Derive the Katz series and explain its spectral bound; identify why a bipartite graph can defeat plain power iteration.
- [ ] Derive $\mathbb E_{\rm endpoint}[K]=\langle k^2\rangle/\langle k\rangle$ from the sampling law.
- [ ] Explain why an unbiased average need not have independent observations or equal the population value in one sample.

**Tutorial focus:** centrality comparisons and lattice/random-regular contrasts. Use the lattice sections in **Paths and components** and **Clustering** as needed.

## Week 3 — build a null model and take the right limit

Read **Random graph ensembles**, then **Erdos-Renyi graphs**. Focus on labelled graph spaces, fixed versus expected edge count, binomial laws, dense versus sparse scaling, and the branching equation for the giant component.

- [ ] Explain why conditioning ER on $L$ gives uniform $G(N,L)$.
- [ ] Derive the Poisson degree limit and $S=1-e^{-cS}$, including physical root selection.
- [ ] Distinguish ensemble spread from uncertainty in the estimated ensemble mean.

**Tutorial focus:** compare an empirical network with repeated ER draws; vary $N$ at fixed density versus fixed mean degree; interpret finite largest-component fractions. A giant component is not whole-graph connectivity.

## Week 4 — sample a constrained graph space

Read the convergence, proposals and uncertainty sections of **Monte Carlo sampling**, then **Configuration model**. Compare the nested spaces with fixed $N$, fixed $N,L$ and fixed labelled degrees.

- [ ] Prove detailed balance implies stationarity and explain the additional convergence conditions.
- [ ] State which invariants each move preserves and why rejected states must be retained.
- [ ] Explain why simplifying a stub pairing changes degrees, and derive expected multiplicity and excess degree.

**Tutorial focus:** Les Misérables null ensembles, burn-in and correlation. A constant degree statistic cannot diagnose mixing on a fixed-degree space. Count update attempts consistently rather than confusing stored rows with elapsed steps.

## Week 5 — explain shortcuts and heterogeneous degrees

Read **Small-world networks**, **Power laws**, then **Preferential attachment**. Keep the two small-world questions separate: whether short routes exist and whether a local algorithm can find them.

- [ ] Derive ring clustering and explain the $C(0)(1-p)^3$ approximation.
- [ ] Use a tail sum/integral to decide which moments converge; use a survival probability for the natural maximum scale.
- [ ] Obtain the BA continuum growth law and exponent-three tail, identifying the approximations.

**Tutorial focus:** rewiring sweeps, degree-preserving lattice swaps, BA versus matched ER, and political-blog degree comparisons. A log–log line alone is not a power-law fit.

## Week 6 — weight graphs to match expected statistics

Revisit the MH ratio in **Monte Carlo sampling**, then read **Maximum entropy and ERGMs**. Separate the proposal from the target and hard constraints from constraints on expectations.

- [ ] Derive the exponential-family distribution using entropy maximisation.
- [ ] Show that derivatives of $\log Z$ give moments/covariances and explain moment fitting.
- [ ] Explain why $Z$ cancels for fixed-parameter graph moves but not for comparing parameters.

**Tutorial focus:** wrapped interval sampling, graph weights $1,C,C^{10}$, and the clustering-conditioned November 17 example. Fit expected clustering, then compare a different statistic such as maximum betweenness. High acceptance or a flat trace alone does not certify mixing.

## Week 7 — infer a block structure without confusing objectives

Read **Stochastic block models**, then **Statistical inference and model selection**. Concentrate on the Bernoulli likelihood, non-edges, fitted block densities, single-vertex search, local barriers, annealing and partition counts.

- [ ] Derive $\widehat p_{rs}=l_{rs}/y_{rs}$ with boundary and zero-dyad cases.
- [ ] Write the allocation MH acceptance with the correct sign and compare it with greedy optimisation.
- [ ] Explain $S(N,B)$ versus $B!S(N,B)$, raw-likelihood overfitting and the best-partition proxy versus full evidence.

**Tutorial focus:** Karate partitions and planted SBMs; compare labels up to permutation. The variational section supplies context from Jenny’s notes rather than an additional long derivation to memorise.

## Week 8 — compare community objectives and spectral relaxations

Read **Community detection**, then the energy identity, eigengap and clustering sections of **Spectral graph theory**. The link-prediction use of the embedding belongs to Week 9.

- [ ] State what Kernighan–Lin fixes and what it minimises; outline its pass/locking procedure.
- [ ] Derive blockwise modularity and a merge gain; explain the greedy $Q(B)$ path.
- [ ] Prove Laplacian positivity and that the number of zero modes equals the number of components; explain clustering the rows of $U$.

**Tutorial focus:** Karate bisection/greedy/Louvain comparisons (Ex.2.1–2.2); communities returned on ER and the five-block contrast sweep (Ex.3.1–3.2); eigengaps and spectral clustering (Ex.4.1–4.2). Distinguish recovering an optimum under an objective from demonstrating meaningful planted structure.

## Week 9 — predict edges and reconstruct interactions

Read **Network reconstruction**, then the link-scoring section of **Spectral graph theory**, then **Reconstruction from node activity**. Use **Stochastic block models** for block scores and **Monte Carlo sampling** for the graph proposal.

- [ ] State the deletion/negative-sampling protocol and explain leakage prevention and AUC ties, especially $B=1$.
- [ ] Explain $-\|v_i-v_j\|^2$, dimension selection and the notebook’s disconnected-graph nullspace convention.
- [ ] Derive the Ising node-conditional, negative log pseudolikelihood and fixed-$L$ MH target; obtain expected random overlap $L^2/\binom N2$.

**Tutorial focus:** compare heuristic, SBM and spectral scores on matched splits (Ex.1.1–1.4); vary observation count for Pearson and coupling for pseudolikelihood reconstruction (Ex.2.1–2.2). Best predictive dimension or $B$ need not recover the generating model. Distinguish supplied $L,J$ from unknown structure.

## Week 10 — thin the network and track its surviving function

Read **Percolation and robustness**. Revisit excess degree in **Configuration model** and the finite-tail qualifications in **Power laws** if needed.

- [ ] Distinguish site/bond retention, failure probability, a crossing, rooted survival and existence of an infinite component.
- [ ] Derive $p\kappa=1$, thinning moments and the two-point degree-law threshold.
- [ ] Explain finite-size rounding, original-size normalisation, nested failure sets, diameter peaks, and static versus adaptive attacks.

**Tutorial focus:** four/eight-neighbour lattice percolation and regular trees (Ex.1.1–1.3); ER/BA and prescribed degrees (Ex.2.1–2.2); static degree attacks (Ex.3.1). Treat random-failure and attack conclusions as model-dependent; do not apply one threshold formula indiscriminately.

## Week 11 — specify the dynamics before interpreting its limit

Read **Binary dynamics and cascades**, **Threshold cascades**, and the discrete SI/SIS and mean-field-revision sections of **Epidemic models**. Its later SIR/continuous-rate material is supplementary, pending the next upload.

- [ ] Distinguish synchronous, permutation and with-replacement updates; explain consensus, mixed fixed points and a period-two example.
- [ ] State irreversible **strict** threshold activation, vulnerability and the original-degree versus induced-degree distinction.
- [ ] Derive $1-(1-\lambda)^m$, the approximate SI time scale and SIS balance $\lambda\langle k\rangle\approx\mu$; explain finite extinction.

**Tutorial focus:** majority attractors (Ex.1.1), threshold/vulnerable-component comparisons (Ex.2.1–2.2), SI curve collapse and SIS finite-window behaviour (Ex.3.1–3.2). Do not confuse an unchanged infected count with an absorbing configuration, or a finite plateau with survival forever.

## Week 12 — pending

No 2026 Week 12 lecture or tutorial has been supplied yet. **Evolutionary games**, **Synchronisation and stability**, and the supplementary SIR/continuous-rate sections retain earlier student-based material. Their placement and final scope will be checked against the next upload; they are not currently a confirmed Week 12 study list.

> [!reference]- Basis of the weekly mapping
> Weeks 1–7 follow the lecture/tutorial synthesis already present in the supplied vault. Weeks 8–11 follow the titles, sections and exercises of the newly supplied 2026 PDFs and notebooks. The guide maps teaching coverage, not assessment weights or a predicted examination paper. For topic-level sources, see each chapter’s source callout.
