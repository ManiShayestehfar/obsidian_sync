---
type: student-source
week: 7
status: supplementary-unverified-source
---

# Student notes - Week 07

[[Student notes index]] · [[Corrections and caveats]]

> [!warning] Secondary source
> Format conversion of Jeny Yuan’s supplied LaTeX notes (identified by the user as last year’s notes). Mathematical errors in the source are retained here, not endorsed. Use the checked 2026 lecture notes for Weeks 1–7. Missing figures are labelled. Formatting has been normalised; the original TeX is retained in `06_Sources/student_notes_original.tex`.

Recall we can consider measures at either the microscale like $z_i$ and $C_i$ of each node, and the macroscale, like $C_{net}$, $\frac{\sigma_z}{\left\langle{z}\right\rangle}$ and $d_{diam}$. However, it is not enough to only look at the node level, neither is it enough to look at the network as a whole.

Now we consider what happens at the intermediate level (**mesoscale** structures).

Examples of mesoscale structures include

- Assortative communities: e.g. in the Karate club there are two groups in the study. These two groups are mesoscale.

- Core-Periphery structures: e.g. rail network of Sydney – everything is connected to City Circle / Redfern / Sydenham.

<figure>
<p><strong>Figure unavailable in supplied archive: imgs/mesoscale.png</strong></p>
</figure>

Our goal is to model and find such structures. This is related to the *clustering problem*.

# Stochastic Block Models and Statistical Inference

## Stochastic Block Models (SBM)

**Definition 1**. Say $N$ nodes of the network are partitioned into $B$ groups (blocks). This clustering is mutually exclusive and exhaustive. We say that the block assignment $b_i \subseteq \{\alpha_1, \dots, \alpha_B\}$ is a latent variable for each node $i=1,\dots, N$.

A link between $i$ and $j$ is created with probability $P_{r,s}$ that depends on the block assignment $b_i$ and $b_j$ with $$P_{rs} = P(A_{ij}=1) \quad \text{with} \quad b_i = \alpha_r,\quad  b_j = \alpha_s \,$$

The connectivity matrix $P_{rs}=P(A_{ij})$ is defined as follows: $$\left[\begin{array}{c:c:c}
P_{1,1}  & \cdots & P_{1,B} \\
\hdashline
\vdots&\ddots&\vdots\\
\hdashline
P_{B,1} & \cdots & P_{B,B}
\end{array}\right]$$

This is a generalisation of the Poisson RG, where the edge links are generated with probability given by their block assignments. SBMs can generate different types of mesoscale structures

- When $B=1$ we recover the Poisson RG. Everyone is in the same group so we have the same linking probability between two nodes.

- $\beta=2$ $P_{1,1}=P_{2,2}=0, P_{2,1} = P_{1,2}\neq0$ is a bipartite graph: $$```latex
\begin{tikzcd}
	{\mathrm{Group}\ 1} & \bullet & \bullet & \bullet & \bullet & \bullet & \bullet \\
	\\
	{\mathrm{Group}\ 2} & \bullet & \bullet & \bullet & \bullet & \bullet & \bullet
	\arrow[no head, from=1-2, to=3-3]
	\arrow[no head, from=1-2, to=3-5]
	\arrow[no head, from=1-3, to=3-3]
	\arrow[no head, from=1-6, to=3-7]
	\arrow[no head, from=1-7, to=3-3]
	\arrow[no head, from=3-2, to=1-5]
	\arrow[no head, from=3-4, to=1-4]
	\arrow[no head, from=3-5, to=1-6]
	\arrow[no head, from=3-6, to=1-5]
\end{tikzcd}
```

*Original diagram source retained; Obsidian does not render TikZ.*$$

- For an arbitrary $B$, we usually have $$P_{rs} = \begin{cases}
          \varepsilon & r\neq s\\
          p\gg \varepsilon & r = s
      \end{cases}$$ which creates assortative communities. $P_{rs}$ can also be visualised as: $$\left[\begin{array}{c:c:c:c:c}
          p&\varepsilon  & \cdots&\varepsilon & \varepsilon \\
          \hdashline
          \varepsilon&p  & \cdots&\varepsilon & \varepsilon \\
          \hdashline
          \vdots&&\ddots&&\vdots\\
          \hdashline
          \varepsilon &\varepsilon  & \cdots& p&\varepsilon \\
          \hdashline
          \varepsilon&\varepsilon & \cdots&\varepsilon & p
          \end{array}\right]$$

- For $B=2$ $$P_{1,1}\gg P_{0,0}, P_{1,2}=P_{2,1}>P_{0,0}$$

## Inference in Networks

We can use the SBM to generate some networks. From a given network, we can perform some *inference* to say something about the block allocation of the nodes by evaluating statistics of the graph against the parameters of the SBM (random graph models).

