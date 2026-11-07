---
tags: [data5441, exam]
aliases: [Trial exams, Past exam patterns]
---
# Exam patterns (from Trial Exams 1 and 2, 2026)

> [!abstract] Structure
> **Part A, short answer (50%):** numerical values read or computed from a figure or a description, comparisons (larger / smaller / equal), and "list the applicable letters" items.
> **Part B, extended answer (50%):** derivations and explanations on ER/BA, ERGM + Metropolis, SBM, percolation, community detection, and interpreting Python code.

## 1. Elementary properties from a drawn graph
> [!exam] Method
> Count $N$ and $L$ (check that $\sum z_i=2L$). Then $\langle z\rangle=2L/N$, the diameter $D$, $C_i=2T_i/[z_i(z_i-1)]$ and $\langle C\rangle$. Betweenness: count the shortest paths through the node, then normalise by $\binom{N-1}2$.
> Example: node 5 is a bridge between groups of $4$ and $5$ nodes, so $b_5=20$ and $\tilde b_5=20/36=5/9$.
> → [[Graphs and representations]], [[Clustering]], [[Centrality]]

## 2. Fitting ER and comparing models
> [!exam] Method
> - $p=2L/[N(N-1)]$, $\langle z\rangle_{ER}=2L/N$ (equal to the data), $C_{ER}\approx p$.
> - $p=c/N$ is sparse, with $\langle z\rangle\to c$.
> - BA with matching $\langle z\rangle$: $m=\langle z\rangle/2$. BA has the larger $\sigma_z/\langle z\rangle$.
> - Neither ER nor BA has high clustering.
> - Which model fits which data: broad degrees → configuration model; groups (school years) → SBM. Most friends → degree centrality; bridges → betweenness.
>
> → [[Erdos-Renyi graphs]], [[Preferential attachment]], [[Configuration model]]

> [!warning] Inconsistency in the Trial 1 solutions
> Trial 1, Q4(i)–(j) ask whether the clustering $C$ and the variability $\sigma_z/\langle z\rangle$ of the fitted ER graph $G_P$ are larger or smaller than those of the real friendship network $G$. The key answers "Larger" for both. Standard course reasoning gives **smaller** for both:
> - ER clustering $\approx p$ is low compared with real social networks;
> - Poisson degrees are less variable than real degree distributions.
>
> Ask the lecturer which is intended, and in the exam justify your answer in one line.

## 3. Graph spaces, ERGMs, Metropolis
> [!exam] Method
> - $Y=N(N-1)/2$, $|\Omega_N|=2^Y$, $|\Omega_{N,L}|=\binom YL$.
> - At $\beta=0$ the distribution is uniform; $\beta>0$ favours large values of the statistic.
> - Symmetric edge-replacement proposal: probability $1/[L(Y-L+1)]$ for both directions.
> - Metropolis acceptance: $\min\{1,p(g')/p(g)\}$, e.g. $e^{\beta\Delta T}$, $(L'/L)^2$, $e^{\beta\Delta L}$.
> - Compare expected $L$ across models; give $p(\text{empty graph})$ for each.
>
> → [[Random graph ensembles]], [[Metropolis–Hastings]], [[Maximum entropy and ERGMs]]

## 4. MCMC traces
> [!exam] Method
> - The value at $t=0$ is the observed $g^*$; the plateau is the null-model value.
> - As $t\to\infty$, a finite ergodic chain hits every state with probability $1$. So any value attainable in the space is observed eventually (probability $1$), and impossible values have probability $0$.
>
> → [[Markov chain Monte Carlo on graphs]]

## 5. SBM fitting
> [!exam] Method
> $\hat p_{rs}=l_{rs}/y_{rs}$, where:
> - undirected: $y_{rr}=\binom{n_r}2$;
> - directed: $y_{rr}=n_r(n_r-1)$;
> - $y_{rs}=n_rn_s$.
>
> Joint link events are products of probabilities, by independence. Real networks show **more** repeated collaboration and reciprocity than the SBM predicts. Classify the structure as assortative, disassortative (e.g. bipartite) or core–periphery.
> → [[Stochastic block models]]

## 6. Degree distributions, the giant component, robustness
> [!exam] Method
> - Normalise $P(z)$, then compute $\langle z\rangle$ and $\langle z^2\rangle$.
> - Sparse if $\langle z\rangle$ does not grow with $N$.
> - Giant component iff $\langle z^2\rangle/\langle z\rangle>2$.
> - $q_c$ from the formula sheet; a larger $\langle z^2\rangle/\langle z\rangle$ means more robust to random failure.
> - Sketch $\theta$ against the parameter, marking the critical value.
>
> → [[Configuration model]], [[Percolation and robustness]]

## 7. Community detection and modularity
> [!exam] Method
> - Read the best $B$ and $Q$ off the plots.
> - Agglomerative is bottom-up merging; divisive is top-down splitting.
> - Greedy methods are path-dependent, so the best $Q$ found is not proof of the global optimum.
> - Louvain on ER finds many groups with positive $Q$ by exploiting random fluctuations; a single group has $Q=0$.
>
> → [[Community detection]]

## 8. Classify methods (letters)
> [!exam] Known answers
> - **Community detection:** spectral (Laplacian) methods, SBM, greedy modularity.
> - **Link prediction / reconstruction:** spectral methods, Jaccard and common neighbours, SBM.
> - **Dynamics on networks:** threshold model, SIR.
> - **Generative random-graph models:** configuration model (also ER, BA, WS, SBM).

## 9. Reading Python
> [!exam] Method
> State, for each line:
> - what is generated (e.g. `erdos_renyi_graph(N, p, seed)` is $G(N,p)$ with $\langle z\rangle=p(N-1)$);
> - the role of each seed (graph realisation vs algorithm randomness);
> - what the variables store (`louvain_communities` returns a list of node sets, i.e. a partition);
> - what each printed quantity means.

## 10. Week 12 (not in the trial papers, expect derivations)
> [!exam] Prepare
> - The SIR ODEs at orders 0 and 1.
> - $r_\infty=1-e^{-\lambda\langle z\rangle r_\infty/\mu}$ and the slope condition.
> - The threshold $\lambda/\mu>\langle z\rangle/\langle z^2\rangle$.
> - The percolation analogy $p\approx\lambda/\mu$, and why scale-free networks have no threshold.
> - Prisoner's dilemma: Nash equilibrium vs collective optimum.
> - Network imitation dynamics and the two-hub argument.
>
> → [[SIR model and epidemic threshold]], [[Evolutionary games on networks]]

---
Up: [[00 Home]] · Related: [[Formula sheet]]
