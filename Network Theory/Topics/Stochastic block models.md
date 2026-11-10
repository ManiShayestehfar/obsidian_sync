---
tags: [data5441, ch07, inference]
aliases: [SBM, Block model, Assortative, Disassortative, Core-periphery]
---
---

# Stochastic block models

> [!abstract] Core idea
> A **stochastic block model (SBM)** describes *meso-scale structure*: nodes belong to groups (blocks), and the probability of a link depends **only on the two blocks**. Given the groups, fitting link probabilities is easy: **observed links / possible links**. The difficult part is **inferring the groups** from the network.
>
> $$\boxed{\Pr(A_{ij}=1\mid\mathbf b,P)=p_{b_i b_j}},\qquad\boxed{\hat p_{rs}=\frac{l_{rs}}{y_{rs}}}. $$
>
> Course: **DATA5441 Week 7**, lecture notes pp. 85–100 and Tutorial 7 (Karate Club). Chapter: [[Ch07 SBMs and statistical inference]].

## 1. Motivation: structure between the local and global scales

Degree and clustering describe *local* properties; total links and mean distance describe *global* properties. But many networks also have **meso-scale** patterns: groups of nodes with similar connection behaviour. SBM is a **generative random-graph model** for such patterns, and statistical inference attempts to recover them from one observed graph.

> [!definition] Stochastic block model *(formula sheet)*
> Partition $N$ nodes into $B$ non-empty, disjoint blocks. Write $b_i\in\{1,\ldots,B\}$ for the block of node $i$. Conditional on the assignments $\mathbf b=(b_1,\ldots,b_N)$, every allowed pair of nodes is linked independently with probability
> $$\boxed{\Pr(A_{ij}=1\mid b_i=r,b_j=s)=p_{rs}}.$$
> The **connectivity matrix** is $P=(p_{rs})_{r,s=1}^B$, with $0\le p_{rs}\le1$. For undirected networks, $P$ is symmetric; for directed networks, it need not be.
>
> **Special case:** $B=1$ gives the Erdős–Rényi graph $G(N,p_{11})$.

> [!important] What “independent” means
> **Edges are independent conditional on $\mathbf b$ and $P$.** They need not have the *same* probability. For example, if two authors have previously collaborated, a basic SBM does not automatically raise the probability of a second collaboration: it remembers their blocks, not their shared history.

### Common meso-scale patterns

![[Assets/sbm-block-patterns.png|800]]


| Pattern | Recognise it from $P$ | Interpretation |
|---|---|---|
| **Assortative (communities)** | Diagonal typically larger: $p_{rr}>p_{rs}$ | Many links **within** groups |
| **Disassortative** | Off-diagonal typically larger | Many links **between** groups; bipartite is an extreme case |
| **Core–periphery** | E.g. $p_{cc}>p_{cp}>p_{pp}$ | Dense core, weakly connected periphery |

## 2. Counting possible links

Let $n_r=|\{i:b_i=r\}|$ and let $l_{rs}$ be the **number of observed links** between blocks $r$ and $s$ (count each undirected edge once). Let $y_{rs}$ be the **number of possible links** of that type.

| Network | Within block ($r=s$) | Between blocks ($r\ne s$) |
|---|---|---|
| **Undirected, no loops** | $\displaystyle y_{rr}=\binom{n_r}{2}$ | $\displaystyle y_{rs}=n_rn_s$ |
| **Directed, no loops** | $\displaystyle y_{rr}=n_r(n_r-1)$ | $\displaystyle y_{rs}=n_rn_s$ |

> [!tip] Avoid the factor-of-two trap
> Undirected **within-block** links use $\binom{n_r}{2}$, not $n_r(n_r-1)$, because $i-j$ and $j-i$ are the same link. In a directed graph, they are different possible links.

![[Assets/sbm-fitting-counts.png|750]]

*Worked illustration: reorder an adjacency matrix by blocks, count the edges in its three distinct regions, then divide by the number of possible edges in each region.*

## 3. Likelihood and fitting $P$ (known partition)

