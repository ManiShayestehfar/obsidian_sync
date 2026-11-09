---
tags: [data5441, ch04, models]
aliases: [Fixed degree sequence, Stub matching, Molloy–Reed, Excess degree]
---

---
tags: [data5441, ch04, models]
aliases: [Configuration model, Stub-matching model, Degree-preserving null model]
---

# Configuration model

> [!abstract] Summary
> The **configuration model** generates random networks with a prescribed degree sequence $\boldsymbol z=(z_1,\ldots,z_N)$. Unlike ER graphs, it preserves degree heterogeneity. Random **stub matching** may produce self-loops and parallel edges; restricting to simple graphs requires extra care. In the sparse, locally tree-like regime, clustering is typically small, distances depend on the mean *excess degree*, and the giant-component threshold is controlled by $\langle z^2\rangle/\langle z\rangle$.
> Chapter: [[Ch04 Sampling random graphs]] · Lecture: **Week 4, configuration model**

## 1. Motivation and construction

ER graphs fix the expected degree but generate approximately Poisson degrees in the sparse limit. To test whether features such as clustering or short paths are explained **by the observed degrees alone**, we instead keep *every node's degree* fixed and randomise its connections.

> [!definition] Configuration model (stub matching)
> Given nonnegative integers $z_1,\ldots,z_N$ with
> $$\sum_{i=1}^N z_i=2L,\qquad \langle z\rangle=\frac1N\sum_i z_i=\frac{2L}{N},$$
> construct a random multigraph as follows:
> 1. Give vertex $i$ exactly $z_i$ **stubs** (half-edges).
> 2. Choose a uniformly random perfect matching of all $2L$ stubs.
> 3. Join each matched pair to form an edge.

Every stub is used once, so the degree of vertex $i$ is **exactly $z_i$**, counting self-loops twice. The sum $\sum_i z_i$ must be even, but stub matching does **not** require the sequence to be graphical as a *simple* graph.

> [!warning] Multigraphs versus simple graphs
> - **Stub-matching ensemble:** allows **self-loops** ($i\leftrightarrow i$) and **parallel edges** (multiple links joining the same pair).
> - **Uniform simple-graph ensemble:** contains only simple graphs with the same degree sequence. It requires a **graphical** sequence and can be sampled using suitable degree-preserving [[Markov chain Monte Carlo on graphs|edge-swap MCMC]]. The proposal and acceptance rule must give the intended stationary distribution.
> - Uniform matching of labelled stubs does **not** mean uniform probability over *multigraph adjacency matrices*. Conditioning stub matching on producing a simple graph, however, gives a uniform simple-graph realisation of the degree sequence.

> [!definition] Graphical degree sequence
> A sequence is **graphical** if some simple undirected graph has exactly those degrees. An even degree sum is necessary but **not sufficient**: $(3,3,1,1)$ has an even sum but cannot describe a simple graph. The [[Erdos-Renyi graphs|ER model]] has no such prescribed-degree restriction; for simple-graph degree sequences, see the Erdős–Gallai criterion.

## 2. Expected connections

The model favours links between high-degree vertices simply because they possess more stubs.

> [!proposition] Expected number of edges between two distinct vertices
> Write $A_{ij}$ for the **number of edges** between $i$ and $j$ (including parallel edges). For $i\ne j$,
> $$\boxed{\mathbb E[A_{ij}]=\frac{z_i z_j}{2L-1}\approx\frac{z_i z_j}{2L}=\frac{z_i z_j}{N\langle z\rangle}.}$$

**Why?** Each of the $z_i$ stubs at $i$ has probability $z_j/(2L-1)$ of being paired to a stub at $j$. Summing these probabilities gives the expected edge multiplicity.

