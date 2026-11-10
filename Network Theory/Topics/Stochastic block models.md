---
tags: [data5441, ch07, inference]
aliases: [SBM, Block model, Assortative, Disassortative, Core-periphery]
---
---
# Stochastic block models

> [!abstract] Overview
> A **stochastic block model (SBM)** generalises Erdős–Rényi random graphs by allowing edge probabilities to depend on **group membership**. Given a partition, the connectivity probabilities are estimated by counting edges; the harder problem is inferring the partition itself.
>
> **Course:** Week 7 · [[Ch07 SBMs and statistical inference]]

## 1. Motivation and model

The Erdős–Rényi model assigns the same edge probability to every node pair. Many networks instead have **mesoscopic structure**: densely connected communities, groups connected mainly to one another, or a dense core surrounded by a sparse periphery.

> [!definition] Stochastic block model
> Partition the $N$ nodes into $B$ non-empty blocks $\alpha_1,\ldots,\alpha_B$. Write $b_i\in\{1,\ldots,B\}$ for the block containing node $i$, and $\mathbf b=(b_1,\ldots,b_N)$ for the **allocation vector**.
>
> Conditional on $(\mathbf b,P)$, distinct edges are independent, with
> $$\boxed{\Pr(A_{ij}=1\mid\mathbf b,P)=p_{b_i b_j}},\qquad P=(p_{rs})_{r,s=1}^{B}.$$
> Here $P$ is the **connectivity matrix**, $0\le p_{rs}\le1$. For undirected simple graphs, $P=P^{\mathsf T}$, $A_{ij}=A_{ji}$ and $A_{ii}=0$; independence refers to the unordered pairs $i<j$.

Taking $B=1$ recovers $G(N,p)$. More generally, the block probabilities encode different structures:

| Structure | Typical pattern |
|---|---|
| **Assortative** (communities) | $p_{rr}>p_{rs}$ for $r\ne s$ |
| **Disassortative** | Edges preferentially cross blocks; bipartite: $p_{11}=p_{22}=0$ |
| **Core–periphery** | $p_{cc}>p_{cp}>p_{pp}$ (a typical two-block example) |

![[sbm-block-structure.png|550]]

*One SBM realisation (left) and its adjacency matrix, ordered by block (right). Dense diagonal submatrices reveal assortative structure.*

## 2. Estimation for a fixed partition

Suppose the observed adjacency matrix $A$ and the allocation $\mathbf b$ are known. Let $n_r=|\alpha_r|$, $l_{rs}$ be the number of **observed** edges between blocks $r,s$, and $y_{rs}$ the number of **possible** edges.

| Node pairs | Undirected, no self-links | Directed, no self-links |
|---|---|---|
| $r=s$ | $y_{rr}=\binom{n_r}{2}$ | $y_{rr}=n_r(n_r-1)$ |
| $r\ne s$ | $y_{rs}=n_rn_s$ | $y_{rs}=n_rn_s$ |

In the undirected case, count each edge once and use only $r\le s$. For a directed graph, use all ordered block pairs $(r,s)$.

> [!theorem] Likelihood and maximum-likelihood estimate
> For an undirected simple SBM,
> $$\mathcal L(A\mid\mathbf b,P)=\prod_{r\le s}p_{rs}^{l_{rs}}(1-p_{rs})^{y_{rs}-l_{rs}}.$$
> Hence, for every $y_{rs}>0$,
> $$\boxed{\hat p_{rs}=\frac{l_{rs}}{y_{rs}}=\frac{\text{observed edges}}{\text{possible edges}}.}$$
> The formula also covers boundary estimates $0$ and $1$. If $y_{rs}=0$, the corresponding probability is not identifiable.

> [!proof]- Why the estimate maximises likelihood
> For one block pair, maximise $f(p)=l\ln p+(y-l)\ln(1-p)$. When $0<l<y$,
> $$f'(p)=\frac lp-\frac{y-l}{1-p}=0\quad\Longrightarrow\quad p=\frac ly,$$
> and $f''(p)<0$. When $l=0$ or $l=y$, the maximum occurs at $p=0$ or $p=1$, respectively. $\square$

## 3. Inferring the blocks

With unknown memberships, estimate $P$ for **each candidate partition**, then compare the resulting likelihoods. Define the *profile negative log-likelihood*

$$\boxed{F(\mathbf b)=-\log\mathcal L\big(A\mid\mathbf b,\hat P(\mathbf b)\big).}$$

For a fixed $B$, maximum-likelihood inference amounts to **minimising $F(\mathbf b)$**. This is computationally challenging: the number of partitions into $B$ non-empty, unlabelled blocks is the Stirling number $S(N,B)$, which can be enormous.