We can use a **Bayesian** framework, where we denote $D$ to be the data and $M$ to be the model with parameters $\Theta$: $$\underbrace{P(M\mid D)}_{\mathrm{Posterior}} = {\frac{\overbrace{P(D\mid M)}^{\mathrm{Likelihood}}\overbrace{P(M)}^{\mathrm{Prior}}}{\underbrace{P(D)}_{\mathrm{Evidence}}}}$$

- Model selection/optimisation: maximum likelihood $P\left({D\;|\;M}\right)$ or maximum a posteriori estimate $P(M\;|\;D)$

- Explore/sample plausible models/parameters from $P\left({D\;|\;M}\right)$ or $P\left({M\;|\;D}\right)$

The data is often a single network, hence only a single observation is available. However, for stochastic block models and Poisson RGs, the edges are conditionally independent ($P\left({A,B\;|\;C}\right) = P\left({A\;|\;C}\right)P\left({B\;|\;C}\right)$) which implies that we have $L$ observations.

| Models |           $M$           |                     Parameters $\Theta$                      |
|:------:|:-----------------------:|:------------------------------------------------------------:|
|        |       Poisson RGs       |                  $N,p;\hat{p}=L/\binom N2$                   |
|        |     Exponential RGs     |                          $\beta$’s                           |
|        | Stochastic Block models | \# blocks $B$, probs $p_{r,s}$, allocations $\boldsymbol b$. |

### Inference in SBMs

The likelihood of a simple graph with $\mathbb{A}= A_{ij}$ is $$\label{eq:star}
    P(\mathbb{A}) = \prod_{{r,s<i}} P_{r,s}^{A_{i,j}} \bigl(1-P_{r,s}\bigr)^{1-A_{i,j}} = \prod_{r,s}\prod_{b_j=\alpha_s}\prod_{b_i=\alpha_r} P_{r,s}^{A_{i,j}}(1-P_{r,s})^{1-A_{i,j}}$$ where $\boldsymbol b$ the block allocation vector is taken as fixed. Let $$\ell_{r,s} = \sum_{b_i \in \alpha_n, b_j\in \alpha_s} A_{i,j} = \text{number of edges between blocks $r$ and $s$}$$ and $$g_{r,s} = 
\begin{cases}
    |\alpha_r|\cdot |\alpha_s|, \qquad r\neq s \\
    \left|{\alpha_r}\right| \left({\left|{\alpha_r}\right|-1}\right)) \text{ (no self-edges)}
\end{cases}\qquad\mathrm{maximum}\; \ell_{rs}$$ then [[Student notes - Week 07|source cross-reference: eq:star]] can be written as $$\label{eq:MLE}
   P(g) =P(\mathbb A) = \prod_{r,s \leq 1}^B P_{r,s}^{l_{r,s}} (1-P_{r,s})^{g_{r,s} - l_{r,s}}$$

Now $P_{r,s}$ are independent parameters of the SBM, so the maximum of [[Student notes - Week 07|source cross-reference: eq:MLE]] is the maximum of each term: $$\hat P_{r,s} = \frac{\ell_{r,s}}{g_{r,s}} = \text{fraction of links between }\alpha_r \text{ and }\alpha_s$$

Our challenge is to find the allocation vector $\boldsymbol{b}$ that maximises [[Student notes - Week 07|source cross-reference: eq:MLE]].

The number of possible block assignments is $\frac{B^N}{B!}$, where the $B!$ comes from dividing by the number of permutations given $B$ blocks, but we identify them to be the same, as we only care about the partition.

Computationally, we prefer to minimise $-\log{\eqref{eq:MLE}}$, which is given by $$-\log P\left({g}\right) = -\sum_{r\text{ and }s\geq r}^B \ell_{rs} \log(P_{rs}) +\left({g_{rs}-\ell_{rs}}\right)\log(1-P_{rs})$$ where $P_{rs} = \frac{\ell_{r,s}}{g_{r,s}}$

## Lessons from Tutorial 7

For Q2 of Tutorial 7, we were looking for the best partition of the Karate Club graph that maximises the log likelihood according to the stochastic block model.

For a SBM, the Karate Club partition was more likely than random but unlikely overall compared to the best possible partition, which involved the $5$ central hub nodes in the same block. This is surprising considering that the karate club is comprised of two assortative communities.

For SBMs, this is inevitable. Complex networks often have a degree variability, and from the perspective of the stochastic block model, the only way to account for this is to put the nodes of high degree (hub nodes) into their own block with high connection probability to other blocks. From this perspective, the SBM is naive.

In 2011, \[Neumann , Karrer\] proposed a degree-corrected stochastic block model where $$P(A_{i,j}) \sim z_iz_j \lambda_{r,s}$$ where $\lambda_{r,s}$ is a SBM parameter. \[??\]