For an undirected simple graph $g$ with adjacency matrix $A$, the full **conditional likelihood** is
$$\mathcal L(\mathbf b,P)=\Pr(A\mid\mathbf b,P)=\prod_{i<j}p_{b_ib_j}^{A_{ij}}(1-p_{b_ib_j})^{1-A_{ij}}.$$

Grouping pairs by their blocks gives
$$\boxed{\log\mathcal L(\mathbf b,P)=\sum_{r\le s}\big[l_{rs}\log p_{rs}+(y_{rs}-l_{rs})\log(1-p_{rs})\big].}$$

> [!theorem] Maximum-likelihood estimate (MLE) for fixed $\mathbf b$
> Maximising over each $p_{rs}$ separately yields
> $$\boxed{\hat p_{rs}=\frac{l_{rs}}{y_{rs}}}\qquad (y_{rs}>0).$$
> In words: **probability of a link = observed links / possible links**. The result also holds for directed graphs when the directed counts are used.

> [!proof]- Why $\hat p=l/y$? (short derivation)
> For one block pair, maximise $f(p)=l\log p+(y-l)\log(1-p)$. If $0<l<y$,
> $$f'(p)=\frac lp-\frac{y-l}{1-p}=0\quad\Longrightarrow\quad p=\frac ly,$$
> and $f''(p)=-l/p^2-(y-l)/(1-p)^2<0$. If $l=0$ or $l=y$, the maximum is attained at **$p=0$** or **$p=1$** respectively. If $y=0$, the parameter is unidentifiable and its term is omitted. Use $0\log0:=0$ in the fitted log-likelihood. $\square$

**Why inference is still hard:** these formulas assume $\mathbf b$ is already known. When the blocks are unknown, *every candidate partition changes the counts $l_{rs}$ and $y_{rs}$*, and hence changes the best-fit matrix $\hat P$.

## 4. Exam: compute SBM probabilities

> [!exam]- Three standard patterns from the 2026 trial exams
> **A. Bipartite authorship (Trial 2, Q6).** There are 200 articles, 40 authors and on average 3 authors per article. Hence $L=200\times3=600$.
>
> - Only author–article links exist: $p_{11}=p_{22}=0$.
> - $\displaystyle \hat p_{12}=\hat p_{21}=\frac{600}{200\times40}=\boxed{\frac3{40}}$.
> - This is **disassortative**. Under the fitted SBM, two specified authors independently being linked to another specified article has probability $\boxed{(3/40)^2=9/1600}$.
> - Real repeated co-authorships can be more frequent because collaborations are **correlated**, unlike SBM links conditional on blocks.
>
> **B. Directed school friendships (Trial 2, Q5).** Three classes of 30 students each; each student names friends by target class.
>
> - Five named friends within class $a$ per student: $\displaystyle \hat p_{aa}=\frac{30\times5}{30\times29}=\boxed{\frac5{29}}$.
> - One named friend from $b$ to $c$ per student: $\displaystyle \hat p_{bc}=\frac{30\times1}{30\times30}=\boxed{\frac1{30}}$.
> - Similarly $\hat p_{cb}=1/30$. The **expected number of reciprocal $b$–$c$ pairs** is
>   $$\boxed{30\times30\times p_{bc}p_{cb}=1}.$$
>   Here the two directions are independent Bernoulli links; observed friendship networks often exhibit greater reciprocity.
>
> **C. Five planted groups (Trial 1, Q1b).** There are $N=45$ nodes, five groups of nine, every degree is eight, and every pair of groups has two links.
>
> - Total links $L=45\times8/2=180$; between-group links $=\binom52\times2=20$.
> - Thus 160 within-group links, or 32 per group: $\displaystyle\boxed{\hat p_{rr}=\frac{32}{\binom92}=\frac89}$.
> - For $r\ne s$: $\displaystyle\boxed{\hat p_{rs}=\frac2{9\times9}=\frac2{81}}$.
>
> **Strategy:** determine whether the graph is directed → count the relevant links → count the possible links → divide.

