---
tags: [data5441, ch09, inference]
aliases: [Ising reconstruction, Pseudolikelihood, Correlation network]
---
# Reconstruction from node activity

> [!abstract] Summary
> This is the **second** Week 9 task: the links are **not observed**; instead, we see repeated **binary states on the nodes**. A **heuristic** reconstructs edges from pairwise Pearson correlations. An **inferential** method assumes an Ising interaction model and searches for graphs that explain the observed states, using **pseudolikelihood** and **Metropolis sampling**. Unlike [[Link prediction]], no partial adjacency matrix is supplied.
> Chapter: [[Ch09 Network reconstruction]] · Sources: DATA5441 **Week 9**, lecture pp. 123–126; Tutorial 9, §2.

## 1. Observations and target

> [!definition] Node-activity data
> For $N$ nodes and $T$ observed configurations, write
> $$F=(s_i^{(t)})\in\{-1,+1\}^{T\times N},$$
> where row $t$ records all node states at observation $t$. The unknown object is a simple undirected graph $g$, encoded by $A_{ij}\in\{0,1\}$.
>
> **Tutorial 9 benchmark:** $N=50$, $T=200$, hidden $L=100$ edges, with states generated on a Watts–Strogatz graph (rewiring $0.2$, degree $4$) using interaction strength $J=0.4$. The number of edges $L$ is **given as extra information** in this synthetic exercise; it is not learned from $F$.

**Central difficulty:** If nodes $i,j$ tend to take the same state, are they directly linked, or are they both influenced by some *third* node? Correlation detects association, not necessarily a direct interaction.

![[Assets/w9-node-activity.png|720]]

## 2. Heuristic reconstruction: correlate the observed states

> [!definition] Pearson similarity
> For each distinct pair $i,j$, compute the correlation across the $T$ observations:
> $$\boxed{r_{ij}=\frac{\sum_{t=1}^T(s_i^{(t)}-\bar s_i)(s_j^{(t)}-\bar s_j)}{\sqrt{\sum_t(s_i^{(t)}-\bar s_i)^2}\sqrt{\sum_t(s_j^{(t)}-\bar s_j)^2}}.}$$
> Here $\bar s_i=T^{-1}\sum_t s_i^{(t)}$. For the tutorial's **positive-coupling** Ising generator, large positive correlation is evidence for a candidate edge. Correlation is undefined for an unchanging column; the tutorial sets such scores to $0$ as a **convention**.

> [!algorithm] Correlation-based network reconstruction
> 1. Calculate $r_{ij}$ for every unordered pair $i<j$ from the **state observations only**.
> 2. Rank all $Y=\binom N2$ pairs from **highest** to lowest $r_{ij}$.
> 3. Predict precisely the top **$L$** pairs as links; this uses the supplied edge count.
> 4. In the *synthetic benchmark only*, count how many predicted links occur in the hidden true graph.
>
> **Why it can fail:** indirect paths also create correlated states, and finite $T$ makes correlations noisy. Increasing $T$ typically stabilises estimates, but no pairwise-correlation rule can automatically distinguish indirect from direct influence.

> [!proposition] Random baseline for the number of correct links
> If a hidden graph has exactly $L$ edges out of $Y=\binom N2$ possible pairs and we choose $L$ predictions **uniformly without replacement**, then
> $$\boxed{\mathbb E[\text{correct predicted links}]=L\frac LY=\frac{L^2}{Y}.}$$
> Indeed, each of the $L$ true edges has probability $L/Y$ of selection (linearity of expectation). For $N=50$, $L=100$:
> $$Y=1225,\qquad \mathbb E[\text{correct}]=\frac{10{,}000}{1225}\approx\boxed{8.16}. $$
> The tutorial's Pearson procedure identifies **44 out of 100** edges from the 200 observations. This is a benchmark outcome, not a general guarantee.

## 3. Inferential reconstruction: assume a mechanism

> [!definition] Ising model on a candidate graph
> Model each configuration $s=(s_1,\ldots,s_N)$ as having energy
> $$E_g(s)=-J\sum_{\{i,j\}\in E(g)}s_is_j,\qquad J>0.$$
> Aligned states on a link ($s_is_j=+1$) lower energy, hence are favoured. The probability of seeing $s$ given graph $g$ is
> $$\boxed{P(s\mid g,J)=\frac{e^{-E_g(s)}}{Z(g,J)},\quad Z(g,J)=\sum_{s\in\{\pm1\}^N}e^{-E_g(s)}.}$$
> **Inference reverses the direction:** we observe configurations and ask which $g$ makes them plausible. A candidate graph's total energy **alone is not its likelihood**, because the partition function $Z(g,J)$ also changes with $g$ and contains $2^N$ configurations.

> [!theorem] Single-node conditional probability
> Write the **local field** at node $i$ as $h_i(s_{-i})=J\sum_jA_{ij}s_j$. Holding all other states fixed,
> $$\boxed{P(s_i\mid s_{-i},g,J)=\frac{e^{s_ih_i}}{e^{h_i}+e^{-h_i}}=\frac1{1+e^{-2s_ih_i}}.}$$
> **Interpretation:** if node $i$ agrees with a strong positive field from its neighbours, its conditional probability is high. Crucially, this expression does **not** require computing $Z(g,J)$.

> [!proof]- Two-line derivation
> Separate $E_g(s)=-s_ih_i+E_{-i}(s_{-i})$, where $E_{-i}$ does not depend on $s_i$. Normalising the two weights $e^{h_i}$ and $e^{-h_i}$ for $s_i=+1,-1$ gives the stated conditional probability.