The problem of finding $B$ requires accounting for the model complexity. A maximum likelihood estimate is not useful because $$B = N \implies \mathcal L = 1\implies -\log \mathcal L = 0$$ is the maximum (all nodes in their own block with $\{0,1\}$ connection probability.

## High Dimensional Inference

Consider the following issues:

1.  The likelihood $P(\mathrm{data}\mid \mathrm{model})$ or the posterior $P(\mathrm{model}\mid \mathrm{data})$ are intractable, i.e. no analytical solution for maxima.

2.  High dimensional parameter space: $\#\text{ parameters }= N \implies \text{space of possibilities } \sim e^N$, therefore exhaustive exploration is unfeasible.

Hence we require efficient computational methods.

### Variational Inference

The idea is to propose a family of *tractable* probability functions $q(M)$ that approximates $P\left({D\;|\;M}\right)$ or $P\left({M\;|\;D}\right)$. For inference, minimise the *“distance"* between $q(M)$ and $P\left({D\;|\;M}\right)$ or $P\left({M\;|\;D}\right)$. We use a mean-field approximation, that is the parameter space can be partitioned into parameters that are independent to create a more tractable family of probability densities.

*Example:* minimise the *Kullback-Leibler divergence* $$q(M^*) = \min_{q(M)}\operatorname{KL}\left({q(M)||P(D\;|\;M)}\right)$$ where $$\operatorname{KL}(p\mid q) = H(q)-H(q\;|\;P) = \sum_\theta p\log p - \sum_\theta p\log q$$

### MCMC

This MCMC occurs in the parameter space for the SBM (compared to sampling graphs).

**Greedy algorithm/variation:**

1.  Check all $k\in\left\{{1,\cdots, N}\right\}$.

2.  Select the one that reduces $-\log L$ the most.

3.  Perform the best change.

4.  Repeat until no improvement is possible.

The problem with the greedy algorithm is that the proposal is simple, but the algorithm is prone to getting stuck within a local optimum.

**Metropolis MCMC:**

1.  Start in $\boldsymbol{ b} = \boldsymbol{b}(t=0)$.

2.  Propose some $\boldsymbol{b}' = T(\boldsymbol{b})$ by flipping one randomly chosen $b_{k}$.

3.  Accept / reject depending on $-\Delta \log (\mathcal L)$.

4.  Repeat.

where the proposal satisfies:

- $\boldsymbol{\boldsymbol{b}}\in$ set of partitions $\implies \boldsymbol{\boldsymbol{b}}=T(\boldsymbol{\boldsymbol{b}})$

- Ergodicity

- Detailed balance ($\pi\left({b\to b'}\right)=\pi\left({b'\to b}\right)=\frac{1}{N}$)

and where the acceptance is such that: $$\begin{aligned}
    A\left({b\to b'}\right) &= \min\left({1,\frac{\mathcal{L}\left({b'}\right)}{\mathcal{L}\left({b}\right)}}\right)\qquad \mathcal{L}\left({b}\right) = P\left({D\;|\;M}\right)\\
    &=\min\left({1,\exp\left({-\Delta\log\mathcal{L}}\right)}\right)
\end{aligned}$$

Therefore we will be sampling partitions $\boldsymbol{\boldsymbol{b}}$ according to the likelihood $\mathcal L(\boldsymbol{\boldsymbol{b}})$ which allows us to do statistics over “plausible" graphs with a good likelihood.

It is also natural to add the inverse temperature $\beta$, $$A\left({b\to b'}\right) = \begin{cases}
    1 & -\Delta\log\mathcal{L}<0\\
    \exp\left({\beta\Delta\log\mathcal{L}}\right) & -\Delta\log\mathcal{L}>0
\end{cases}$$ so the Metropolis method will sometimes accept a worse configuration, which allows the algorithm to escape local optima.

Note that $\beta=0$ is a random search through the parameter space (yields bad partitions). If $\beta=1$ then we are sampling from $\mathcal L$ as per the previous case. Finally if $\beta\to \infty$ then we will only accept if we improve, which is similar to the greedy approach.

## Local Minima Problem

When we are optimising over local minima, the minus log likelihood will have many local minima (dips and valleys). So there are many opportunities for local moves to get stuck. Hence, the *greedy* algorithm will likely get stuck at some local minima close to the initial. Therefore, convergence of the greedy or $\beta\to\infty$ methods depends on the initial $\theta(t=0), b(t=0)$.

MCMC-metropolis can jump over barriers. The probability to jump over a barrier of height $-\Delta\log\mathcal{L}$ is $\exp\left({-\beta\Delta\log}\right)$. A power idea for optimisation is **simulated annealing**, where we start with $\beta=0$, then move to $\beta\to \infty$ slowly.

<figure id="fig:simAnn">
<p><strong>Figure unavailable in supplied archive: imgs/simAnn.png</strong></p>
<figcaption>Simulated Annealing</figcaption>
</figure>
