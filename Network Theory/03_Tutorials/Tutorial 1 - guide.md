---
type: study-note
tags: [DATA5441]
---

# Tutorial 1 - guide

[[00_HOME]]

[[Tutorial 1 - source export]]


Read [[Walks and clustering]] and [[Sampling and friendship paradox]] first.

| Source exercise / cells | What to do | Checkpoint |
| --- | --- | --- |
| Quiz 1, 4–5 | Count edges, distances, triangles by hand, then compare code | $N=6,L=7$, diameter $2$, hub $C=1/5$, mean local $7/10$, transitivity $3/7$ |
| Quiz 2 and Ex.4.1, 6–11 | Inspect Karate Club and its split | A drawing is evidence of neither optimal communities nor causation |
| Ex.4.2, 12–16 | Load Facebook edges and inspect graph type | An undirected `Graph` merges duplicate edges; it can still contain self-loops |
| Ex.4.3, 17–24 | Compare uniform-node degrees and neighbours; estimate clustering | Explain the sampling distribution before using a friendship-paradox formula |
| Airport example, 27–29 | Repeat on another dataset | Reusing a variable from Facebook can silently print the wrong comparison |
| Quiz 3, 30–32 | Count possible friendship graphs | $2^{N(N-1)/2}$ grows extremely rapidly; use logarithms |

In cell 3, nodes are sampled without replacement and one neighbour is selected for each. This is **not** uniform-edge endpoint sampling. Also ensure `max(Rs) <= N` and handle isolated vertices. Cell 9’s `np.mean(avg_degree_karate)` averages running means, not vertex degrees. Use the last running mean for its final sample, or `sum(dict(G.degree()).values()) / G.number_of_nodes()` for the exact graph mean. Cell 22 repeats the running-mean issue for neighbours; cell 29 also prints an earlier `avg_degree` variable rather than the airport mean.

Cell 32 solves a strict inequality in a real-valued $N$. Use the smallest integer satisfying it (test the candidate), rather than unconditional rounding. With the notebook’s sand estimate, the answer is 12 vertices.

The animation is optional and separate from the mathematics. Create `outputs/` before saving; the expression `6 - 3*log1p(degree)` becomes negative for sufficiently large degrees and needs a positive size rule. The provided 77-edge Karate file is different from NetworkX’s 78-edge example used in Week 7, so exact statistics can differ.

**Explain aloud:** why do duplicated reverse edges in the input not double $L$ in a simple undirected graph? Why are mean local clustering and transitivity different?


The cell references above use one-based notebook order, matching the source-export headings. These guides provide derivations and checks; the full long-running notebooks were not re-executed when preparing this vault.
