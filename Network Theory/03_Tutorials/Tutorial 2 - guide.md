---
type: study-note
tags: [DATA5441]
---

# Tutorial 2 - guide

[[00_HOME]]

[[Tutorial 2 - source export]]


Read [[Centrality and Perron-Frobenius]], then [[Walks and clustering]].

| Exercise / source cells | Reasoning task | Checkpoint |
| --- | --- | --- |
| 2.1, 20 onwards | Compare centralities on a star and an axis-aligned square lattice | Star hub dominates; lattice boundary changes degree and distance |
| 2.2, 26 onwards | Directed graph with many leaves feeding a centre and a downstream two-cycle | Incoming eigenvector prestige can concentrate on the terminal cycle |
| 2.3, 30 onwards | Compare Les Misérables and Star Wars rankings | Explain what each centrality rewards; do not treat rankings as interchangeable |
| 3.1, 39 onwards | Square lattice including diagonals | Distances are Chebyshev distance; triangles now exist |
| 3.2, 46 onwards | Compare with an 8-regular random graph | Degrees alone do not fix clustering or distance |

For an $M\times M$ grid with horizontal, vertical and both diagonal nearest-neighbour edges ($M\ge2$),
$$N=M^2,\quad L=2(M-1)(2M-1),\quad d((a,b),(c,d))=\max(|a-c|,|b-d|).$$
The diameter is $M-1$. Corners have degree three and local clustering one; non-corner boundary vertices have degree five and clustering $3/5$; interior vertices have degree eight and clustering $3/7$. Thus
$$\bar C=\frac{4+4(M-2)(3/5)+(M-2)^2(3/7)}{M^2}.$$
For $M=3$: $L=20$, mean distance $13/9$, $\bar C=239/315$ and transitivity $3/5$. Do not apply these diagonal-grid results to the earlier axis-only lattice.

An 8-regular simple graph requires $N>8$ and even $8N$; its mean degree is exactly eight. Under the usual sparse random-regular limit its clustering vanishes and typical distances grow logarithmically. Verify connectedness before computing a whole-graph diameter. The first branching step has eight neighbours; subsequent tree-like steps have seven new opportunities.

For the directed example, state whether edges convey incoming prestige or outgoing influence before choosing an eigenvector. Check damping ranges for Katz and dangling-node handling for PageRank.


The cell references above use one-based notebook order, matching the source-export headings. These guides provide derivations and checks; the full long-running notebooks were not re-executed when preparing this vault.
