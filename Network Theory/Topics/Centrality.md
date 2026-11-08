---
tags: [data5441, ch02, foundations]
aliases: [Centrality measures, Betweenness, Eigenvector centrality, PageRank, Katz]
---
# Centrality

> [!abstract] Summary
> "Importance" has several meanings, and each centrality encodes one mechanism: many contacts (degree), short routes (closeness), brokerage (betweenness), or importance inherited from important neighbours (eigenvector, Katz, PageRank). Choose the measure that matches the question.
> Chapter: [[Ch02 Centrality measures]]

## Local and path-based measures

### Degree Centrality

> [!definition] Degree centrality
> The degree $z_i$, often normalised as $z_i/(N-1)$. It identifies nodes with the most direct contacts ("students with the most friends").

*Limitation:* Treats each neighbour equally.

### Betweenness Centrality

> [!definition] Betweenness centrality
> Let $\sigma_{st}$ be the number of shortest paths from $s$ to $t$, and $\sigma_{st}(i)$ the number of those that pass through $i$ as an internal node. Then
> $$b_i=\sum_{s<t,\ s,t\ne i}\frac{\sigma_{st}(i)}{\sigma_{st}},\qquad \tilde b_i=\frac{b_i}{\binom{N-1}{2}}\in[0,1].$$
> It identifies **brokers or bridges**, e.g. students who connect different school years.

*Limitations:* 
1. High betweenness does not automatically mean removing the node disconnects the graph: alternative routes may exist, but be longer.
2. The measure assumes that the process of interest follows shortest paths.


![[centrality-comparison.png|650]]


## Spectral (recursive) measures

All three methods let **a node inherit importance from other nodes**. For directed graphs, use $A_{ij}=1$ for an edge $j\to i$, so $(Ax)_i$ collects incoming scores; $\mathbf1$ denotes the all-ones vector.

### Eigenvector Centrality

**Idea:** A node is important when its neighbours are important (unlike degree, which counts all neighbours equally).

1. **Define importance recursively:** $x_i\propto\sum_j A_{ij}x_j$. With a common proportionality constant,
   $$\boxed{x_i=\frac1{\lambda_1}\sum_jA_{ij}x_j\quad\Longleftrightarrow\quad Ax=\lambda_1x.}$$
   Choose the **principal (Perron) eigenvector**, $x=v_1\ge0$, for $\lambda_1=\rho(A)$. Its scale is arbitrary.
2. **Why this eigenvector?** Propagating scores gives $x(t+1)=Ax(t)$, hence $x(t)=A^tx(0)$. If $A$ is symmetric, expand $x(0)=\sum_k a_kv_k$ to obtain
   $$\frac{x(t)}{\lambda_1^t}=a_1v_1+\sum_{k\ge2}a_k\left(\frac{\lambda_k}{\lambda_1}\right)^tv_k.$$
   When $a_1\ne0$ and $|\lambda_k|<\lambda_1$ for $k\ge2$, the direction tends to $v_1$.

> [!theorem] Perron–Frobenius — exam essentials
> For a **connected undirected** graph with $N\ge2$, $\lambda_1>0$ is simple and has a strictly positive eigenvector, unique up to scale; $\min_i z_i\le\lambda_1\le\max_i z_i$. A connected **bipartite** graph also has eigenvalue $-\lambda_1$, so ordinary power iteration may oscillate (using $A+I$ resolves this). Directed graphs require strong connectivity for the corresponding strict-positivity guarantee.

**Limitations:** A node passes its full score to every outgoing neighbour; some nodes in directed graphs can receive score $0$. These issues motivate Katz and PageRank.

### Katz Centrality

**Idea:** Eigenvector centrality can give zero scores in directed graphs. Give every node an intrinsic **baseline** $\beta>0$.

1. **Add a source term** ($\alpha\ge0$ controls neighbour influence):
   $$x(t+1)=\alpha Ax(t)+\beta\mathbf1.$$
2. **Solve for equilibrium** $x(t+1)=x(t)=x$:
   $$x=\alpha Ax+\beta\mathbf1\quad\Longrightarrow\quad\boxed{x=\beta(I-\alpha A)^{-1}\mathbf1.}$$
   Only relative scores matter, so $\beta=1$ is a common choice.
3. **Interpret and constrain $\alpha$:** For $0\le\alpha<1/\rho(A)$ (when $\rho(A)>0$),
   $$\boxed{x=\beta\sum_{k=0}^{\infty}\alpha^kA^k\mathbf1.}$$
   Katz counts walks arriving at each node, weighting length-$k$ walks by $\alpha^k$; $k=0$ supplies the baseline. Small $\alpha$ emphasises direct connections; larger $\alpha$ gives longer walks more influence. If $\rho(A)=0$, the finite series is valid for any finite $\alpha$.

**Limitation:** Katz prevents zero scores, but still passes the *full* score along every outgoing link.

### PageRank

**Idea:** A node should **share** its importance among outgoing links rather than transmit its full score to each recipient.

1. **Normalise each outgoing contribution.** Let $z_j^{\mathrm{out}}$ be node $j$'s out-degree. The course update is
   $$\boxed{x_i(t+1)=\alpha\sum_jA_{ij}\frac{x_j(t)}{z_j^{\mathrm{out}}}+\beta.}$$
   So an incoming link from a node with many outgoing links contributes less.
2. **Write the fixed point.** If all out-degrees are positive, set $D_{\mathrm{out}}=\operatorname{diag}(z_j^{\mathrm{out}})$ and $P=AD_{\mathrm{out}}^{-1}$; each column of $P$ sums to $1$. Then, for $0\le\alpha<1$,
   $$x=\alpha Px+\beta\mathbf1\quad\Longrightarrow\quad\boxed{x=\beta(I-\alpha P)^{-1}\mathbf1.}$$
3. **Random-surfer interpretation.** With probability $\alpha$ (commonly $0.85$), follow a random outgoing link; otherwise, teleport uniformly. For a probability vector $p$,
   $$\boxed{p(t+1)=\alpha Pp(t)+\frac{1-\alpha}{N}\mathbf1.}$$
   The stationary probability $p_i$ is node $i$'s PageRank. The course's arbitrary $\beta>0$ gives the **same ranking after normalisation**; the probability form uses $\beta=(1-\alpha)/N$.

> [!warning] Dangling nodes
> If $z_j^{\mathrm{out}}=0$, the denominator is undefined. Standard PageRank replaces that node's transition column with a teleportation distribution (e.g. uniform), restoring a valid stochastic matrix.

**Remember:** **Eigenvector:** important neighbours. **Katz:** important neighbours **+ baseline**. **PageRank:** baseline **+ out-degree-normalised contributions**.

> [!code]- NetworkX (tutorial 2)
> ```python
> nx.degree_centrality(G); nx.closeness_centrality(G)
> nx.betweenness_centrality(G)                 # normalised by default
> nx.eigenvector_centrality(G); nx.katz_centrality_numpy(G, alpha=0.1)
> nx.pagerank(G, alpha=0.85)
> ```

> [!selftest]- Self-test
> 4. Which centrality identifies bridges between communities? — Betweenness.
> 5. What is the condition on $\alpha$ for Katz centrality? — $\alpha<1/\lambda_1$.
> 6. Why can power iteration fail on a bipartite graph? — Because $-\lambda_1$ is also an eigenvalue, the iterates oscillate.

---
Related: [[Graphs and representations]] · [[Paths and components]] · [[Spectral graph theory]]