> [!definition] Pseudolikelihood and its negative log
> Replace the intractable **joint** likelihood by the product of node-conditionals over observations:
> $$\mathrm{PL}(g;F,J)=\prod_{t=1}^T\prod_{i=1}^N P(s_i^{(t)}\mid s_{-i}^{(t)},g,J).$$
> The function to minimise is
> $$\boxed{F_{\mathrm{PL}}(g)=-\ln\mathrm{PL}(g;F,J)=\sum_{t=1}^T\sum_{i=1}^N\ln\left(1+e^{-2s_i^{(t)}h_i^{(t)}}\right).}$$
> **Pseudolikelihood is *not* the exact joint likelihood.** It is a tractable *surrogate* that preserves useful local conditional information.

## 4. Metropolis: sample candidate graphs using pseudolikelihood

> [!algorithm] Fixed-$N,L$ graph reconstruction by Metropolis (Tutorial 9)
> **Target:** on the simple graphs $\Omega_{N,L}$, use a uniform graph prior and the **pseudo-posterior weight** $w(g)\propto\mathrm{PL}(g;F,J)=e^{-F_{\rm PL}(g)}$.
> 1. **Initialise:** choose any simple graph $g$ with $N$ nodes and exactly $L$ edges; calculate $F_{\rm PL}(g)$.
> 2. **Propose:** uniformly select one existing edge to remove and one **currently absent** pair to add, giving a new graph $g'\in\Omega_{N,L}$. This keeps $L$ fixed and is **symmetric**: forward and reverse proposals have the same probability.
> 3. **Score:** compute $\Delta F=F_{\rm PL}(g')-F_{\rm PL}(g)$.
> 4. **Accept/reject:** use
>    $$\boxed{A(g\to g')=\min\{1,e^{-\Delta F}\}.}$$
>    Always accept a better (lower-$F$) graph; sometimes accept a worse graph. On rejection **stay at the original graph**, and count the step.
> 5. **Sample:** after burn-in, record graphs (including repeats), assess mixing and compute observable averages. The benchmark compares sampled graphs to the hidden truth; in real inference **the truth is not known**.
>
> This is **sampling**, not simply greedily minimising $F_{\rm PL}$. For the detailed-balance derivation, see [[Metropolis–Hastings]]. The stationary target here is a **pseudolikelihood-based distribution**, **not** the exact Ising posterior $P(g\mid F)$.

> [!proof]- Why $F_{\rm PL}$ gives the Metropolis rule
> For a symmetric proposal $\Pi(g\to g')=\Pi(g'\to g)$ and $w(g)\propto e^{-F_{\rm PL}(g)}$,
> $$\frac{w(g')\Pi(g'\to g)}{w(g)\Pi(g\to g')}=\frac{e^{-F_{\rm PL}(g')}}{e^{-F_{\rm PL}(g)}}=e^{-\Delta F}.$$
> The unknown normalisation over all graphs cancels. This is exactly the [[Metropolis–Hastings|MH]] acceptance probability.

## 5. Consequences and what the tutorial illustrates

> [!exam] What happens at $J=0$?
> Then $h_i=0$ for every node and configuration, so each node-conditional equals $1/2$ and
> $$F_{\rm PL}(g)=TN\ln 2\quad\text{for every }g.$$
> All proposed graph exchanges are accepted; the target is **uniform over $\Omega_{N,L}$**, and the expected overlap returns to the **chance baseline** $L^2/Y$.

> [!remark] Benchmark results are not guarantees
> - In Tutorial 9, Pearson reconstruction gets **44/100** links; the supplied $J=0.4$ pseudolikelihood run averages roughly **67/100** correct links in the displayed parameter sweep.
> - The observed acceptance rate for some non-zero-$J$ graph chains is about **$0.5\%$**. That is a warning: **strong serial correlation or poor mixing** can make finite runs unreliable even when the target is correct.
> - The tutorial explores $J\in[0,1]$, including a misspecified $J=1$. Using hidden-edge overlap to pick $J$ is only possible for **synthetic benchmarking**; real data require validation or an inference strategy for $J$.
> - Correlation is **symmetric association**, not proof of a direct causal interaction. Ising inference adds model assumptions; it does not automatically establish causation either.

> [!code]- The essential score in NumPy (Tutorial 9)
> ```python
> # states has shape (T,N) with entries -1 or +1; G is a candidate graph.
> A = nx.to_numpy_array(G, nodelist=range(len(G)), weight=None)
> fields = J * (states @ A)           # fields[t,i] = J sum_j A[i,j] s[t,j]
> F_PL = np.logaddexp(0, -2 * states * fields).sum()
> # For a proposed edge swap: accept with min(1, exp(-(F_PL_new - F_PL))).
> ```

> [!selftest]- Self-test
> 1. **Input difference: link prediction versus reconstruction from activity?** — Partial edges versus observed node states.
> 2. **Why not minimise only $E_g(s)$ across graphs?** — $Z(g,J)$ depends on the candidate graph.
> 3. **Why pseudolikelihood?** — Node-conditionals have a tractable form independent of $Z$.
> 4. **What is the target of Metropolis here?** — $w(g)\propto e^{-F_{\rm PL}(g)}$ on graphs with fixed $N,L$, not the exact Ising posterior.
> 5. **At $J=0$?** — Uniform graph sampling and expected overlap $L^2/\binom N2$.

---
Related: [[Link prediction]] · [[Metropolis–Hastings]] · [[Maximum entropy and ERGMs]] · [[Stochastic block models]]
