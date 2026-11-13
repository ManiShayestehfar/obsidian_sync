---
tags: [data5441, ch10, dynamics]
aliases: [Robustness, Resilience, Random failures, Targeted attacks, Critical failure fraction]
---

# Percolation and robustness of random graphs

> [!abstract] Summary
> **Network robustness** asks how much connectivity survives random failures or deliberate attacks. For a large **uncorrelated, locally tree-like** random graph, the giant component survives uniform random deletion with probability $q$ when
>
> $$\boxed{(1-q)\left(\frac{\langle z^2\rangle}{\langle z\rangle}-1\right)>1.}$$
>
> The variance of the degree distribution is decisive: hubs make scale-free networks **robust to random deletion** but often **fragile to targeted hub removal**. The same $p_c$ governs uniform edge and node failures in the configuration-model limit, although their finite-size curves differ.
>
> **Study order:** observable $K_1$ → giant-component criterion → random failures and $q_c$ → ER/regular/BA/two-point examples → simulation and diameter → targeted attack.
>
> Chapter: [[Ch10 Resilience and percolation]] · **2026 lecture pp. 128–129, 136–143** · **Tutorial 10 §§2–3**.

## 1. What does robustness measure?

Examples in the lecture include internet traffic after cables fail, power transmission after substations fail, and connectivity relevant to epidemic control. To make the question mathematical, **remove part of a network and measure what remains connected**.

> [!definition] Failure experiment and giant component
> Start with a graph $G_0$ with $N_0$ vertices and $L_0$ edges. Let $q\in[0,1]$ be the probability that a particular element fails; $p=1-q$ is its survival probability.
> - **Bond failure:** delete edges independently, leaving the vertices.
> - **Site failure:** delete vertices independently, including all incident edges.
> - **Targeted attack:** delete chosen vertices according to network information, typically highest degree first; this is **not uniform random failure**.
>
> Write $N_1(q)$ for the largest surviving connected component's size. The principal measured quantity is
> $$\boxed{K_1(q)=\frac{N_1(q)}{N_0}}$$
> using the **original** node count $N_0$ even after deleting vertices.

> [!remark] What is a giant component?
> A component is **giant** if its size is proportional to $N$ as $N\to\infty$, i.e. $N_1/N\to\theta>0$. On a finite network, a small $K_1$ may still be nonzero even beyond the infinite-size critical point. A giant-component transition is **not** the same as the network becoming completely empty.

> [!definition] Diameter (second tutorial observable)
> For a connected graph $H$, $D(H)=\max_{u,v\in H}d_H(u,v)$, where $d_H$ is shortest-path distance. For disconnected $G$, Tutorial 10 computes the diameter **only of the largest component** $G[C_1]$.
> - If $C_1$ is a singleton, its diameter is $0$.
> - If **no vertices remain**, the diameter is undefined (record `NaN`, not $0$).
>
> $K_1$ and diameter measure **different aspects** of breakdown.

## 2. First result: when does a random graph have a giant component?

Let $P(z)$ be the degree distribution and define its moments

$$\langle z\rangle=\sum_z zP(z),\qquad\langle z^2\rangle=\sum_z z^2P(z).$$

A graph reached by following edges does **not** sample the degree distribution uniformly.

> [!definition] Degree bias / excess degree
> Following a uniformly chosen edge to one of its endpoints reaches a degree-$z$ node with probability
> $$\boxed{P_{\mathrm{edge}}(z)=\frac{zP(z)}{\langle z\rangle}.}$$
> Such a node has $z-1$ **unused** edges, since one edge was needed to reach it. Their mean number is
> $$\boxed{\kappa=\sum_z(z-1)P_{\mathrm{edge}}(z)=\frac{\langle z^2\rangle}{\langle z\rangle}-1.}$$

![[Assets/w10-size-biased-degree.png|680]]

*For $P(4)=P(12)=1/2$, a random node has probability $1/2$ of degree $12$, but following a random edge reaches degree $12$ with probability $12/(4+12)=3/4$.*

