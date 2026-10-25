---
tags: [inference]
---

# Reconstruction from node activity

Suppose the edges are hidden and only the vertices’ states are measured. Similar state histories may suggest a link, but they can also arise from indirect paths or common causes. A generative model asks whether a proposed graph makes the observations plausible; it requires a different likelihood from link prediction on an observed subgraph.

## What is observed and what is known

In the tutorial, $D=(s_i^{(t)})\in\{-1,+1\}^{T\times N}$ contains $T=200$ configurations of $N=50$ vertices. The synthetic generator has $L=100$ edges and coupling $J=0.4$. **The reconstruction is supplied with $L$**; inferring the number of edges is not part of this benchmark.

![[tutorial-9-cell-39-plot-1.png|300]]
*Supplied Tutorial 9, cell 39: columns are vertices and rows are observed configurations. This array contains states, not an adjacency matrix.*

> [!definition] Correlation reconstruction
> For each pair, compute Pearson correlation across observations,
> $$r_{ij}=\frac{\sum_t(s_i^{(t)}-\bar s_i)(s_j^{(t)}-\bar s_j)}{\sqrt{\sum_t(s_i^{(t)}-\bar s_i)^2}\sqrt{\sum_t(s_j^{(t)}-\bar s_j)^2}}.$$
> Rank distinct pairs $i<j$ and select the largest $L$ scores. A constant column has undefined correlation; setting its score to zero is a convention, not evidence of independence. The tutorial favours positive correlations, consistent with its positive-coupling generator.

The supplied full-data example recovers 44 of 100 true edges. Varying $T$ probes how data quantity affects that particular reconstruction. At $T=0$ there is no empirical correlation to estimate; for very short or dependent records uncertainty can be substantial.

If truth has $L$ edges among $Y=\binom N2$ dyads and a baseline chooses $L$ dyads uniformly, expected overlap is $L^2/Y$: each true edge is selected with probability $L/Y$. For $N=50,L=100$, this is $10000/1225\approx8.16$ edges. This is an expectation, not an exact baseline in every draw.

## Why the normaliser matters

> [!definition] Ising graph likelihood
> With zero fields and known uniform coupling,
> $$E_G(s)=-J\sum_{\{i,j\}\in E(G)}s_i s_j,\qquad P(s\mid G)=e^{-E_G(s)}/Z(G),\qquad Z(G)=\sum_s e^{-E_G(s)}.$$
> For independent configurations,
> $$-\log P(D\mid G)=\sum_tE_G(s^{(t)})+T\log Z(G).$$
> Since $Z(G)$ depends on the candidate graph, energy alone is not a valid graph-inference likelihood.

Evaluating $Z$ directly sums $2^N$ configurations. The tutorial replaces the joint likelihood with a tractable product of node-conditionals.

> [!theorem] Ising pseudolikelihood
> Define $h_i^{(t)}=J\sum_{j\ne i}A_{ij}s_j^{(t)}$. Then
> $$P(s_i^{(t)}\mid s_{-i}^{(t)},G)=\frac1{1+e^{-2s_i^{(t)}h_i^{(t)}}},$$
> so negative log pseudolikelihood is
> $$F_{PL}(G)=\sum_{t,i}\log\left(1+e^{-2s_i^{(t)}h_i^{(t)}}\right).$$

**Proof.** Holding all other states fixed, the energy is $-s_i h_i+C$, with $C$ independent of $s_i$. Normalising the two weights $e^{h_i}$ and $e^{-h_i}$ gives the conditional probability. Taking minus the logarithm of their product gives $F_{PL}$. The conditionals share variables, so their product is generally **not** the joint probability. $\square$

For $J>0$, alignment $s_i h_i>0$ should increase the conditional probability. This check fixes the sign ambiguity in the handwritten formula on Lecture 9 p.13. The partition function is a sum of exponential weights, not a sum of energies.

## Sample candidate graphs, then evaluate

> [!algorithm] Fixed-$N,L$ graph inference
> 1. Start from a simple graph with the prescribed $N,L$.
> 2. Exchange one uniformly selected edge and one uniformly selected non-edge.
> 3. For $\Delta F=F_{PL}(G')-F_{PL}(G)$, accept with $\min(1,e^{-\Delta F})$; retain the current graph on rejection.
> 4. After a justified burn-in, retain samples, including repeats, and assess uncertainty and exploration.
>
> The target is proportional to $PL(G;D)$ under a uniform fixed-$L$ graph prior. This is a pseudolikelihood-based target, not the exact Ising posterior. Increasing an inverse temperature would change it to an optimisation-oriented tempered target.

> [!code]- Stable evaluation of the score
> ```python
> import networkx as nx
> import numpy as np
>
> def negative_log_pseudolikelihood(g, states, J=0.4):
>     nodes = list(g)
>     states = np.asarray(states, dtype=float)
>     if (g.is_directed() or g.is_multigraph() or nx.number_of_selfloops(g)
>         or states.ndim != 2 or states.shape[1] != len(nodes)
>         or not np.isin(states, [-1, 1]).all() or not np.isfinite(J) or J < 0):
>         raise ValueError('Use a simple graph, finite J>=0, and T-by-N ±1 states')
>     # Columns of states must follow the order in nodes.
>     A = nx.to_numpy_array(g, nodelist=nodes, weight=None)
>     fields = J * (states @ A)
>     return float(np.logaddexp(0.0, -2 * states * fields).sum())
> ```
> Use the symmetric edge replacement and Metropolis machinery in [[Monte Carlo sampling]] with log target $-F_{PL}$. `logaddexp` avoids numerical overflow; preserve the state-column/node-order mapping.

![[tutorial-9-cell-49-plot-2.png|850]]
*Supplied Tutorial 9, cell 49: two graph-sampling runs using different $J$. Left: overlap with the true graph, used only for evaluation. Right: negative log pseudolikelihood per observed node state. These are different targets and their samples must not be pooled.*

The supplied chains have very low post-burn-in acceptance, around $0.005$ in this run. A flattening trace is insufficient evidence of mixing. At $J=0$, every conditional is $1/2$, $F_{PL}=TN\log2$ is constant and the graph target is uniform; expected edge overlap returns to the chance value.

Sweeping $J\in[0,1]$ compares modelling assumptions. Do not choose $J$ by minimising its raw pseudolikelihood score alone or by using unknown true edges in a real reconstruction: use a stated validation/fitting procedure. The benchmark can use truth to measure recovery, but that information is unavailable in an application.

## For revision

- Distinguish observations, unknown graph, supplied edge count and assumed coupling.
- Derive the logistic conditional and explain why $Z(G)$ cancels there but not from the joint likelihood.
- Explain Pearson ranking, the $L^2/Y$ overlap baseline, the MH sign and the difference between joint likelihood and pseudolikelihood.

> [!reference]- Sources
> Lecture Week 9 pp.11–15; Tutorial 9 §2 and Ex.2.1–2.2, cells 42–51. Jenny’s notes Week 9 supplies background but omits the graph-dependent normaliser; the current lecture/notebook and the derivation above correct it. Figures are supplied notebook outputs. Newman Chapter 9 provides measurement/inference context.