> [!important] Expected count $\ne$ link probability
> In a multigraph, $A_{ij}$ can exceed $1$, so $\mathbb E[A_{ij}]$ is **not generally** $\Pr(A_{ij}\ge1)$. When $z_i z_j/(2L)\ll1$ and multiple edges are negligible,
> $$\Pr(i\text{ linked to }j)\approx\frac{z_i z_j}{2L}.$$
> This approximation may fail for hubs with very large degrees. The term $z_i z_j/(2L)$ also appears as the configuration-model **null expectation** in [[Community detection|modularity]].

## 3. Sparsity, clustering and distances

Define the empirical degree distribution $P(z)$ and its moments
$$\langle z\rangle=\sum_z zP(z),\qquad \langle z^2\rangle=\sum_z z^2P(z).$$

**Sparsity.** Since $L=N\langle z\rangle/2$, if $\langle z\rangle$ stays bounded as $N\to\infty$, then $L=O(N)$: the network is sparse.

### Clustering

For low degrees relative to the network size, links are approximately independent locally. Two neighbours of a vertex are therefore unlikely to be linked merely by random matching.

> [!proposition] Clustering in the sparse configuration model (approximation)
> Under standard locally tree-like assumptions with sufficiently controlled degree moments,
> $$\boxed{C\approx\frac{1}{N\langle z\rangle}\left(\frac{\langle z^2\rangle-\langle z\rangle}{\langle z\rangle}\right)^2
> =\frac{(\langle z^2\rangle-\langle z\rangle)^2}{N\langle z\rangle^3}.}$$
> In particular, for bounded moments and $\langle z\rangle$ bounded away from zero, $C=O(1/N)\to0$.

**Interpretation.** Fixing degrees can explain why hubs have many links, but generally **does not produce persistent triangle closure** in the sparse, finite-moment limit. The formula need not apply to degree sequences with extremely large hubs or diverging moments.

### Distances and excess degree

Following an edge reaches higher-degree vertices more frequently. The degree of a vertex reached this way has the **size-biased** distribution (see [[Sampling and friendship paradox]])
$$\Pr(z_{\mathrm{reached}}=z)=\frac{zP(z)}{\langle z\rangle}.$$

One edge was used to arrive, leaving $z-1$ **new** edges. Their expected number is the **mean excess degree**:
$$\boxed{\kappa=\sum_z(z-1)\frac{zP(z)}{\langle z\rangle}=\frac{\langle z^2\rangle-\langle z\rangle}{\langle z\rangle}.}$$

In a locally tree-like supercritical graph with $\kappa>1$ and suitable regularity conditions, neighbourhoods expand roughly as $\kappa^d$. Thus the **typical distance within the giant component** scales as
$$\boxed{\ell_{\mathrm{typ}}\sim\frac{\log N}{\log\kappa}.}$$
This is a branching approximation for typical distances, **not an exact diameter formula**. For sparse ER (Poisson degrees), $\kappa=\langle z\rangle$, recovering the familiar ER estimate.

## 4. Giant-component threshold

> [!theorem] Molloy–Reed criterion (standard sparse configuration-model regime)
> The transition is governed by the mean excess degree:
> $$\boxed{\kappa=\frac{\langle z^2\rangle-\langle z\rangle}{\langle z\rangle}.}$$
> - If $\kappa>1$, the model is **supercritical** and has a giant component under the standard regularity assumptions.
> - If $\kappa<1$, it is **subcritical**, with no giant component.
> - $\kappa=1$ is the **critical boundary**, requiring separate care in degenerate cases.

Equivalently, the supercritical condition is
$$\boxed{\frac{\langle z^2\rangle}{\langle z\rangle}>2.}$$

**Why?** Exploring a component resembles a branching process: after arriving along an edge, a node produces on average $\kappa$ further edges. If $\kappa>1$, exploration can continue on a macroscopic scale; if $\kappa<1$, it dies out. At the boundary, special distributions (notably all vertices of degree $2$) require separate analysis, so the strict condition should not be read as an unconditional *if and only if* for every degree sequence.

### Size of the giant component