## 5. Inferring the unknown partition

For each candidate assignment $\mathbf b$, substitute its optimal $\hat P(\mathbf b)$ into the likelihood. This produces the **profile cost**

$$\boxed{F(\mathbf b)=-\log\mathcal L\big(\mathbf b,\hat P(\mathbf b)\big).}$$

For a fixed number of blocks $B$, **minimise $F$ over valid partitions** (equivalently maximise the likelihood). Lower $F$ means a better fit. Relabelling the blocks, such as swapping labels 1 and 2, changes neither the model nor its likelihood.

> [!remark] Why exhaustive search is difficult
> There are $B!\,S(N,B)$ assignments to **$B$ labelled, non-empty** blocks, where $S(N,B)$ is a Stirling number of the second kind. Up to relabelling, there are $S(N,B)$ distinct partitions. For $B=2$, this equals $2^{N-1}-1$—already enormous for a modest network. This motivates approximate algorithms.

### Greedy search versus Metropolis MCMC

![[Assets/sbm-greedy-vs-metropolis.png|750]]

> [!algorithm] Greedy partition search (Tutorial 7, Exercises 3–4)
> 1. Start with an assignment $\mathbf b$ (e.g. randomly chosen).
> 2. For each node, consider changing its block (without making a block empty); recompute $F$.
> 3. Make the **single best strict improvement**. Repeat until none exists.
>
> The algorithm stops at a **local minimum**, which need not be the global minimum. Different initial partitions can produce different answers; use multiple starting points.

