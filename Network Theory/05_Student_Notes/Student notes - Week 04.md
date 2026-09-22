---
type: student-source
week: 4
status: supplementary-unverified-source
---

# Student notes - Week 04

[[Student notes index]] · [[Corrections and caveats]]

> [!warning] Secondary source
> Format conversion of Jeny Yuan’s supplied LaTeX notes (identified by the user as last year’s notes). Mathematical errors in the source are retained here, not endorsed. Use the checked 2026 lecture notes for Weeks 1–7. Missing figures are labelled. Formatting has been normalised; the original TeX is retained in `06_Sources/student_notes_original.tex`.

# Monte Carlo Methods

1.  Start with $g=g_0\in\Omega$ (eg. $g_0=g^*$).

2.  Apply a transformation $g'=T(g): \Omega\rightarrow\Omega$.

3.  Measure $x(g')$.

4.  Repeat steps 2 and 3 $t$ times.

When does this work?

- Let $W(g\rightarrow g')$ be the probability of moving from $g$ to $g'$ via $T$. We would like $\sum_{g'\in\Omega} W(g\rightarrow g')=1$.

- Let $w_g(t)$ be the probability of being at $g$ at time $t$, with $\boldsymbol{\boldsymbol{w}}=(w_1,w_2,...,w_g,...,w_{|\Omega|})$. A **Monte Carlo iteration** is given by the Markov Chain: $$w_g(t+1)=\sum_{g^+\in\Omega} W(g^+\rightarrow g) w_{g^+}(t)$$ or $$\boldsymbol{\boldsymbol{w}}(t+1)=W\boldsymbol{\boldsymbol{w}}(t)$$

Let the initial condition be $g=g_0\implies \boldsymbol{\boldsymbol{w}}=(0,0,...,1,...,0)$ where the $1$ is situated at $g_0$.

We expect that, for large $t$, $\boldsymbol{\boldsymbol{w}}(t)\propto\boldsymbol{\boldsymbol{w}}_1$, which is the eigenvector associated with the largest eigenvalue of $W$ by the Perron-Frobenius theorem.

We would like to know when $\boldsymbol{\boldsymbol{w}}_1$ is equal to $\boldsymbol{\boldsymbol{p}}=(p_1,p_2,...,p_g,...,p_{|\Omega|})$.

There are three conditions that should be satisfied

1.  $g\in\Omega\implies T(g)\in\Omega$ or in other words, $W(g\to g')=0$ for $g'\notin \Omega$.

2.  Ergodicity: there is a nonzero probability to go from any $g\in \Omega$ to any other $g'\in \Omega$ for $t\to \infty$.

3.  Detailed balance (equilibrium): $p_g W(g\to g')=p_{g'}W(g'\to g)$ for all $g,g'\in\Omega$.

Justification:

- From (3) we sum over all $g'\in \Omega$ and get $$\begin{aligned}
          \sum_{g'\in \Omega} p_gW(g\to g') &=  \sum_{g'\in \Omega} p_{g'}W(g'\to g)\\
          p_g \sum_{g'\in \Omega} W(g\to g')&= \sum_{g'\in \Omega} p_{g'}W(g'\to g)\\
          \boldsymbol p &= \boldsymbol p W 
      
  \end{aligned}$$ so $1$ is an eigenvalue of $W$ with eigenvector $\boldsymbol p$.

- \(2\) implies that $W$ is an irreducible matrix. So we can use the Throb theorem to see that $\lambda_i\leq 1$. Altogether, this implies $\lambda=1$ is the largest eigenvalue, which implies $\boldsymbol{\boldsymbol{w}}_1\propto\boldsymbol{\boldsymbol{p}}$.

## Simple Graph with Fixed Number of Nodes

Let $p(g)=\frac{1}{|\Omega|}=2^{-\frac{N(N-1)}{2}}$, where $N$ is fixed.

One possible transformation $T(g)$ is:

1.  Picking two nodes $i$ and $j$ randomly where $i\neq j$.

2.  Flipping links: if $A_{ij}=1$, then $A_{ij}\leftarrow 0$; if $A_{ij}=0$, then $A_{ij}\leftarrow 1$.

We check the conditions

1.  It is clear that if $g\in \Omega$ then $T(g)\in \Omega$.

2.  Ergodicity also holds

3.  We have $$W(g\to g') = \begin{cases}
        1/\binom N2 & \text{if $|L(g)-L(g')| = 1$}\\ 
            0 & \text{otherwise}
        \end{cases}$$ so $$p_g W(g\to g') = \begin{cases}
            1/|\Omega|\cdot  1/\binom N2 = p_{g'}W(g'\to g) \\
            0
        \end{cases}$$

In principle, this MCMC can sample graphs with any number of edges $L=L^*$. However, in a random graph $G$ with fixed $N$, the peak of the distribution of $p(L)$ is at $L=\frac{Y}{2}=\frac{N(N-1)}{4}$, then the sample mainly contains $L=\frac{Y}{2}$ where $Y=\binom N2$. Hence in practice we do not sample graphs with $L\ll\frac{Y}{2}$ in reasonable time.

## Networks with Fixed $N$ and $L$

$$\left\{\text{Case 2: simple graphs with $N,L$ fixed}\right\} \subseteq \left\{\text{Case 1: simple graphs with $N$ fixed}\right\}  \subseteq \Omega$$

A possible transformation $T$ is as such:

- Pick an edge ($A_{i,j}=1$) randomly.

- Pick a non-edge ($A_{s,t}=0$) randomly.

- Swap the edges: $A_{i,j}\leftarrow 0$ and $A_{s,t}\leftarrow 1$.

Note that:

- The sampling is NOT iid from $p_g$.

- $\boldsymbol{\boldsymbol{w}}(t)\xrightarrow[t \to\infty]{} \boldsymbol{\boldsymbol{p}}$.

- We need to wait for equilibration ($t>t_{\text{equilibrium}}$) and sample over time $t>t_{\text{correlation}}$.

- $t_{\text{equilibrium}}\approx t_{\text{correlation}}$ scales as

  - $\frac{N(N-1)}{2}$ in case 1.

  - $L$ in case 2.

## Networks with Fixed $N$ and fixed degree sequence $\{z_i\}$ (Refer to Configuration Model)

Possible Transformation $T$:

1.  Pick two edges randomly, suppose have $(i,j)$ and $(s,r)$

2.  Consider all allowable swaps between $(i,j)$ and $(s,r)$, i.e. no self-loops, no multi-edge. For example, swap in to $(i,r)$ and $(s,j)$

3.  Perform one acceptable swap chosen randomly.

*Check conditions:*

1.  $g\in \Omega\implies g':=T(g) \in \Omega$

2.  Ergodicity

3.  Detailed balance: $W(g\to g') = W(g'\to g)$ and $p(g)=p(g') = \mathrm{cst} \implies\mathrm{D.B.}$

We expect the equilibration time $t_e\sim L$. We can thus compute: $$\hat{x}_{RG}=\frac{1}{|S|}\sum_{g\in S} x(g)$$ where $g=g(t)$ and $S$ is the set of sampled graphs in the MCMC, requiring $t>t_{\text{equilibrium}}$ and $t_{\text{sampling}}\gg t_{\text{correlation}}$.

## Configuration Model

1.  Choose a degree sequence $\{z\}=(z_1,z_2,...,z_n)$.

2.  Generate the $z_i$ "stubs" of links $i=1,...,N$.

3.  Connect stubs randomly with equal probability.

**Note 1**. This allows for *multi-edges* and *self-loop*, i.e. may not be simple.

Properties of the model:

- The network is sparse if the degree sequence is chosen from a distribution with a well-defined $\langle z\rangle$.

- The probability of a link between nodes $i$ and $j$:

  - For a stub in $i$: $p=\frac{z_i}{2L}$

  - Sum over all stubs in $i$ and $j$: $p_{ij} =z_j \frac{z_i}{2L}$

- Clustering: $p_{jk}=\frac{z_jz_k}{2L}$ for $2L=\langle z\rangle N$ and constant $z_j$, $z_k$. Then $C\sim \frac{1}{N}\to 0$ as $N\to\infty$.

- $d_{\text{diameter}}$: sparse and $C\to 0\implies d_{\text{diameter}}\sim \frac{\ln N}{\ln \langle z\rangle}$

To note:

- Not all degree sequences generate (simple) graphs, see Erdös–Gallai theorem.

- Typical realisations of configuration models are not simple graphs due to self and multiple loops.

- For large $N$, we expect that *almost all* graphs of the configuration model will not be simple graphs, and that the fraction of edges that violate the simple graph conditions *decays to zero*.