> [!algorithm] Two approaches from Week 7
> **Greedy search:** Start from an allocation, examine permitted single-node block moves, and make the move that decreases $F$ most. Stop when none improves $F$. The result may be a **local minimum**; different initial allocations may give different answers.
>
> **Metropolis sampling:** Propose a valid block move $\mathbf b\to\mathbf b'$ and set $\Delta F=F(\mathbf b')-F(\mathbf b)$. For a symmetric proposal, accept with
> $$\boxed{a(\mathbf b\to\mathbf b')=\min\{1,e^{-\beta\Delta F}\}.}$$
> At $\beta=1$, an ergodic chain samples allocations with weights proportional to $e^{-F}$. **Simulated annealing** gradually increases $\beta$ to favour lower values of $F$; it does not guarantee the global minimum.

Block labels themselves have no meaning: two allocations that differ only by permuting labels represent the **same partition**.

> [!warning] Why likelihood alone cannot choose $B$
> At $B=N$, give each node its own block and choose $\hat p_{ij}=A_{ij}$. The observed graph then has likelihood $1$, hence $F=0$: a perfect but uninformative fit. Selecting $B$ requires accounting for **model complexity** (e.g. Bayesian priors). See [[Statistical inference and model selection]].

> [!remark] Degree heterogeneity
> In an ordinary SBM, nodes in the same block have the same expected degree,
> $$\mathbb E[z_i\mid b_i=r]=(n_r-1)p_{rr}+\sum_{s\ne r}n_sp_{rs}.$$
> Consequently, the SBM may group hubs together rather than recover the expected communities (as in Tutorial 7's Karate Club example). A **degree-corrected SBM** adds node-specific degree parameters to address this limitation.

## 4. Worked exam patterns

> [!exam] A. Bipartite authorship — Trial 2, Q6
> There are $200$ articles, $40$ authors and on average $3$ authors per article. Treat articles and authors as the two blocks.
>
> $$L=200\cdot3=600,\qquad \hat p_{11}=\hat p_{22}=0,\qquad\boxed{\hat p_{12}=\hat p_{21}=\frac{600}{200\cdot40}=\frac3{40}.}$$
>
> For two particular authors and another specified article, the probability that **both** authors wrote it is $(3/40)^2=9/1600$. The model misses persistent collaborations, so real data generally show **more** repeated co-authorships than this baseline.

> [!exam] B. Directed friendships — Trial 2, Q5
> Three classes $a,b,c$ each contain $30$ students. The mean outgoing friendships per student are
> $$M=\begin{pmatrix}5&0&0\\0&4&1\\1&1&3\end{pmatrix}.$$
> Divide the total observed directed links from $r$ to $s$ by the number of possible directed links:
> $$\boxed{\hat P=\begin{pmatrix}5/29&0&0\\0&4/29&1/30\\1/30&1/30&3/29\end{pmatrix}.}$$
> Within-class denominators are **29 per student**, not 30, because self-links are forbidden. Expected reciprocal $b$–$c$ pairs:
> $$30\cdot30\,p_{bc}p_{cb}=1.$$
> Real social networks often have more reciprocity than this independent-edge model predicts.

> [!exam] C. Five planted groups — Trial 1, Q1(b)
> There are five groups of nine nodes, every node has degree eight, and each pair of distinct groups has two connecting edges.
> $$L=\frac{45\cdot8}{2}=180,\qquad L_{\mathrm{between}}=\binom52\cdot2=20.$$
> Hence each block contains $(180-20)/5=32$ internal edges, giving
> $$\boxed{\hat p_{rr}=\frac{32}{\binom92}=\frac89,\qquad \hat p_{rs}=\frac{2}{9\cdot9}=\frac2{81}\quad(r\ne s).}$$

## 5. Revision essentials

> [!summary] Remember
> - **Definition:** edge probability $p_{b_i b_j}$; distinct edges are conditionally independent.
> - **Fitting:** $\hat p_{rs}=l_{rs}/y_{rs}$; use the correct directed/undirected denominator.
> - **Inference:** optimise $F(\mathbf b)$ for fixed $B$; greedy can get stuck, and Metropolis can cross barriers.
> - **Model selection:** $B=N$ overfits; account for complexity when choosing $B$.
> - **Limitations:** basic SBMs do not capture individual degree variation or edge correlations.

> [!selftest]- Check your understanding
> 1. Why is $y_{rr}=\binom{n_r}{2}$ for an undirected simple graph but $n_r(n_r-1)$ for a directed graph?
> 2. How do you estimate $p_{rs}$ from an observed partition? What if there are no possible edges?
> 3. Why are reciprocal friendships and repeated co-authorships generally underpredicted?
> 4. Why is the smallest $F$ not enough to select $B$?

---
**Related:** [[Statistical inference and model selection]] · [[Community detection]] · [[Link prediction]] · [[Random graph ensembles]]

*Sources: DATA5441 Lecture Notes (2026), Week 7, pp. 85–100; Trial Exam 1, Q1(b); Trial Exam 2, Q5–6.*
