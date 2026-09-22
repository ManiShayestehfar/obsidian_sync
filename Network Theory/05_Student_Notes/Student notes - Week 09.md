---
type: student-source
week: 9
status: supplementary-unverified-source
---

# Student notes - Week 09

[[Student notes index]] · [[Corrections and caveats]]

> [!warning] Secondary source
> Format conversion of Jeny Yuan’s supplied LaTeX notes (identified by the user as last year’s notes). Mathematical errors in the source are retained here, not endorsed. Use the checked 2026 lecture notes for Weeks 1–7. No 2026 lecture PDF or tutorial for this week was supplied. Missing figures are labelled. Formatting has been normalised; the original TeX is retained in `06_Sources/student_notes_original.tex`.
>
> **Specific correction:** The Bayesian signs and graph-inference normaliser require correction; see [[Corrections and caveats]] before using the Ising reconstruction formulas.

# Network Reconstruction

Idea: given an incomplete observation (data) on a network $G$, the goal is to reconstruct $G$, ie. what are the links and nodes of $G$?

For example

- Social networks: from some friendship links, predict unobserved future friendships – eg. recommendation systems.

- Product-Buyer bipartite network

- Protein-protein interactions – which protein interactions do we test experimentally, given limited information?

## General Approaches

### Heuristic Methods

Heuristic methods are based on experience and heuristic functions, so we can assume the observation have clustering $C>0$. We can predict that links between nodes with similar neighbours are more likely to occur because they increase the clustering.

### Inferential methods

Based on a generative process of the data $P(D\mid M)$ where $D$ is the data and $M$ is the model. Some possible settings are

- Random graph models define the probability of a graph given the model.

- Inference can happen using MCMC-Metropolis to sample / optimise models $M$ from $P(D\mid M)$ or $P(M\mid D)$ and also to sample $P(g\mid M)$. Sampled $g$’s are candidates for network reconstruction.

Note that in the community-detection problem, we have:

- Heuristic methods: finding a partition of the graph that maximises modularity.

- Inferential methods: stochastic block models - using the probability of observing edges in a certain graph to infer the structure of the graph.

- Note that modularity maximisation will overfit and find communities even in random graph models like Poisson RG which are entirely noise.

## Link Prediction

Given the *data* $\ell_1,...,\ell_L$ links between $N$ nodes, which build an observed network $g_o$.

The *goal* is to predict “missing" links $\ell_{L+1},\dots, \ell_{L+L^*}$ between the same $N$ nodes of an underlying network $g$ (where $g_0\subseteq g$).

The *method* is to rank all $\frac{N(N-1)}{2}-L$ non-links according to their probabilities of being “real" links.

### Heuristic methods

Let $\Gamma(i)$ be the set of neighbours of node $i$ in the observed network $g_0$. Denote $|\Gamma(i)|$, the observed degree of node $i$, as it’s length ($\left|{\Gamma(i)}\right|\equiv z_i$).

A potential link $(i,j)$ is ranked higher if the neighbours of nodes $i$ and the neighbours of node $j$ have a large intersection $|\Gamma(i)\cap \Gamma(j)|$ is big.

1.  Jaccard Coefficient: $$J_{i,j} = \frac{|\Gamma(i)\cap \Gamma(j)|}{|\Gamma(i)\cup \Gamma(j)|}\,.$$ The Jaccard coefficient is proportional to the fraction of common neighbours (there is a normalisation).

2.  Resource Allocation Index $$\mathrm{RA}_{ij} = \sum_{k\in \Gamma(i)\cap\Gamma(j)} \frac{1}{\left|{\Gamma(k)}\right|}$$ Here, neighbour contribution is inversely proportional to degree. Its like saying Jenny is more likely to be Friends with Mitch vs Taylor Swift.

3.  Adamic-Adar index: $$\mathrm{AA}_{ij} = \sum_{k\in \Gamma(i)\cap\Gamma(j)} \frac{1}{\log{\left|{\Gamma(k)}\right|}}$$ There is a smaller penalty for degree in view of higher degree variability

4.  Preferential-attachment score: $$\mathrm{PA}_{ij}=|\Gamma(i)||\Gamma(j)|$$ Here, there is a preference for hubs.

## Inferential Methods

1.  Choose a random graph model $M$ with parameters $\Theta$. For example, exponential random graph model, SBM, etc. which define $P(G\mid M,\Theta)$

2.  We then fit the model $M$ to data $D$ to estimate the best parameters $\Theta$, eg. the maximum likelihood values $\Theta^* = \operatorname{argmax}_{\Theta}P(D\mid M,\Theta)$.

3.  We can sample $\{g_t\}$ from $P(g\mid M,\theta^*)$ and compute links $$p_{ij}=P(\ell=(i,j))=\sum_{g\in\{g_t\}}\frac{\delta(A_{ij}=1)}{|\{g_i\}|}$$

For example, SBM as RG, $\Theta = \boldsymbol{b}$ and $P_{ij} = P\left({\ell=\left({i,j}\right)}\right) P_{rs}$ with $\boldsymbol{b}(i) =r,b(j) = s$

## Comparing Methods

1.  Start from $g$, and remove a number (e.g. 10%) of links to obtain $g_o$.

