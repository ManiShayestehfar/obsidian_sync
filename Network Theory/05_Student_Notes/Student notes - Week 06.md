---
type: student-source
week: 6
status: supplementary-unverified-source
---

# Student notes - Week 06

[[Student notes index]] · [[Corrections and caveats]]

> [!warning] Secondary source
> Format conversion of Jeny Yuan’s supplied LaTeX notes (identified by the user as last year’s notes). Mathematical errors in the source are retained here, not endorsed. Use the checked 2026 lecture notes for Weeks 1–7. Missing figures are labelled. Formatting has been normalised; the original TeX is retained in `06_Sources/student_notes_original.tex`.

We want to sample random graphs that have a high clustering. It is computationally difficult to explore this space using local Monte-Carlo methods like Case I, II and III sampling.

Recall in our previous methods we could sample $g\in \Omega$ with uniform probability and weigh it by $x(g)$. But this is not feasible because we will never sample $g$ with $x(g)$ far from a “typical" value $x(g)$.

In our methods we have always kept $p(g) = p(x(g))$ a constant in our random graph model. But we will now choose $p(g)$ to give more weight to graphs with a higher clustering, and create an MCMC that samples from $p_g$ as $\{x_g\}_{p_g}$. Two main problems arise: (1) what $p_g$ should be used, and (2) how can we sample from an arbitrary $p_g$?

# Metropolis-Hastings MCMC & ERGMs

## Metropolis-Hastings MCMC

