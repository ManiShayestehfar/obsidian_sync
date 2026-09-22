---
type: study-note
tags: [DATA5441]
---

# Study route and mastery checklist

[[00_HOME]]

Work through each week in this order: read the lecture export, reconstruct one derivation without looking, attempt the tutorial, then consult its guide and the relevant Newman section. Keep a separate note recording your own wrong answers and why they were wrong.

| Week | Derive from a blank page | Explain in words | Demonstrate computationally |
| --- | --- | --- | --- |
| 1 | $\sum k_i=2L$, walk counts, triangle/clustering formulas | Why local mean and transitivity differ | Load a graph; check simplicity; compute statistics |
| 2 | Katz series, endpoint degree bias | What each centrality rewards | Compare rankings and directed conventions |
| 3 | ER binomial degree law, Poisson limit, $S=1-e^{-cS}$ | Dense versus sparse, giant versus connected | Repeated null-model draws with uncertainty |
| 4 | Detailed balance and invariant distribution | Hard constraints define different null questions | Preserve each move’s invariants; inspect mixing |
| 5 | Ring clustering; BA continuum exponent; power-law moments | Short paths versus navigability | Sweep rewiring and compare BA to fitted ER |
| 6 | Maximum-entropy law; MH ratio; derivative of $\log Z$ | Constraints in expectation; partition-function role | Fit a multiplier and check a held-out statistic |
| 7 | Block-probability MLE; partition counts; acceptance sign | Local optimum, overfitting, evidence versus best score | Multi-start search; compare partitions up to labels |

A useful three-session revision cycle is: (1) definitions and short calculations; (2) derivations and assumptions; (3) model criticism and tutorial interpretation. Space repeats over multiple days and revisit mistakes before rereading comfortable material. This is a suggested study method, not an official course schedule.

Before considering a topic mastered, answer:

- What is random, and what is fixed?
- Is the statement exact, asymptotic, approximate or observed in one simulation?
- What breaks if the graph is disconnected, directed, weighted or has loops?
- Which quantities were fitted, and which test the model?
- Does an algorithm sample a distribution or optimise an objective?
- Which source page and assumptions support the equation?

Use [[Worked revision problems]] for active recall and [[Formula sheet]] for a final check. These are independent study aids, not predictions of exam questions or marking criteria.