> [!derivation]- Why exactly does the factor $zP(z)$ appear? (lecture p. 137)
> Among approximately $NP(z)$ degree-$z$ vertices there are approximately $NzP(z)$ incident edge-ends. The total number of edge-ends is $N\langle z\rangle=2L$, hence the fraction of edge-ends attached to degree-$z$ nodes is $zP(z)/\langle z\rangle$.
>
> This is the lecturer's Bayes-rule calculation in a direct counting form: high-degree vertices appear more often when reached along links.

> [!theorem] Giant-component condition (Molloy–Reed / branching approximation)
> For an uncorrelated, locally tree-like configuration-model random graph with nondegenerate degree distribution, an extensive connected component occurs when the mean excess degree exceeds $1$:
>
> $$\boxed{\kappa>1\quad\Longleftrightarrow\quad\frac{\langle z^2\rangle}{\langle z\rangle}>2\quad\Longleftrightarrow\quad\langle z(z-2)\rangle>0.}$$
>
> At the critical equality the system requires separate treatment; this strict inequality is the **supercritical** criterion used throughout the lecture.

> [!derivation]- Reason for the condition
> Explore a component outward. Each newly visited node generates on average $\kappa$ unexplored edges. When $\kappa>1$, the approximating branching process is supercritical and has a positive probability of unbounded growth; otherwise typical explorations die out. Negligible short cycles and degree correlations are crucial assumptions.

> [!example] ER graph before deletion
> For an ER graph of fixed mean degree $c$, the limiting degree distribution is Poisson, so
> $$\langle z^2\rangle=c^2+c,\qquad\kappa=\frac{c^2+c}{c}-1=c.$$
> The giant component appears at $c>1$, reproducing Week 3.

## 3. Uniform failure: derive $q_c$ carefully

### 3.1 Bond percolation — independently delete edges

An original degree-$z$ vertex retains each of its $z$ links with probability $p=1-q$. Thus its new degree $Z'$ satisfies

$$\boxed{Z'\mid Z=z\sim\operatorname{Binomial}(z,p).}$$

The post-failure degree distribution and the first two moments are

$$P'(z')=\sum_{z\ge z'}P(z)\binom z{z'}p^{z'}q^{z-z'},$$

$$\boxed{\langle Z'\rangle=p\langle Z\rangle,\qquad\langle (Z')^2\rangle=p^2\langle Z^2\rangle+pq\langle Z\rangle.}$$