To answer the second question, we consider the **Metropolis-Hastings MCMC**. Start from the *detailed balance* condition $$p(g)W(g\to g') = p(g') W(g'\to g)$$

The key idea is to split $W(g\to g')$ into two steps (Accept-Reject method):

1.  **Proposal** probability $\pi(g\to g')$

2.  **Acceptance** probability $A(g\to g')$

3.  Hence $W(g\to g') = \pi(g\to g')A(g\to g')$.

From the detailed balance we want $$\frac{W(g\to g')}{W(g'\to g)} = \frac{\pi(g\to g')A(g\to g')}{\pi(g'\to g)A(g'\to g)} = \frac{p(g')}{p(g)}$$ and hence $$\frac{A(g\to g')}{A(g'\to g)} = \frac{p(g')\pi(g'\to g)}{p(g)\pi(g\to g')} \,.$$ And as $A()$ is a probability $\in[0,1]$, the fraction is either $$\frac{p(g')\pi(g'\to g)}{p(g)\pi(g\to g')}\geq 1 \quad\text{or}\quad \frac{p(g)\pi(g\to g')}{p(g')\pi(g'\to g)} \geq 1$$

We can choose either $A(g\to g')=1$ or $A(g'\to g)=1$. A solution to the detailed balance is $$\label{metroAlgo1}
A(g\to g') = \min \left\{ 1, \frac{p(g')\pi(g' \to g)}{p(g)\pi(g\to g')}\right\}$$

The Markov chain will sample from $p(g)$ if we choose a sample using this method (assuming Ergodicity). This is the *Metropolis-Hastings* choice. Note also that we frequently have $\pi(g\to g') = \pi(g'\to g)$.

Explicitly, the *Metropolis-Hastings algorithm* is: $$\label{metroAlgo2}
A(g\to g') = 
    \begin{cases}
        1 & \mathrm{for}\;p(g')\geq p(g)\\
        \frac{p(g')}{p(g)} & \mathrm{for}\;p(g')< p(g)
    \end{cases}$$ The algorithm to estimate $x_{RG}$ from a RG $(\Omega,p_g)$ is as such:

1.  Start with $g(t=0)\in \Omega$.

2.  Propose a state $g'$ with probability $\pi(g\to g')$. For example using $T(g\to g')$ suitable to $\Omega$.

3.  Compute $A=A(g\to g')$ using [[Student notes - Week 06|source cross-reference: metroAlgo1]] or [[Student notes - Week 06|source cross-reference: metroAlgo2]].

4.  Draw a random number $r\in [0,1]$:

    - If $r>A$ then we reject $g'$ which means $g(t+1)= g$.

    - If $r<A$ then we accept $g'$ and let $g(t+1)=g'$.

5.  Repeat step 2 to 4, $t$ times, sampling $g(t)$.

We consider samples $S$ for $t>t_{\text{equilibrium}}$: $$\hat x_{RG} = \frac 1 {|S|} \sum_{g\in S} x(g(t))$$

Some remarks:

- $T(g)$ needs to ergodically explore $\Omega$ and $p(g)>0$ for all $g\in \Omega$.

- Sampling occurs also when rejecting, i.e. Markov time is evolving when we reject as well. (q.v. step 4 in above and when $r>A$)

## Exponential Random Graph Models (ERGMs)

To solve the second main problem on how to choose $p(g)$, let us consider $i=1,2,...,m$ different constraints $x_i$. To constrain $p(g)$ we use $$\begin{cases}
    x_i^{RG} \equiv \sum_{g\in \Omega} p(g)x_i(g) = x_i^* & \text{for }i=1,...,m \\
    \quad \sum_{g\in \Omega} p(g) = 1 
\end{cases}$$ So we have $|\Omega|$ unknowns where the number of constraints $m+1 \ll |\Omega|$. So in general it is impossible to fully determine the unknowns.

### Maximum Entropy Principle

The best choice of $p(g)$ is the one that satisfies one of the equivalent statements below:

- Adds no additional information beside the constraints

- Maximises the randomness

- Maximises the Gibbs-Shannon entropy (subject to constraints) $$H(p)=-\sum_{g\in\Omega}p(g)\log p(g)$$

**Example**

If $m=0$ then the only constraint is $\sum_{g\in \Omega} p(g) =1$. We can use the Method of Lagrange Multipliers: $$\mathcal L (\boldsymbol p ; \lambda ) = -\sum_{g\in \Omega} p(g)\log p(g) - \lambda \left( 1-\sum_{g\in \Omega} p(g)\right)$$ and $\lambda$ is our Lagrange multiplier. We maximise $\mathcal L$ with respect to $p(g)$ for *one* graph $g$. Then $$\frac{d\mathcal L}{d p(g)} = -\log p(g) - p(g)\cdot \frac 1p(g) +\lambda = 0$$ so $\log p(g) = \lambda - 1$ and $p(g)=\exp(\lambda -1)$ is a constant. We fix $\lambda$ $$\sum_{g\in \Omega} p(g) = \sum_{g\in \Omega} \exp(-\lambda-1) = 1 \implies p_g=\frac{1}{|\Omega|} \text{ is constant}$$

Case with $m+1$ constraints ($x_i$ for $i=1,...,m$): $$\mathcal L(p;\lambda)=-\sum_{g\in\Omega}p(g)\log p(g)-\lambda\left(1-\sum_{g\in\Omega}p(g)\right) - \sum_{i=1}^m\beta_i\left(x_i^*-\sum_{g\in\Omega}p(g)x(g)\right)$$ where each $\beta_i$ are also Lagrange multipliers. So we maximise $\mathcal L$ for a graph $g$. $$\begin{aligned}
\frac{d\mathcal L}{d p(g)} &= -\log p(g) - p(g)\cdot \frac{1}{p(g)} + \lambda +\sum_{i=1}^m \beta_i x_i(g) = 0\\
\log p(g) &= \lambda-1+\sum_{i=1}^m \beta_i x_i(g) \\
p(g) &= \exp(\lambda-1)\exp\left(\sum_{i=1}^m\beta_ix_i\right)\\
\exp(\lambda-1) &= \frac{1}{\mathcal Z} \quad \text{for } \mathcal Z \text{ partition function}\\
\sum_{i=1}^m \beta_i x_i &\equiv H(x) \to \mathrm{Hamiltonian}\\
p(g)&=\frac{1}{\mathcal Z} \exp(\sum_{i=1}^m \beta_i x_i(g)) \text{ Boltzmann distribution}
\end{aligned}$$

Now to consider **exponential random graph models (ERGMs)**, we have:

- $\Omega$ is a suitable set of graphs.

- Define $p(g)=\exp(\sum \beta_i x_i(g))/\mathcal Z$ for any $g\in \Omega$ and $x_i\colon g\to \mathbb R$ is a graph measure. The normalisation constant $\mathcal Z$ is not important in the sampling. We can tune $\beta_i$ for $i=1,\dots, m$ to impose the constraints that we want. Fixing the parameters is typically done based on $m$ observables/statistics of interest: $x_1^*,...,x_m^*$.

- If $x(g) = L(g)$, the number of edges is fixed (on average), the Poisson RG is retrieved. Hence, ERGMs are generalisations of the Poisson RG for different observables $x(g)$.

## Metropolis for ERGMs

We will sample ERGMs using the Metropolis Hastings approach.

1.  Fit $\beta$ by repeating the Metropolis algorithm for $\beta\in[\beta_{\min}, \beta_{\max}]$. For $\beta=0$, we have uniform probability, therefore a normal random graph, and the clustering coefficient remains low. However, as we increase $\beta$, the clustering increases. Here the acceptance of the Metropolis algorithm is $$A(g\to g') = 
            \begin{cases}
                1 & {p(g')>p(g)} \\
                \frac{p(g')}{p(g)}  = \exp{(\beta(x(g')-x(g)))} & p(g')\leq p(g)
            \end{cases}$$

2.  For $\beta_i = \beta_i^*$ (i.e. we have fitted our $\beta$’s). We discard the equilibration time and collect samples $g(t)$ using the same Metropolis algorithm.

**Remarks:**

- When $g'$ is rejected, we sample $g$ again $(t\to t+1)$.

- Equilibration/Mixing time of the chain depends on moving in $g\in\Omega$, and thus on the *‘acceptance rate’*.
