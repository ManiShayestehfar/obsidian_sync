---
tags: [data5441, ch04, methods]
aliases: [MCMC, Graph sampling, Edge swap, Detailed balance, Burn-in]
---
# Markov chain Monte Carlo on graphs

> [!abstract] Summary
> **Markov chain Monte Carlo (MCMC)** samples random graphs by repeatedly making small random changes to a graph. We design the changes so that the chain explores a chosen graph ensemble and has its prescribed probability distribution as equilibrium. The essential issues are **valid moves, ergodicity, detailed balance, equilibration and correlated samples**.
> Chapter: [[Ch04 Sampling random graphs]] · Lecture: **Week 4**

## 1. Motivation: why MCMC?

A random-graph model specifies a space $\Omega$ of admissible graphs and a target distribution $p(g)$. We want to estimate an ensemble property:
$$
\boxed{\mathbb E_p[X]=\sum_{g\in\Omega}p(g)X(g).}
$$
Directly enumerating $\Omega$ is usually impossible, and drawing independent samples may be difficult when graphs must satisfy constraints (e.g. **fixed $L$** or a **fixed degree sequence**). MCMC instead constructs a sequence
$$g_0\longrightarrow g_1\longrightarrow g_2\longrightarrow\cdots$$
of *dependent* random graphs whose long-run distribution is $p(g)$. We can then approximate $\mathbb E_p[X]$ by averaging $X(g_t)$.

## 2. Markov chains and the general MCMC algorithm

> [!definition] Markov chain on graphs
> A Markov chain is a random sequence $(g_t)_{t\ge0}$ taking values in $\Omega$, where the next graph depends only on the current graph:
> $$\Pr(g_{t+1}=h\mid g_t=g,g_{t-1},\ldots)=\Pr(g_{t+1}=h\mid g_t=g)=W(g\to h).$$
> The **transition probabilities** satisfy $W(g\to h)\ge0$ and $\sum_{h\in\Omega}W(g\to h)=1$.
>
> If $w_t(g)=\Pr(g_t=g)$, its evolution is
> $$\boxed{w_{t+1}(h)=\sum_{g\in\Omega}w_t(g)W(g\to h).}$$

> [!algorithm] MCMC sampling of a graph ensemble
> 1. **Choose the target:** specify $\Omega$ and $p(g)$ (which network features are fixed, and which are random?).
> 2. **Initialise:** choose $g_0\in\Omega$, often the observed network $g^*$.
> 3. **Propose a move:** randomly modify $g_t$ according to a transition rule. A disallowed proposal must leave the chain at $g_t$.
> 4. **Update:** obtain $g_{t+1}$; include any self-transition or rejection as a genuine time step.
> 5. **Equilibrate:** discard an initial **burn-in** period.
> 6. **Measure and average:** collect $X(g_t)$ after burn-in, accounting for dependence between successive graphs:
>    $$\boxed{\widehat{\mathbb E_p[X]}=\frac1R\sum_{r=1}^{R}X(g_{t_r}).}$$
>
> In **Week 4**, moves are chosen to sample *uniformly* within constrained graph spaces. [[Metropolis–Hastings]] extends the construction to **non-uniform** targets.

## 3. When does the algorithm sample the intended distribution?

> [!definition] Stationarity and detailed balance
> A distribution $p$ is **stationary** if a chain started with $g_0\sim p$ also satisfies $g_t\sim p$ for every $t$:
> $$\boxed{p(h)=\sum_{g\in\Omega}p(g)W(g\to h).}$$
> A convenient **sufficient** condition is **detailed balance**:
> $$\boxed{p(g)W(g\to h)=p(h)W(h\to g)\qquad(g,h\in\Omega).}$$
> For a **uniform** target $p(g)=1/|\Omega|$, detailed balance reduces to **symmetric transitions**, $W(g\to h)=W(h\to g)$.

> [!proof]- Why detailed balance implies stationarity
> $$\sum_g p(g)W(g\to h)=\sum_g p(h)W(h\to g)=p(h)\sum_g W(h\to g)=p(h).\qquad\square$$