> [!derivation]- Why the second moment has the extra term $pq\langle Z\rangle$
> The binomial identities give $\mathbb E[Z'\mid Z=z]=pz$ and $\operatorname{Var}(Z'\mid Z=z)=pqz$. Therefore
> $$\mathbb E[(Z')^2\mid Z=z]=\operatorname{Var}(Z'\mid Z=z)+(\mathbb E[Z'\mid Z=z])^2=pqz+p^2z^2.$$
> Average over the original $P(z)$.

The new mean excess degree is

$$\kappa'=\frac{\langle (Z')^2\rangle}{\langle Z'\rangle}-1
= p\left(\frac{\langle Z^2\rangle}{\langle Z\rangle}-1\right)=p\kappa.$$

The giant component survives iff $p\kappa>1$. Thus

> [!theorem] Critical random-failure fraction *(formula sheet)*
> If the original network is supercritical ($\kappa>1$), the random bond-failure threshold is
>
> $$\boxed{\begin{aligned}
> p_c&=\frac{1}{\kappa}=\frac{\langle z\rangle}{\langle z^2\rangle-\langle z\rangle},\\[2pt]
> q_c&=1-p_c=1-\frac{1}{\langle z^2\rangle/\langle z\rangle-1}.
> \end{aligned}}$$
>
> $p$ is the **surviving** fraction; $q$ is the **failed** fraction. The giant component survives for $q<q_c$ and disappears for $q>q_c$ in the infinite-size configuration-model setting. If $\kappa\le1$ initially, there is no ordinary supercritical giant component to destroy and the formal $q_c$ need not be a valid fraction.

### 3.2 Site percolation — independently delete nodes

Uniform node deletion removes a node **and all its edges**. The same branching argument applies: each reached neighbour survives with probability $p$, leaving an effective offspring mean $p\kappa$. Therefore

$$\boxed{p_c^{\mathrm{site}}=p_c^{\mathrm{bond}}=1/\kappa}$$

**for the configuration-model assumptions above**. The equality is about **critical probabilities**, not equality of $K_1(q)$ for finite graphs: surviving vertices are limited to at most a fraction $p$, while bond failure leaves isolated vertices in place.

> [!remark] Random probability versus exact removal fraction
> Under independent failure, the number removed fluctuates (binomial) around $qL_0$ or $qN_0$. Under a targeted attack removing $\lfloor qN_0\rfloor$ vertices, that count is fixed. The corresponding horizontal axes both represent $q$, but the experiments have different sampling rules.

## 4. Standard examples and their interpretation

| Original degree model | $\kappa=\langle z^2\rangle/\langle z\rangle-1$ | Critical $q_c$ |
|---|---:|---:|
| ER/Poisson, mean $c>1$ | $c$ | $1-1/c$ |
| $k$-regular, $k\ge3$ | $k-1$ | $1-1/(k-1)$ |
| Broad scale-free, $2<\gamma\le3$ | $\to\infty$ with $N$ | $\to1$ |

> [!example] Tutorial 10, Exercise 2.1(a): ER with $c=4$ or $6$
> $$c=4:\quad q_c=1-\frac14=\boxed{0.75},\qquad
> c=6:\quad q_c=1-\frac16=\boxed{0.8333\ldots}.$$
> Increasing $c$ increases robustness: more edges must fail before branching stops being supercritical.

> [!example] Bethe lattice and finite random regular networks (Exercise 1.3)
> A $k$-regular network has $\langle z^2\rangle=k^2$, so $q_c=1-1/(k-1)$. For $k=5$: $q_c=0.75$. A large random $5$-regular graph has local tree-like structure, so its simulations approach the same prediction with finite-size rounding.

> [!proposition] Why broad degrees matter
> A scale-free tail $P(z)\propto z^{-\gamma}$ with $2<\gamma\le3$ has a finite limiting mean but diverging second moment as the graph grows (logarithmically for the idealised $\gamma=3$ boundary). Therefore
> $$\boxed{\kappa\to\infty,\qquad p_c\to0,\qquad q_c\to1.}$$
> This is the lecture's **robustness to random failure** result. For any particular finite graph, $\langle z^2\rangle$ is finite and the crossover happens before all elements have failed. BA graphs ($\gamma=3$) can also have finite-size correlations, so the configuration-model calculation is their **asymptotic explanation**, not an exact finite-$N$ BA identity.

### 4.1 Compare ER and BA at fixed mean degree (Tutorial 10, Exercise 2.1)

![[Assets/w10-er-ba-random-failure.png|700]]

*Seeded simulations of random **edge** deletion with similar average degree; shaded regions are ±1 standard deviation. The dashed ER threshold is theoretical. These finite-size curves do not determine a unique exact BA threshold.*

> [!remark] How to explain each sub-question in Exercise 2.1
> - **(a) Analytical thresholds:** use $q_c=1-1/c$ for ER and $q_c\to1$ for idealised large scale-free networks.
> - **(b) Increase $N$, hold $c$ fixed:** the ER crossover becomes closer to the limiting threshold; BA's finite-size resilience reflects a growing degree range. A sharp threshold is an infinite-size statement.
> - **(c) Increase $c$, hold $N$ fixed:** additional connections increase resilience, so curves generally shift toward larger $q$.
> - **(d) Plot diameter as well as $K_1$:** diameter can rise before breakdown and fall after fragmentation.
> - **(e) Compare site and bond deletion:** the **critical $q_c$ agrees** in the locally tree-like theory; $K_1$ curves need not agree.

### 4.2 Diameter near breakdown

![[Assets/w10-diameter-example.png|700]]

*A representative ER graph under nested edge failures. $K_1$ is non-increasing, whereas the diameter of its largest component is not.*

Why? While a large component still exists, deleting shortcuts can increase the length of its longest shortest path. Later, the system fragments into small components, whose diameters are also small. A peak near the transition is a useful **finite-size indicator**, not a mathematical identity or an exact estimator of $q_c$.

> [!exam] Important monotonicity distinction
> Under **nested** deletions, $N_1(q)$ cannot increase with $q$ (deleting elements cannot enlarge any connected component). But the diameter **of the largest component** can increase, decrease or jump because paths change and the identity of the largest component may change.

## 5. Prescribed two-point degree distributions (Tutorial 10, Exercise 2.2)

Suppose half the nodes have degree $4$ and half have degree $k\ge2$:

$$P(z)=\frac12\delta_{z,4}+\frac12\delta_{z,k}.$$

> [!example] Derive the threshold
> The first two moments are
> $$\langle z\rangle=\frac{4+k}{2},\qquad\langle z^2\rangle=\frac{16+k^2}{2}.$$
> Substitution gives
> $$\boxed{q_c(k)=1-\frac{k+4}{k^2-k+12}.}$$
>
> | $k$ | $q_c(k)$ (approx.) |
> |---:|---:|
> | 2 | 0.5714 |
> | 4 | 0.6667 |
> | 6 | 0.7619 |
> | 8 | 0.8235 |
> | 16 | 0.9206 |
>
> Here the model becomes more robust with $k$, but **both the average degree and degree heterogeneity change** as $k$ increases; do not attribute the entire change to variance alone.

![[Assets/w10-two-point-threshold.png|700]]

> [!algorithm] Exercise 2.2 simulation
> 1. Choose even $N$ and an admissible $k$; construct a **simple** graph with exactly $N/2$ nodes of degree $4$ and $N/2$ of degree $k$.
> 2. Check the realised degree sequence. Graphicality and an appropriate sampler matter: random stub pairing can create self-loops/multi-edges.
> 3. For each $q$, independently fail edges; compute $K_1=N_1/N$. Repeat graph realisations.
> 4. At fixed $N=500$, compare $k=2,4,8,16$ and the theoretical vertical lines $q_c(k)$.
> 5. At fixed $k=6$, increase $N$; the observed crossover should become more consistent with the predicted $q_c(6)\approx0.7619$.
>
> These numerical comparisons are checks of the **large-network, locally tree-like approximation**; they are not guaranteed to match exactly at finite $N$.

> [!exam] Related trial-exam example: uniform degrees $1,\ldots,z^*$ (Trial 2, Q7)
> This is **not** the two-point distribution above. For $P(z)=1/z^*$ on $\{1,\ldots,z^*\}$:
> $$\langle z\rangle=\frac{z^*+1}{2},\qquad
> \frac{\langle z^2\rangle}{\langle z\rangle}=\frac{2z^*+1}{3},$$
> $$\boxed{q_c=1-\frac{3}{2(z^*-1)}}.$$
> A giant component is supercritical when $z^*\ge3$ (for $z^*=2$, the mean excess degree is below $1$). Increasing $z^*$ makes random failure less destructive.

## 6. Targeted attacks: why the conclusions reverse

> [!definition] Static versus adaptive degree attack
> - **Static high-degree attack** (Tutorial 10 §3): rank all vertices by their **original** degrees (break ties randomly), then remove the first $\lfloor qN_0\rfloor$. Do **not** recompute the ranking.
> - **Adaptive degree attack** (not the tutorial experiment): recompute current degrees after each removal and repeatedly attack the current largest-degree vertex.
>
> Both differ from uniform node failure, which chooses vertices without regard to degree.

> [!remark] Why $q_c$ from uniform deletion cannot be reused directly
> The formula $q_c=1-1/\kappa$ assumes the same survival probability for every degree. A targeted attack chooses nodes **because of their degree**. Removing one hub removes **all its incident edges**, so the degrees and paths of many surviving vertices change simultaneously. Substituting the original $\langle z^2\rangle$ into the uniform-deletion formula does not model this process.

> [!proposition] Degree-dependent survival criterion (extension of lecture argument)
> Suppose a degree-$z$ vertex is retained with probability $\phi_z$, independently conditional on original degrees. For an uncorrelated configuration-model network, the effective branching factor is
> $$\boxed{\mathcal R=\frac{\sum_z z(z-1)P(z)\phi_z}{\langle z\rangle}.}$$
> A giant component survives when $\mathcal R>1$.
> - Uniform site survival: $\phi_z=p$ for all $z$, giving $\mathcal R=p\kappa$.
> - Degree-targeted survival: $\phi_z$ is small (or zero) for high degrees, removing the terms proportional to $z(z-1)$ first.
>
> This is a degree-based **approximation for static attacks**, not a universal formula for finite adaptive attacks.

![[Assets/w10-targeted-attack.png|700]]

*Independent seeded simulations compare random vertex failure (solid) with **static highest-degree removal** (dashed). BA is relatively resilient to random failure but loses connectedness quickly under targeted attacks. Exact finite-$N$ critical fractions depend on the network and protocol.*

> [!theorem] Robust yet fragile (main Week 10 conclusion)
> **Scale-free networks** with $2<\gamma\le3$ are:
> 1. **Robust to uniform random failure:** hubs are seldom removed, so $\langle z^2\rangle$ remains large and $q_c\to1$ in the idealised large-network limit.
> 2. **Vulnerable to targeted hub attacks:** deliberately removing hubs eliminates disproportionate numbers of paths, and connectivity can collapse after a comparatively small removed fraction.
>
> By contrast, the narrower degrees of ER graphs make random and degree-targeted removal less dramatically different. The lecture illustrates the contrast with internet/WWW attack studies (pp. 141–143); their specific attack thresholds are **empirical**, not values predicted by the uniform-deletion $q_c$ formula.

![[Assets/w10-lecture-error-attack.png|650]]

*Original 2026 lecture illustration (p. 141), adapted from Albert, Jeong & Barabási (2000). The plotted vertical measurements are **path-length/distance measures**, not $K_1$; attacks cause it to increase sharply, whereas random failures have a smaller initial effect. The figure supports the mechanism but does **not** give a universal $q_c$ for all networks.*

## 7. Algorithms: what Tutorial 10 actually does

### 7.1 Independent, nested edge failures

> [!algorithm] Generate $K_1(q)$ versus $q$ correctly
> 1. Generate one ER, BA or prescribed-degree graph $G_0$; set $N_0=|V(G_0)|$.
> 2. Give every *original edge* a single independent mark $u_e\sim U(0,1)$.
> 3. For each $q$, retain precisely those edges with $u_e\ge q$; keep **all original vertices**.
> 4. Find the connected components, measure $K_1$ and the largest-component diameter.
> 5. Repeat using independent graph realisations and new marks. Plot the sample mean with standard-deviation bands.
>
> **Why reuse marks across $q$?** It creates **nested deletions**: once removed, an edge never reappears when $q$ increases. Independent new marks for every $q$ do not give a monotone path in one realisation, making the curve harder to interpret.

> [!code]- Minimal correct NetworkX implementation
> ```python
> import numpy as np
> import networkx as nx
>
> rng = np.random.default_rng(13)
> G0 = nx.erdos_renyi_graph(500, 4 / 499, seed=13)
> edges = list(G0.edges())
> marks = rng.random(len(edges))   # once per original edge
> K1, diameter = [], []
>
> for q in np.linspace(0, 1, 51):
>     H = nx.Graph()
>     H.add_nodes_from(G0)        # bond failure: keep original nodes
>     H.add_edges_from(e for e, u in zip(edges, marks) if u >= q)
>     comp = max(nx.connected_components(H), key=len)
>     K1.append(len(comp) / len(G0))
>     diameter.append(nx.diameter(H.subgraph(comp), usebounds=True))
> ```
> For larger graphs, a union-find/connected-component routine can be used to avoid repeated all-pairs distance calculations. Diameter is computationally much more expensive than $K_1$.

### 7.2 Uniform node failures and targeted node removal

> [!algorithm] Distinguish the two experiments
> **Uniform node failure:** generate one $u_v\sim U(0,1)$ for each original vertex and retain $u_v\ge q$. The induced graph on retained vertices loses all edges incident to removed vertices. Repeat for new random draws.
>
> **Static targeted attack:** sort vertices once by decreasing **original degree**, randomise ties, remove the first $\lfloor qN_0\rfloor$, and take the induced subgraph on the remainder. Again compute $K_1$ with the **original denominator**.

> [!code]- Static hub attack (Tutorial 10, Exercise 3.1)
> ```python
> rng = np.random.default_rng(13)
> tie = {v: rng.random() for v in G0}
> order = sorted(G0, key=lambda v: (G0.degree(v), tie[v]),
>                reverse=True)
> N0 = len(G0)
> for q in np.linspace(0, 1, 51):
>     removed_count = int(np.floor(q * N0))
>     H = G0.subgraph(order[removed_count:])
>     n1 = max((len(c) for c in nx.connected_components(H)), default=0)
>     K1 = n1 / N0
> ```
> The calculation above uses **static**, not adaptive, ranks.

> [!exam] Tutorial 10, Exercise 3.1 — interpreting the plots
> - At the **same average degree**, BA networks tend to break under smaller targeted-attack fractions than ER networks, although BA is more resilient under uniform failure.
> - Increasing average degree (e.g. from about $4$ to about $10$) generally improves robustness under both schemes.
> - A peak in diameter is a useful finite-size indicator that the once-large component is becoming stretched before it fragments; it does **not** define a rigorous threshold.
> - Use the **same original $N_0$** on every $K_1$ plot and explicitly state whether the experiment removes **edges or vertices**.

## 8. Complete Week 10 exam checklist

| You should be able to… | Key result or explanation |
|---|---|
| Interpret $K_1(q)$ and diameter | Connectivity size versus longest path *within* the largest component |
| Identify a giant component | $N_1=\Theta(N)$; mean excess degree $\kappa>1$ |
| Explain degree bias | $P_{\mathrm{edge}}(z)=zP(z)/\langle z\rangle$ |
| Derive uniform-failure threshold | $p\kappa>1$, $q_c=1-1/\kappa$ |
| Compute ER and $k$-regular thresholds | $q_c^{\rm ER}=1-1/c$; $q_c^{\rm regular}=1-1/(k-1)$ |
| Explain scale-free robustness | Divergent $\langle z^2\rangle$ pushes $q_c\to1$ |
| Analyse the two-point $P(z)$ | $q_c(k)=1-(k+4)/(k^2-k+12)$ |
| Distinguish random failure from attack | Independent uniform marks versus degree-ordered node deletion |
| Explain shape of simulation curves | Finite-size rounding, nested monotonic $K_1$, non-monotonic diameter |
| Explain failure-versus-attack reversal | Hubs support connectivity but are deliberately removed in attacks |

> [!selftest]- Five questions to check your understanding
> 1. Why is the average number of *new* links $\langle z^2\rangle/\langle z\rangle-1$, not $\langle z\rangle$? — Degree bias and the already-used arrival link.
> 2. For ER with $c=6$, find $q_c$. — $5/6$.
> 3. Does node deletion have the same $K_1(q)$ as edge deletion? — Not necessarily; the large-$N$ **critical probability** agrees under the model assumptions.
> 4. For $P(4)=P(8)=1/2$, compute $q_c$. — $1-12/68=14/17\approx0.8235$.
> 5. Why should $q_c=1-1/\kappa$ **not** be inserted unchanged into the targeted-attack problem? — Hubs are not removed uniformly and their incident links disappear together.
> 6. Does diameter have to decrease as $q$ increases? — No. Loss of shortcuts can increase it before fragmentation reduces it.

---
**Related:** [[Percolation on lattices]] · [[Configuration model]] · [[Power laws]] · [[Preferential attachment]] · [[SIR model and epidemic threshold]] · [[Threshold model and cascades]]
