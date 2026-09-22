---
type: study-note
tags: [DATA5441]
---

# Worked revision problems

[[00_HOME]]

Try each question before expanding its answer. These are original study exercises grounded in the supplied material.

## 1. Which clustering coefficient?
A triangle has one extra leaf attached to one of its vertices. Find $\bar C$ and transitivity, counting degree-one local clustering as zero.

> [!answer]- Solution
> Degrees are $(3,2,2,1)$; local coefficients are $(1/3,1,1,0)$. Hence $\bar C=7/12$. There is one triangle and five wedges, so transitivity is $3/5$.

## 2. The friendship-paradox distribution
A graph has degree distribution $p_1=1/2,p_3=1/2$. What is the mean degree at a uniform edge endpoint?

> [!answer]- Solution
> $\langle k\rangle=2$ and $\langle k^2\rangle=5$, so the endpoint mean is $5/2$. Endpoint degree probabilities are $1/4$ and $3/4$. This does not alone determine the uniform-vertex-then-neighbour distribution; degree correlations matter for that protocol.

## 3. Sparse ER does not imply connectivity
A model uses $N=10000$ and $q=2/(N-1)$. Estimate its mean degree and giant fraction. Is it expected to be connected?

> [!answer]- Solution
> Mean degree is exactly two. The large-$N$ equation gives $S\approx0.7968$. A positive fraction remains outside the giant, so whole-graph connectivity is not predicted. The giant-fraction number is an asymptotic approximation to a random finite graph.

## 4. A stationary but oscillating chain
A chain on simple graphs flips one uniformly selected dyad at every step. Prove that uniform graph probability is stationary, then explain why its distribution need not converge from a fixed graph.

> [!answer]- Solution
> Every neighbouring graph pair has equal transition probability $1/Y$, so detailed balance holds with the uniform law. Edge parity changes every step, giving period two. Retain the current graph with probability $1/2$, or resample the selected dyad with a fair Bernoulli variable, to remove this periodicity.

## 5. Is a hub sufficient for a giant?
A configuration-model degree law has $p_1=3/4,p_3=1/4$. Compute $\kappa$.

> [!answer]- Solution
> Mean degree is $3/2$ and $\langle k(k-1)\rangle=3/2$, so $\kappa=1$. This is the critical boundary, not the strict supercritical regime. A broad-looking distribution or an occasional degree-three vertex is not sufficient evidence of a giant fraction.

## 6. A tail exponent is not a survival exponent
For $p_k\propto k^{-5/2}$, which of the first two moments diverges in the infinite-tail limit, and what is the natural sample maximum scale?

> [!answer]- Solution
> The mean is finite; the second moment diverges. The survival tail scales as $k^{-3/2}$, so $k_{max}\asymp N^{2/3}$ under independent-tail sampling. Do not set the single-value mass equal to $1/N$.

## 7. Weighting an ERGM
On a fixed-degree graph space, the target is $p(g)\propto e^{10C(g)}$. A symmetric proposal raises clustering from $0.20$ to $0.25$. What is its acceptance probability, and that of the reverse proposal?

> [!answer]- Solution
> The forward ratio is $e^{0.5}>1$, so accept with probability one. The reverse probability is $e^{-0.5}\approx0.6065$. No partition function is needed for these moves at fixed parameter.

## 8. Derive edge-independent ER from entropy
Maximise entropy on all simple graphs while fixing expected edge count $\ell$.

> [!answer]- Solution
> The maximum-entropy distribution is $p_\beta(g)\propto e^{\beta L(g)}$. Summing over independent dyad indicators gives $Z=(1+e^\beta)^Y$. Thus each edge has probability $q=e^\beta/(1+e^\beta)$; matching the moment gives $q=\ell/Y$ and $\beta=\log[\ell/(Y-\ell)]$ for $0<\ell<Y$. Endpoint constraints are limiting deterministic cases.

## 9. Why cannot raw SBM fit choose the model size?
Explain why a separate block for every vertex maximises a Bernoulli SBM’s fitted likelihood.

> [!answer]- Solution
> Every cross-block dyad contains one observation and can be fitted with probability equal to its observed indicator. Every likelihood factor is one, so total likelihood is one and negative log-likelihood zero. Complexity control or integrated model comparison is necessary; a perfect in-sample fit is not evidence of useful groups.

## 10. Read a simulation claim critically
A chain’s clustering trace is flat, its acceptance rate is 95%, and its mean differs from the empirical graph by ten standard errors. Does this establish that the empirical graph is anomalous?

> [!answer]- Solution
> No. A flat trace and high acceptance can coexist with slow exploration. Check multiple starts, autocorrelation and support. Standard error measures uncertainty in the estimated model mean, while a single empirical graph should usually be compared with ensemble variability. Also identify which statistics were used to fit the model.
