---
type: study-note
tags: [DATA5441]
---

# Tutorial 4 - guide

[[00_HOME]]

[[Tutorial 4 - source export]]


Read [[MCMC and detailed balance]], [[Configuration model and excess degree]] and [[Simulation and uncertainty]].

| Exercise / source cells | Invariants | Main check |
| --- | --- | --- |
| 1.1, 20–22 | $N,L$ | Edge replacement destroys much empirical organisation while preserving density |
| 1.2, 23–26 | $N$ | Dyad resampling approaches independent density $1/2$; edge count varies |
| 1.3, 28–36, method (i) | Stub degrees before simplification | Erasing defects changes the degree sequence |
| 1.3, method (ii) | Every labelled degree | Degree-preserving rewiring tests organisation beyond degrees |

The spaces satisfy $\Omega_3\subset\Omega_2\subset\Omega_1$, but their uniform laws have different expectations. Starting at the empirical graph explains an initial transient; it does not make that graph representative of equilibrium. In a finite irreducible chain, a positive-probability graph is eventually revisited almost surely, but the expected waiting time can be enormous.

**Code checks before rerunning:**

- Cell 4’s knee finder is a heuristic and ignores its `curve` argument by hard-coding a value. It may return no knee. It is not a proof of equilibration.
- Cells 22 and 35 slice `Cs[L:]` by row position. If observations are `step` updates apart, discard by the `time` column instead; some current slices are empty. Cell 35’s `sigmas` is stale because that loop does not assign it from the current data.
- `RUN=False` skips generating cached CSVs while later cells read them. The archive’s original cached output folders are included in the vault; reruns with different settings need newly generated files. Use `mkdir(parents=True, exist_ok=True)` where necessary.
- Cell 33 uses `double_edge_swap(..., nswap=1)`, which repeats proposals until success. This differs from a one-attempt chain that retains invalid proposals. Use the Week 6 single-attempt proposal for an exact symmetric-kernel derivation.
- Nested quotes in some f-strings require a recent Python parser; alternating single and double quotes makes these cells portable.

After burn-in, compare the empirical transitivity with the ensemble distribution. In the degree-fixed space, degree variability is constant by construction and cannot diagnose mixing. Check clustering, edge overlap and multiple starts instead.


The cell references above use one-based notebook order, matching the source-export headings. These guides provide derivations and checks; the full long-running notebooks were not re-executed when preparing this vault.
