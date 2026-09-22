---
type: student-source
week: 2
status: supplementary-unverified-source
---

# Student notes - Week 02

[[Student notes index]] · [[Corrections and caveats]]

> [!warning] Secondary source
> Format conversion of Jeny Yuan’s supplied LaTeX notes (identified by the user as last year’s notes). Mathematical errors in the source are retained here, not endorsed. Use the checked 2026 lecture notes for Weeks 1–7. Missing figures are labelled. Formatting has been normalised; the original TeX is retained in `06_Sources/student_notes_original.tex`.

# Graph Measures

## Centrality

**Centrality measures** of node $i$:

- Degree $z_i$

- Average shortest path $\langle d\rangle_i$

- **Between-ness centrality** $B_i\equiv\sum_{s=1, s\neq i}^N\sum_{t=1}^N\frac{\eta_{st}^i}{|\eta_{st}|}$ where

  - $\eta_{st}^i$ is the number of shortest paths between nodes $s$ and $t$ that pass through node $i$.

  - $|\eta_{st}|$ is the number of shortest paths between $s$ and $t$.

- **Eigenvector centrality** $x_i=v_{1i}\in\mathbb{R}$ where $x_i=\frac{1}{\lambda_1}\sum_{j=1}^NA_{ij}x_j$ (see below ofr P-F Theorem and propagation process).

  - Note that in directed networks, $A_{ij}\neq A_{ji}$. So nodes with $z^{\text{in}}=0$ have $x=0$, and nodes that have in-degree from nodes with $z^{\text{in}}=0$ also have $x=0$.

  - Another problem: centrality is passed on in full to neighbours. This might not make sense eg. Google links to everyone and has high centrality would mean everyone gets Google’s centrality.

- **Katz centrality** $\boldsymbol{x}=\frac{\beta}{\gamma}(I-\frac{\alpha}{\gamma}A^{-1})\mathbbm{1}$ which comes from that $\boldsymbol{x}(t+1)=\alpha A\boldsymbol{x}(t)+\beta\mathbbm{1} \implies \boldsymbol{x}(t+1) \propto \gamma\boldsymbol{x}(t)$ for $\alpha,\beta, \gamma\in\mathbb{R}$ and $\mathbbm{1}$ a unit vector. As we are interested in relative measures, we can set $\beta=\gamma=1$.

- **Page-rank algorithm** $\boldsymbol{x}(t+1)=\alpha\sum_{j=1}^N\frac{A_{ij}x_j}{z_j^{\text{out}}}+\beta\mathbbm{1}$

  This time, the centrality of a high degree node is shared amongst the nodes that it links to. An expression for the PageRank update is $$\boldsymbol{x}(t+1) = \alpha AD^{-1}\boldsymbol{x}(t)  + \beta \mathbbm 1 \implies \boldsymbol{x} = \beta(I - \alpha AD^{-1})^{-1} 
      \mathbbm 1$$ and again we set $\beta = 1$ and hence $\boldsymbol{x} = (I - \alpha AD^{-1})^{-1} \mathbbm 1$.

**Theorem 1** (Perron-Frobenius Theorem). Let $|\lambda_1|\geq...\geq|\lambda_N|$ be the $N$ eigenvalues of a $N\times N$ matrix $A$, and $\boldsymbol{v}_1,...,\boldsymbol{v}_N$ be their corresponding eigenvectors: $A_i\boldsymbol{v}_i=\lambda_i\boldsymbol{v}_i$. We hypothesise that the entries of $A$ are non-negative, and that $A$ is irreducible (single connected component). Then, the theorem states that:

- The largest eigenvalue $\lambda_1: \min_{ij}A_{ij}\leq\lambda_1\leq\max_i\sum_jA_{ij}$ is real.

- The components of $\boldsymbol{v}_1=(v_{11},...,v_{1N})$ are all real.

Process - **propagation** through the network:

- Start with a measure $\boldsymbol{x}=(x_1,...,x_{N})$ for $x_i\in\mathbb{R}$

- Evolve it in time as: $$x_i(t+1)=\sum_{j=1}^NA_{ij}x_j(t)\implies \boldsymbol{x}(t+1)=A\boldsymbol{x}(t)$$

- Decompose $\boldsymbol{x}_0=\sum_{k=1}^Na_k\boldsymbol{v}_k$ and set initial condition $\boldsymbol{x}(t=0)=\boldsymbol{x}_0$

- Then $$\boldsymbol{x}(t)=A^t\boldsymbol{x}(0)=A^t\sum_{k=1}^Na_k\boldsymbol{v}_k(0)=\sum_{k=1}^Na_k\lambda_k^t\boldsymbol{v}_k=\lambda_1^t\sum_{k=1}^Na_k\left(\frac{\lambda_k}{\lambda_1}\right)^t\boldsymbol{v}_k$$ where $\lim_{t\rightarrow\infty}\left|\left(\frac{\lambda_k}{\lambda_1}\right)^t\right|\rightarrow 0$ for all $k\neq 1$.

## Sampling

Let $m=1,2,...,M$ be the different types of observations, and $m(s)$ be the type of sample $s$. Let $\mu(m):\mathbb{N}\rightarrow\mathbb{R}$ be a function of the sample type. The expected value over the population is: $$\mathbb E(\mu) \equiv \lim_{Q\rightarrow\infty}\frac{1}{Q}\sum_{q=1}^Q\mu(m(q))=\sum_{m=1}^M p_m\mu(m)$$ where $p_m=\lim_{Q\to\infty}\frac{1}{Q}\sum_{q=1}^\infty \delta(m(q)-m)$ is the probability of sampling a ball of type $m$ ($\delta(0)=1$ and $\delta(x)=0$ for $x\neq 0$).

We estimate $\mathbb E(\mu)$ and $p_m$ as $\hat{\mu}$ and $\hat{p}$ from finite sample sizes $S$: $$\begin{aligned}
    \hat{p}_m &= \frac{1}{S}\sum_{s=1}^S\delta(m(s)-m) \\
    \hat{\mu} &\equiv \sum_{m=1}^M \hat{p}_m\mu(m)
\end{aligned}$$

The expected value of estimators over $r=1,...,R$ realisations: $$\mathbb E(\hat{p}_m)=\lim_{R\to \infty}\frac{1}{R}\sum_{r=1}^R \hat{p}_m(r)=\lim_{R\rightarrow\infty}\frac{1}{RS} \sum_{r=1}^R \sum_{s=1}^S\delta(m(s)-m)=p_m$$ ie. $\hat{p}_m$ is an unbiased estimator of $p_m$. Similarly: $$\mathbb E(\hat \mu)\equiv\lim_{R\rightarrow\infty}\frac{1}{R}\sum_{r=1}^R\hat{\mu}(r)=\lim_{R\to\infty}\frac{1}{R}\sum_{r=1}^R \sum_{s=1}^S\mu(m(s))= \lim_{R\to \infty} \frac 1R \sum_{r=1}^R \sum_{m=1}^M \hat p_m(r) \mu(m) = \sum_{m=1}^Mp_m\mu(m)=\mathbb E(\mu)$$

Observed data are often finite and biased samples. Sampling methods to obtain networks include:

- Node sampling: pick users and look at all links.

- Edge sampling: pick links and check users involved.

- Random walks: start at a node, pick a random link, check all links to the new node, repeat.

- Snowball sampling: start at a node, pick all neighbours, go to all neighbours, repeat.
