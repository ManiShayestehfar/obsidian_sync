---
type: study-note
tags: [DATA5441]
---

# Tutorial 3 - guide

[[00_HOME]]

[[Tutorial 3 - source export]]


Read [[Random graph ensembles]] and [[Giant components and finite graphs]].

| Exercise / source cells | Workflow | What a sound conclusion needs |
| --- | --- | --- |
| 2.1, 10 | Choose and describe an empirical network | Graph type, $N,L$, statistic definitions, component treatment |
| 2.2, 12 onwards | Fit ER density and generate repeated samples | $q=2L/[N(N-1)]$; simulated $L$ fluctuates |
| 3.1, 35 onwards | Increase $N$ at fixed $q=0.1$ | This is dense, with mean degree $0.1(N-1)$ |
| 3.2, 42 onwards | Increase $N$ at mean degree about three | This is sparse; Poisson is a limiting approximation |
| 4.1, 56 onwards | Estimate giant-component fraction against mean degree | Multiple realisations and finite-size effects near $c=1$ |

At fixed $q$, $\operatorname{Var}(K)=(N-1)q(1-q)$ and relative degree variability is $\sqrt{(1-q)/[(N-1)q]}$. At fixed $c$ with $q=c/(N-1)$ it approaches $1/\sqrt c$. These are population/model formulas; empirical degree statistics from one graph fluctuate.

For vertices with degree at least two, ER’s conditional expected local clustering is $q$. If zero is assigned to lower-degree vertices, $\mathbb E[\bar C]=q\Pr(K\ge2)$, not exactly $q$. Expected transitivity is a different ratio question.

Build a results table containing the empirical value, ensemble mean, ensemble standard deviation, number of realisations and component convention. A two-standard-deviation rule is descriptive unless its sampling distribution and fitting procedure justify a test. Report whether each metric was used to fit the model or is an independent check.

For sparse $c=3$, solve $S=1-e^{-3S}$ for the positive solution, approximately $0.9405$. This predicts a giant component, not guaranteed connectedness. Empty or one-vertex components require explicit path-length handling.


The cell references above use one-based notebook order, matching the source-export headings. These guides provide derivations and checks; the full long-running notebooks were not re-executed when preparing this vault.
