---
type: study-note
tags: [DATA5441]
---

# Tutorial 5 - guide

[[00_HOME]]

[[Tutorial 5 - source export]]


Read [[Small worlds and preferential attachment]] and [[Power laws and finite-size cutoffs]].

| Exercise / source cells | Task | Checkpoint |
| --- | --- | --- |
| 1.1, 10 | Sweep WS rewiring probability | Plot both distance and clustering relative to the lattice baseline |
| 1.2, 12 | Rewire diagonal lattices of side 10, 30 and 50 through edge swaps | State attempted or successful swaps; compare normalised time such as $2t/L$ |
| 2.1, 19 onwards | Compare BA and density-matched ER | Similar mean degree need not imply similar degree variation |
| 2.2, 32 onwards | Political blogs: empirical, Poisson, ER and BA | Describe model mismatch without declaring a power law from the plot alone |

The WS generator and a degree-preserving edge-swap chain are different processes: the latter preserves all degrees, whereas standard WS rewiring generally does not. Keep disconnectedness conventions consistent when plotting distances.

For a realised BA graph match ER with $q=L_{BA}/\binom N2$. Choosing $m\approx\langle k\rangle/2$ only approximately matches a target network because $m$ is integer and the seed contributes edges. The notebook uses $m=\operatorname{round}(L/N)$ for blogs; explain any residual density difference.

The blogs exercise text mentions a data subdirectory, but cell 33 correctly refers to the supplied file `./out.moreno_blogs_blogs` in that week’s folder. Run the notebook from its own folder. It intentionally converts the network to simple undirected form and removes loops, so interpret the resulting graph rather than the raw directed data.

A BA graph with one added edge per new vertex and a tree seed remains a tree. If your code reports triangles there, inspect the graph construction or seed. On logarithmic plots, omit zero-probability and zero-degree coordinates explicitly; that omission is a plotting restriction, not evidence they were absent from the data.


The cell references above use one-based notebook order, matching the source-export headings. These guides provide derivations and checks; the full long-running notebooks were not re-executed when preparing this vault.
