---
type: study-note
tags: [DATA5441]
---

# Configuration model and excess degree

[[00_HOME]]

Sources: Week 4; Newman §§12.1–12.6. A degree sequence must have an even sum to admit a stub pairing. A simple realisation additionally requires that the sequence is graphical.

Give vertex $i$ exactly $k_i$ labelled stubs and pair all $2L$ stubs uniformly. Every vertex keeps its degree if a loop contributes two. Self-loops and multiple edges can occur. For $i\ne j$, the expected number of edges is
$$\mathbb E[M_{ij}]=\frac{k_i k_j}{2L-1}.$$
It is an expected multiplicity, not generally the probability of at least one edge. The latter agrees approximately only when multiplicities are negligible. Erasing loops and merging parallel edges changes degrees, so it does not give the uniform simple fixed-degree ensemble.

Following an edge reaches degree $k$ with probability $kp_k/\langle k\rangle$, leaving $k-1$ outgoing opportunities. The mean excess degree is
$$\kappa=\frac{\langle k(k-1)\rangle}{\langle k\rangle}=\frac{\langle k^2\rangle-\langle k\rangle}{\langle k\rangle}.$$
For a suitably regular locally tree-like configuration-model sequence, the supercritical giant-component condition is $\kappa>1$. Equality is a critical or degenerate boundary requiring more care (a degree-two graph is a useful warning).

With $G_0(s)=\sum_kp_ks^k$ and $G_1(s)=G_0'(s)/G_0'(1)$, solve $u=G_1(u)$ and take $S=1-G_0(u)$. This is a textbook extension of the lecture’s branching intuition. Uncorrelated sparse configurations with suitable moments have clustering approximately
$$C\approx\frac{(\langle k^2\rangle-\langle k\rangle)^2}{N\langle k\rangle^3}.$$
Do not use this outside its regime, particularly when heavy tails make collision probabilities substantial or the expression ceases to be small.

For simple fixed-degree sampling, a double-edge swap preserves all degrees. Draw one proposal and retain invalid/rejected steps to establish a clear transition kernel. See [[MCMC and detailed balance]].