> [!algorithm] Metropolis search / sampling (Tutorial 7, Exercise 5)
> 4. Start from a valid partition $\mathbf b$; propose a single-node block change $\mathbf b\to\mathbf b'$.
> 5. Calculate $\Delta F=F(\mathbf b')-F(\mathbf b)$.
> 6. For a **symmetric proposal**, accept with
>    $$\boxed{A(\mathbf b\to\mathbf b')=\min\{1,e^{-\beta\Delta F}\}.}$$
> 7. If rejected, **remain at $\mathbf b$**. Repeat, retaining rejected states in the trajectory.
>
> **Interpretation:**
> - $\Delta F\le0$: accept (same or better fit).
> - $\Delta F>0$: occasionally accept a worse fit; this can cross an objective barrier and escape a greedy local minimum.
> - $\beta=0$: random exploration (all valid proposed moves accepted); $\beta=1$: sample with weight $\propto e^{-F(\mathbf b)}$; large $\beta$: increasingly favour minima.
>
> This is precisely the **Metropolis–Hastings** principle from [[Metropolis–Hastings]], now applied to **partitions rather than graphs**.

> [!proof]- Why is the Metropolis formula valid here?
> Define the target for fixed $B$ as $\pi_\beta(\mathbf b)=e^{-\beta F(\mathbf b)}/Z_\beta$. For a symmetric proposal $q(\mathbf b\to\mathbf b')=q(\mathbf b'\to\mathbf b)$, MH gives
> $$A=\min\!\left\{1,\frac{\pi_\beta(\mathbf b')}{\pi_\beta(\mathbf b)}\right\}=\min\{1,e^{-\beta[F(\mathbf b')-F(\mathbf b)]}\}.$$
> The normalising constant $Z_\beta$ cancels. For $B=2$, uniformly choosing a node and *flipping* its label is symmetric; to enforce non-empty blocks, treat an invalid flip as a **self-proposal**. For an asymmetric proposal the usual Hastings proposal ratio must also appear. $\square$

> [!warning] Sampling is not the same as optimisation
> At $\beta=1$, the chain targets **profile-likelihood weights** $e^{-F(\mathbf b)}$, not automatically a fully Bayesian posterior (which would also specify priors and account for uncertainty in $P$). At very large $\beta$, the method seeks low-cost partitions, but a finite run is **not guaranteed** to find the global optimum. **Simulated annealing** gradually increases $\beta$; chains still require time to explore the partition space.

### Choosing the number of blocks $B$

Increasing $B$ makes the model more flexible: at $B=N$, each node forms its own block and the model can perfectly fit every observed edge or non-edge. Therefore **maximum likelihood alone cannot reliably select $B$**.

> [!remark]- Complexity correction and Bayesian model comparison (lecture and Tutorial 7, Exercises 6–7)
> The lecture introduces priors and posterior model probabilities to penalise over-flexible descriptions. With a uniform prior over **labelled, non-empty** assignments,
> $$\Pr(\mathbf b\mid B)=\frac1{B!S(N,B)}.$$
> A simple *best-partition proxy* uses $\mathcal L(\mathbf b,\hat P(\mathbf b))\Pr(\mathbf b\mid B)$ to compare solutions at different $B$ (and a prior on $B$ if needed).
>
> **Important distinction:** this plug-in, best-partition comparison is **not the exact Bayesian evidence**. Exact evidence sums over partitions and integrates over unknown parameters $P$ under a specified prior. The course uses simplified comparisons to illustrate the fit–complexity trade-off.

## 6. Degree correction: a limitation of the ordinary SBM

The basic SBM assigns every node in block $r$ the same expected connection pattern. If the observed graph has a few **hubs**, a likelihood-based partition can group nodes according to degree rather than the social groups of interest (as the Karate Club tutorial illustrates).

> [!definition] Degree-corrected SBM (idea)
> Introduce a node-level propensity $\theta_i$ so the expected interaction strength has the schematic form
> $$\mathbb E[A_{ij}\mid\mathbf b,\boldsymbol\theta]\propto \theta_i\theta_j\,\omega_{b_i b_j}.$$
> The $\theta_i$ factors accommodate varying degrees **within** a block, while $\omega_{rs}$ describes **between-block** structure. (This is commonly formulated with Poisson edge counts; the displayed relation is not automatically a valid Bernoulli probability without additional modelling choices.)

## 7. Tutorial code and exam essentials

> [!code]- Generate a known two-block SBM (Tutorial 7)
> ```python
> import networkx as nx
>
> G = nx.stochastic_block_model(
>     [20, 50], [[0.15, 0.01], [0.01, 0.20]], seed=13
> )
> # For an observed graph and a fixed partition:
> #    p_hat[r, s] = observed_links[r, s] / possible_links[r, s]
> # Tutorial 7 then optimises or samples the partition itself.
> ```

> [!exam] Remember
> - **Model:** $\Pr(A_{ij}=1\mid\mathbf b,P)=p_{b_i b_j}$; $B=1$ is ER.
> - **Fit for known blocks:** $\hat p_{rs}=l_{rs}/y_{rs}$, with correct directed/undirected denominators.
> - **Unknown blocks:** minimise the **profile negative log-likelihood** $F(\mathbf b)$.
> - **Greedy:** improves the cost but can get trapped in a local minimum.
> - **Metropolis:** $A=\min\{1,e^{-\beta\Delta F}\}$ for **symmetric** proposals; worse moves may be accepted.
> - **Choose $B$ carefully:** more blocks improve flexibility but risk overfitting.
> - **Degree correction:** separates node degree heterogeneity from block structure.

> [!selftest]- Quick self-test
> 1. With two undirected blocks of sizes 8 and 10 and 12 between-block edges, what is $\hat p_{12}$? — **$12/80=0.15$**.
> 2. If $\Delta F=2$ and $\beta=1$, what is the Metropolis acceptance probability? — **$e^{-2}\approx0.135$**.
> 3. Why do we include rejected moves in MCMC? — They contribute to the **stationary state frequencies**.
> 4. Why can greedy and Metropolis find different partitions? — Metropolis can cross a **temporary likelihood barrier**.
> 5. Why is an SBM with many blocks not automatically best? — **Overfitting:** likelihood alone ignores model complexity.

---
Related: [[Statistical inference and model selection]] · [[Community detection]] · [[Link prediction]] · [[Erdos-Renyi graphs]] · [[Metropolis–Hastings]]