> [!theorem] Conditions for reliable MCMC (finite graph spaces)
> 1. **Closure:** every step stays in $\Omega$; the graph constraints are preserved.
> 2. **Irreducibility/Ergodicity:** every admissible graph can be reached from every other through a sequence of moves with positive probability.
> 3. **Correct equilibrium:** $p$ is stationary; checking **detailed balance** is the standard method used in the lectures.
> 4. **Aperiodicity:** the chain is not forced into a deterministic cycle (a positive probability of staying put is a convenient sufficient condition).
>
> Under these conditions, $\Pr(g_t=h)\to p(h)$ from any starting graph. For a finite irreducible chain, **long-run time averages** converge to ensemble averages even if the chain is periodic; aperiodicity is needed for convergence of its distribution at each time.

**Important distinction:** detailed balance proves *stationarity*, not *mixing*. If a chain cannot reach all admissible graphs, it may sample only a subset even though detailed balance holds.

## 4. Three graph ensembles and their moves

Write $Y=\binom N2$ for the number of possible edges in a labelled, simple, undirected graph.

| Target space | Random move | Preserves | Uniform-target reasoning |
|---|---|---|---|
| $\Omega_N$ (all graphs with $N$ vertices) | **Edge toggle:** choose a node pair and add/delete its edge | $N$ | Every toggle has an equally likely reverse |
| $\Omega_{N,L}$ (exactly $L$ edges) | **Edge replacement:** remove an edge, add a non-edge | $N,L$ | Forward and reverse replacements have equal probabilities |
| $\Omega_{\boldsymbol z}$ (fixed degrees $z_1,\ldots,z_N$) | **Double-edge swap:** rewire two edges without changing endpoints' degrees | Every $z_i$ (hence $N,L$) | A symmetric proposal with invalid moves rejected is reversible |

### Case 1 — Fixed $N$: edge toggling

Select one of the $Y$ unordered node pairs uniformly and **toggle** its edge: $0\leftrightarrow1$.

- The move preserves $N$ and can reach every graph in $\Omega_N$.
- A one-edge change has the same probability $1/Y$ in either direction, so the **uniform distribution** $p(g)=2^{-Y}$ is stationary.
- **Pitfall:** every toggle changes the parity of $L$. The non-lazy chain has period 2; occasionally **stay put** to remove periodicity.
- **Efficiency:** this ensemble typically contains $L\approx Y/2$ edges. It is unsuitable for obtaining a *sparse, fixed-$L$* graph by waiting for a rare configuration.

### Case 2 — Fixed $N,L$: edge replacement

1. Choose one of the $L$ existing edges uniformly and remove it.
2. Choose uniformly among the $Y-L+1$ absent pairs **after removal**, including the removed edge, and add it.

The forward probability for a particular nontrivial replacement is

$$\boxed{W(g\to h)=\frac{1}{L(Y-L+1)}=W(h\to g).}$$

Thus the chain samples **uniformly on $\Omega_{N,L}$** once equilibrated. Re-adding the removed edge produces a self-transition. For $L=0$ or $L=Y$, the space contains only one graph, so no replacement is needed.

> [!remark] Why constrain $L$ directly?
> Starting from an observed sparse network and using a fixed-$N$ edge-toggle sampler will generally drive the edge count towards $Y/2$. Fixing $L$ avoids this mismatch and gives a more relevant null model when comparing statistics such as clustering.

### Case 3 — Fixed degree sequence: double-edge swapping

Let $\boldsymbol z=(z_1,\ldots,z_N)$ be a **graphical** degree sequence. Starting from any simple graph realising it:

1. Choose two distinct edges, such as $\{a,b\}$ and $\{c,d\}$.
2. Propose one of the alternative pairings, e.g. $\{a,d\}$ and $\{c,b\}$.
3. **Accept the switch only if** it creates neither self-loops nor parallel edges; otherwise **stay at the current graph**.

Each valid switch removes one incident edge and adds one incident edge at each of the four endpoints, so **every degree is unchanged**. With symmetric selection of the two edges and the proposed pairing, including invalid proposals as self-transitions, the transition is reversible for a uniform target.

> [!warning] Symmetry can be lost by changing the proposal rule
> Choosing only among **currently valid** swaps, or repeatedly retrying until one succeeds, need not give equal forward and reverse transition probabilities. A degree-preserving move alone does **not** establish uniform sampling. Check the *actual* proposal probabilities (or use an appropriate acceptance correction).

This is a **simple-graph, degree-preserving null model**. It is different from unconstrained configuration-model **stub pairing**, which may create self-loops and parallel edges; see [[Configuration model]].