2.  Apply (various) link prediction methods to $g_o$.

3.  Evaluate the methods based on comparison with the ground-truth removed links, using the AUC. (Area under the Curve score)

4.  Average over different realisations of removed links.

To predicted links, we can calculate

- True positive rate: $\operatorname{TPR}=\frac{\mathrm{TP}}{\mathrm{TL}}$

- False positive rate: $\operatorname{FPR} = \frac{\mathrm{FP}}{\mathrm{FL}}$

We try to achieve $\operatorname{TPR}=1$, and $\operatorname{FPR}=0$. A $\operatorname{FPR}=1$ can occur if we accept all possible links. As I move my threshold for accepting a link, I move from $(0,0)$ to $(1,1)$ in $\operatorname{FPR}-\operatorname{TPR}$ curve. This is the ROC plot for binary prediction.

If we consider the area under the ROC curve, then that is the AUC value. If the method is perfect, it will have area $1$. Note that if we randomly pick nodes, we will move on the diagonal $y=x$, and so AUC will be $1/2$.

Below are some AUCs for heuristic models:

- JD 0.714

- AA 0.714

- RA 0.711

- BA 0.552

Now we consider the SBM approach:

- Fix $B$, and compute $\vec{b}^*$, and calculate AUC.

- We can use this to infer the optimal $B$ by maximising AUC (can easily confirm this by generating SBM with known $B$ and calculate the AUC for different $B$’s)

## Bayesian Approach

Bayesian inference of $B$: $$P(M\mid D)=\frac{P(D\mid M)P(M)}{P(D)}$$ if we take the log of both sides $$\log P(M\mid D) = \log P(D\mid M) + \log P(M) + \log P(D)$$ where $\log P(M)$ are the log priors and $\log P(D)$ are constants.

Recall from Week 7 that we aimed to minimise $$-\log P\left({g}\right) = -\sum_{r\text{ and }s\geq r}^B \ell_{rs} \log(P_{rs}) +\left({g_{rs}-\ell_{rs}}\right)\log(1-P_{rs})$$

Since we are in a Bayesian framework, we need to choose a prior, ie. $P(M)\equiv P(\boldsymbol{b})$. We will use a noninformative (uniform) prior.

We use $$P(\boldsymbol{b}) = P(\boldsymbol{b}\mid B)P(B)$$ where $B$ is a hyperprior. In our case, we can use $P(B)=1/N$ as a flat prior as $B$ the number of blocks can be $1,2,\dots, N$. The allocation over $B$ must be $$p(\boldsymbol b\mid B) = \text{number of different allocations we have} = \frac{1}{B! \genfrac\{\}{0pt}{}{N}{B}}$$ This would account for the increasing complexity of a model with a larger $B$. Then taking the log we have $$\log P(\boldsymbol{\boldsymbol{b}}\mid D) = - \log P(D\mid \boldsymbol{\boldsymbol{b}}) + \log B! + \log \genfrac\{\}{0pt}{}{N}{B} + \log N + \mathrm{constant}$$

When we add the $-\log P(D\mid \boldsymbol{b}^*)$ with $\boldsymbol{b}^*$, obtained using the greedy algorithm with $B$. **CHECK** There is a correction factor.

## Reconstruction from Node Activity

Consider the *data* of node attributes $s_i$ for $i=1,...,N$ at different times $t=1,...,T$. The simplest case of which is where $s\in[-1,1]$. We assume that nodes influence each other through a network $g$ such that $s_i=s_j$ is more likely if $A_{ij}=1$.

### Heuristic Methods

The idea of the methods is as such:

1.  Compute the pairwise “similarity" of $s_i(t)$ and $s_j(t)$.

2.  Threshold the similarity and predict $g$ as all links with similarity above the threshold.

3.  Some similarity measures we may look at are:

    - Pearson correlation

    - Mutual information

4.  An example of a threshold can be the prior guesses on numbers of edges, where we can compute the p-value of chance similarity. (**CHECK**)

### Inferential methods

Data: $\boldsymbol{\boldsymbol{s}}(t) =\left({s_1(t),\cdots,s_N(t)}\right)$ for $t=1,\cdots, T$ where $s_i(t)\in\left\{{-1,1}\right\}$. We consider $$P(D\mid M)=P(\boldsymbol{\boldsymbol{s}}\mid g)=Ae^{-E(\boldsymbol{\boldsymbol{s}})}$$ where $E(\boldsymbol{\boldsymbol{s}})=-\sum_{i<j}A_{ij}s_is_j$ is the Ising model. Then, $$-\log P(\boldsymbol{\boldsymbol{s}}\mid g) = E(\boldsymbol{\boldsymbol{s}})\implies \text{Maximum Likelihood}\equiv\min E(\boldsymbol{\boldsymbol{s}})$$

The heuristic approach is as such:

- Compute the Pearson correlation, assuming that $L=100$ is known.

The inferential approach is as such:

- Use the Ising model.

- Sample $g$’s from $P(\boldsymbol{\boldsymbol{s}}\mid \boldsymbol{\boldsymbol{g}})$ with fixed $L$ using MCMC Metropolis add/remove proposals.

- Then, average over multiple graphs by taking $g(t)$ for $t>t^*$.