The threshold tells us *whether* a giant can exist. To find its **fraction** $S$, use generating functions:
$$G_0(s)=\sum_zP(z)s^z,\qquad G_1(s)=\frac{G_0'(s)}{\langle z\rangle}. $$

Let $u$ be the probability that following a random edge **does not** lead to the giant component. Under the locally tree-like approximation, it solves
$$\boxed{u=G_1(u),\qquad S=1-G_0(u),}$$
where $u$ is the **smallest solution in $[0,1]$**. A vertex of degree $z$ avoids the giant if all $z$ outgoing branches fail, with probability $u^z$; averaging gives $G_0(u)=1-S$.

> [!remark] Check against ER
> For Poisson degrees, $\langle z^2\rangle=\langle z\rangle^2+\langle z\rangle$, hence $\kappa=\langle z\rangle$. The criterion reduces to $\langle z\rangle>1$, and the generating-function equations give $S=1-e^{-\langle z\rangle S}$.

## 5. Uses and exam essentials

| Question | Configuration-model answer |
|---|---|
| What is preserved? | Every node's degree $z_i$ |
| What is randomised? | Which stubs are paired, hence which nodes are connected |
| Is the result necessarily simple? | **No**: loops and parallel edges can occur |
| Expected connection count | $\mathbb E[A_{ij}]=z_i z_j/(2L-1)$ for $i\ne j$ |
| Sparse if… | $\langle z\rangle=O(1)$ |
| Clustering with controlled moments | Typically $C=O(1/N)\to0$ |
| Giant component | Supercritical when $\langle z^2\rangle/\langle z\rangle>2$ |
| Typical distances | Roughly $\log N/\log\kappa$ when $\kappa>1$ |

> [!exam] Trial Exam 2, Question 7(c)(i)
> If $P(z)$ is uniform on $\{1,\ldots,z^*\}$, then
> $$\langle z\rangle=\frac{z^*+1}{2},\qquad \langle z^2\rangle=\frac{(z^*+1)(2z^*+1)}6,$$
> so
> $$\frac{\langle z^2\rangle}{\langle z\rangle}=\frac{2z^*+1}{3}>2\iff z^*>\frac52.$$
> Since $z^*$ is an integer, the first supercritical value is **$z^*=3$**.

> [!warning] Common pitfalls
> - **Even degree sum is not enough** for a *simple* realisation; the sequence must be graphical.
> - Replacing a multigraph by `nx.Graph` and removing self-loops generally **changes its degrees**; this does not sample the fixed-degree simple ensemble.
> - Uniform stub matching is different from sampling uniformly over all multigraphs.
> - The formulas for clustering and distances are **asymptotic approximations**, not universal identities for arbitrary degree sequences.
> - Large observed clustering relative to this null model suggests structure beyond what the degree sequence alone explains.

> [!code]- NetworkX (tutorial context)
> ```python
> assert sum(z) % 2 == 0                      # enough for stub pairing
> M = nx.configuration_model(z, seed=13)    # MultiGraph; degrees preserved
> G = nx.Graph(M)
> G.remove_edges_from(nx.selfloop_edges(G)) # simple graph; degrees may change
> # For simple graphs with the exact degrees, first check nx.is_graphical(z)
> # and use an appropriate degree-preserving simple-graph sampler.
> ```

> [!selftest]- Self-test
> 1. Why does the configuration model produce more links between hubs? — Hubs have more stubs available for pairing.
> 2. Why can it have loops and multiple edges? — Stubs are paired without forbidding these outcomes.
> 3. Why does $\langle z^2\rangle$ control the giant-component threshold? — Following an edge biases arrivals towards high-degree nodes; the resulting mean excess degree is $\kappa$.

---

Related: [[Sampling and friendship paradox]] · [[Erdos-Renyi graphs]] · [[Percolation and robustness]] · [[Power laws]] · [[Markov chain Monte Carlo on graphs]]