## 5. Equilibration, dependence and interpretation

> [!definition] Equilibration and correlation times
> - **Equilibration time $t_{\mathrm{eq}}$:** time required for the Markov chain to approximately forget its initial graph and approach the target distribution $p(g)$. Earlier samples are discarded (**burn-in**).
> - **Correlation time $t_{\mathrm{corr}}$:** characteristic time over which dependence between successive sampled graphs (or their measured statistics) decays. MCMC samples are generally **not independent**.

Both timescales describe how quickly the chain **forgets its previous state**, so they are often comparable:
$$
t_{\mathrm{eq}}\sim t_{\mathrm{corr}}.
$$
### Why do the timescales depend on $Y$ or $L$?

Each MCMC step changes only a small part of the graph. To substantially change the graph, the chain must update a significant fraction of its relevant edges.

| MCMC method | Probability of selecting an edge | Characteristic timescale |
|---|---|---|
| **Edge toggling** (fixed $N$) | $1/Y$, where $Y=\binom N2$ | $O(Y)$ |
| **Edge replacement** (fixed $N,L$) | $1/L$ for removing an existing edge | $O(L)$ |
| **Double-edge swap** (fixed degrees) | $O(1/L)$ for selecting an existing edge | $O(L)$ (heuristic) |

For edge toggling, the probability that a particular potential edge has **never been selected** after $t$ steps is
$$
\left(1-\frac1Y\right)^t\approx e^{-t/Y}.
$$
Similarly, for edge replacement, the probability that a particular original edge has **not been removed** is
$$
\left(1-\frac1L\right)^t\approx e^{-t/L}.
$$

Hence the characteristic times required to update a substantial fraction of the graph are
$$
\boxed{t_{\mathrm{eq}}\sim t_{\mathrm{corr}}\sim Y\ \text{(toggling)},\qquad
t_{\mathrm{eq}}\sim t_{\mathrm{corr}}\sim L\ \text{(replacement/swaps)}.}
$$

### Estimating ensemble properties

After burn-in, estimate a network statistic $X$ from $R$ sampled graphs:
$$
\boxed{\widehat{\mathbb E_p[X]}=\frac1R\sum_{r=1}^R X(g_{t_r}).}
$$

Distinguish two sources of variation:

- **Ensemble spread $\sigma_X$:** variation of $X$ across graphs drawn from $p(g)$; used to judge whether the observed $X(g^*)$ is unusual.
- **Monte Carlo error:** uncertainty in the estimated ensemble mean. Correlated samples contain less information than independent samples; increasing the spacing between observations reduces dependence.

**Practical rule:** discard burn-in, sample over a period much longer than the correlation time, and check convergence rather than relying solely on the rough $Y$ or $L$ estimates.

> [!warning] Common pitfalls
> - **A stable-looking trace is not proof of mixing.** A chain may be stuck or explore only one region of $\Omega$.
> - **Do not discard rejected steps:** remaining at the same graph is part of the Markov chain; recording only successful moves can bias the result.
> - **Do not confuse rare with impossible.** In a finite irreducible chain, every admissible graph is visited eventually with probability 1, even if visits are exceedingly rare.
> - **Preserving degrees is not preserving clustering.** Degree-preserving swaps intentionally randomise other structures; this is what makes the null-model comparison informative.

> [!exam] How to read an MCMC trace (Trial Exam 1, Q3)
> If $g_0=g^*$ is the observed graph, then $X(g_0)$ is the **observed value**. The post-burn-in fluctuations estimate the **null ensemble**, and their mean estimates $\mathbb E_p[X]$.
>
> For a finite irreducible degree-preserving chain, $\Pr(\text{eventually revisit }g^*)=1$, while an impossible statistic (e.g. negative clustering) is never observed. **Eventual occurrence** is not the same as **typical occurrence**.

> [!selftest]- Check your understanding
> 1. Why is detailed balance useful? — It guarantees the chosen target distribution is stationary.
> 2. Which move preserves every degree? — A valid double-edge swap.
> 3. Why are MCMC samples not i.i.d.? — Each graph is generated from the preceding graph.
> 4. Why is a flat trace insufficient? — A poorly mixing chain can remain in one region of the graph space.

---
Related: [[Random graph ensembles]] · [[Configuration model]] · [[Metropolis–Hastings]]