---
type: study-note
tags: [DATA5441]
---

# Tutorial 7 - guide

[[00_HOME]]

[[Tutorial 7 - source export]]


Read [[SBM inference and model selection]] and the Week 7 lecture export.

| Exercise / source cells | Task | Checkpoint |
| --- | --- | --- |
| 1, 21–25 | Rank fixed Karate partitions; fit block probabilities and clustering | Known split has better likelihood than the supplied random allocation, then the one-group allocation |
| 2, 26–33 | Count partitions, time evaluation, find a good split | $S(34,2)=8{,}589{,}934{,}591$ unlabelled nonempty partitions |
| 3, 34–38 | Best single-switch greedy search from several starts | Final values may differ; a local optimum is not a global certificate |
| 4, 39–42 | Verify a local minimum and a barrier | Evaluate all single-switch $\Delta F$; account for label permutations |
| 5, 43–45 | Metropolis sampling | Uphill acceptance is $e^{-\Delta F}$, not $e^{+\Delta F}$ |
| 6, 46–56 | Generalise to $B$ groups; compare fitted scores | $B=N$ fits perfectly, illustrating overfitting; the penalised plot is a proxy |
| 7, 57–70 | Infer a planted two-group SBM | Sizes 20 and 50, probabilities $0.15,0.20,0.01$, requested seed 13 |

**Corrections that affect execution or interpretation:**

1. Cell 22 computes the ratio of expected closed wedges to expected wedges. This is a useful approximation to ensemble transitivity, but in general $\mathbb E[X/Y]\ne\mathbb E[X]/\mathbb E[Y]$. Estimate the actual expected transitivity by averaging transitivity across simulated graphs if that is the requested quantity.
2. The early `computeMinusLogL` in cell 9 expects a Python list because it uses `.count`. Cell 44 converts partitions to NumPy arrays and passes them into that function. Define the general array-compatible version from cell 47 **before** running the MCMC, or adapt the early function consistently. A clean sequential run otherwise fails here.
3. The one-block allocation used initially is a one-group model, not an allocation with exactly two nonempty groups. The greedy code may permit an empty group, whereas later MCMC rejects moves that would empty one. State the support being compared.
4. Cell 37 takes the first strictly best move found; it does not implement the exercise’s random tie-breaking. If ties matter, collect all best moves and sample one.
5. Fixed-$B$ initialisations must contain all $B$ labels. `rng.integers(B, size=N)` alone does not guarantee this; cell 61’s helper checks it. The one-node nonempty-group chain is also frozen for labelled allocations when $B=N$; do not claim irreducibility there.
6. Exercise 7 requests seed 13, but cell 59 uses `SEED`, defined as 5441. Change that graph-generation call to `seed=13` to reproduce the specified instance; otherwise label results as the 5441 instance. Stored outputs should not be interpreted as answers for seed 13.
7. `SBMlogLs.npy` and `SBMbbests.npy` supply cached optimisation results for the three-block example. These are provided data, not proof of global optimality. The included original files remain available.
8. Block code indexes allocations by vertex identifier and assumes integer labels $0,\ldots,N-1$. Relabel other datasets or use an explicit vertex-to-position mapping. For large $N$, use log-space Stirling recurrences and `gammaln(B+1)` rather than converting enormous counts to floating point.

The notebook itself correctly warns that its model-selection result uses the best partition and fitted probabilities, not the full Bayesian sum and integral. Preserve that qualification when explaining the plot. Repeated stochastic searches can change the best value found.


The cell references above use one-based notebook order, matching the source-export headings. These guides provide derivations and checks; the full long-running notebooks were not re-executed when preparing this vault.
