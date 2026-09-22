---
type: student-source
week: 8
status: supplementary-unverified-source
---

# Student notes - Week 08

[[Student notes index]] · [[Corrections and caveats]]

> [!warning] Secondary source
> Format conversion of Jeny Yuan’s supplied LaTeX notes (identified by the user as last year’s notes). Mathematical errors in the source are retained here, not endorsed. Use the checked 2026 lecture notes for Weeks 1–7. No 2026 lecture PDF or tutorial for this week was supplied. Missing figures are labelled. Formatting has been normalised; the original TeX is retained in `06_Sources/student_notes_original.tex`.

# Community Detection

**Communities** are assortative mesoscale structures with more links within the group than across different groups.

Community detection is the problem of identifying the communities, or to partition the network based on only the graph. Typically, our number of communities are unknown and need to be inferred from the graph. This is challenging because the number of partitions of $N$ nodes in $B$ groups grows quickly. Naively, we might think: $$\mathrm{Naively:}\quad \sum_{B=1}^N \frac{B^N}{B!} \,,$$ but this is **not** correct because this allows for empty partitions. Actually, we have $$\operatorname{Be}(N) = \sum_{B=1}^N \genfrac\{\}{0pt}{}{N}{B}$$ where $\operatorname{Be}$ is the **Bell number**, $\genfrac\{\}{0pt}{}{N}{B}$ is the **Stirling number** of the second kind. The Bell number is super exponential, but slower than a factorial. We want a solution that scales like polynomials in $N$.

## Graph Partitioning/Mode Clustering

We aim to minimise the "cut size", i.e. the number of links between communities that you need to cut before these two communities are separated.

To simplify, consider the case where $B=2$, and $N_1$ and $N_2$ are known where $N_1+N_2=N$. The number of possible partitions is then $\binom{N}{N_1}\sim e^N$, assuming $P\neq NP$, such that we do not have a polynomial algorithm.

The **Kernighan-Lin algorithm** for graph bisection is as such:

1.  Initialisation: have any partition with $B=2$ and the given $N_1$ and $N_2$.

2.  For all pairs of nodes, identify the node swap that *minimises* the cut size (or the one with the least increase).

3.  Perform the swap and repeat step 2, now excluding the pairs already swapped.

4.  Optional: check the cut size through steps 2-3 and pick the one with minimal cut size.

5.  Repeat steps 2-4 until no improvement.

The *efficiency* of this algorithm is $O(N^2)$ (polynomial in $N$). However, there is no possible simple extension to find $B$, as the cut size for $B=1$ or $N_1=0$ is $0$. So we can do this hierarchically, but this is a different question to finding the best $B$.

## Modularity Maximisation Methods

We would like to find $B$, with the community allocation $b_i\subset\{\alpha_1,...,\alpha_B\}$ for $i=1,...,N$ nodes. The idea is as such:

1.  We take the links within the same community and sum $$L_c = \sum_{\mathrm{edges\  }(i,j)} \delta(b_i =b_j) = \frac12 \sum_{i=1}^N \sum_{j=1}^N A_{i,j} \delta(b_i = b_j)$$ where $\delta(x)=\begin{cases} 1 & \text{if $x$ occurs } \\ 0 & \text{otherwise}\end{cases}$

2.  We want the expected number of such links by chance. The probability of a random $(i,j)$ link should be $P_{i,j} = \frac{z_iz_j}{2L}$. Then the random expectation is $$L_R = \frac12 \sum_{i=1}^N \sum_{j=1}^N\ \frac{z_i z_j}{2L} \delta(b_i = b_j)$$ The quantity to be maximised, the *modularity* $Q$, is $$Q=\frac{L_C-L_R}{L}=\frac{1}{2L}\sum_{i=1}^N \sum_{j=1}^N \left({A_{i,j}-\frac{z_iz_j}{2L}}\right) \delta(b_i = b_j)$$ We can see that: $$\begin{aligned}
            B=1 &\implies L_C=L_R\implies Q=0 \\ 
            B=N &\implies \delta(b_i=b_j)=1\iff i=j\implies A_{ij}=0\implies L_C=0\implies Q\leq 0
        
    \end{aligned}$$ Hence, for $1<B<N$, it is likely that $Q>0$, so we choose $B$ and the partition $\boldsymbol{b}$ that maximises $Q$.

We can use the greedy algorithm to change a partition $\boldsymbol{b}$ systematically, and then vary it to maximise the modularity of the clustering.

- **Agglomerative methods:** take two partitions and combine them into one.

- **Divisive methods:** take one partition and divide into two.

Consider an example of a greedy *agglomerative* or *divisive* method:

|                Method                 | Agglomerative | Divisive  |
|:-------------------------------------:|:-------------:|:---------:|
|            1\. Start with             |     $B=N$     |   $B=1$   |
|        2\. Check all possible         |    merges     | divisions |
| 3\. Choose the one that maximises $Q$ |               |           |
|         4\. Repeat 2-3 until          |     $B=1$     |   $B=N$   |

Select $B$ and $\boldsymbol{b}$ that maximises $Q$.

The computational cost involves looking at pairs of block assignments, so it is $B^2\sim O(N^2)$, i.e. polynomial in $N$, which is not so bad.

**Remark 1**. The efficiency of the greedy methods be improved to $O(n(\log n)^2)$ by testing possible merges only between connected communities. We will need to store the links between communities during the algorithm, forming a multi-graph type structures with communities as nodes.

There are also other optimisation methods applicable to modularity, such as the *Louvain method*.

There are different variations of modularity, for example, $z$-modularity, and others.

## Other Community Detection Methods

### Centrality-Based Approaches

The idea is to identify “bridging edges" and cut them in order. For example, the **Girvan-Newmann method** uses between-ness centrality to identify the nodes to cut then tracks modularity to select communities.

### Dynamical Approaches

An example is **label propagation**:

- Each node starts in its own community $B=N$.

- At each step, each node adopts the community of most neighbours or one by chance.

Another example if **infomap** which is based on transfer operators.

### Spectral Methods

Based on the eigenvalues of the Graph Laplacian given by .

An example is the **Graph Laplacian**: $$\mathbb{L} = \mathbb{D-A}$$ where $\mathbb D = \operatorname{diag}(z_1,\dots, z_n)$ is a diagonal matrix with the node degrees along the diagonal.

Consider $A$ with $B$ components that are completely disconnected. Then the graph Laplacian $\mathbb L$ is block diagonal with the structure $$\mathbb L = 
\begin{bmatrix}
    \mathbb L_1 & 0 & \cdots & 0 \\ 0 & \mathbb L_2 & \cdots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \cdots & \mathbb L_B \,.
\end{bmatrix}$$ where there are $B$ eigenvectors that each correspond to $\mathbb{L}_1,...,\mathbb{L}_B$: $$\boldsymbol{\boldsymbol{v}}_1=
\begin{pmatrix}
    c_1 \\ c_1 \\ \vdots \\ c_1 \\ 0 \\ 0 \\ 0
\end{pmatrix}, 
\quad \boldsymbol{\boldsymbol{v}}_2=
\begin{pmatrix}
    0 \\ \vdots \\ 0 \\ c_2 \\ c_2 \\ 0 \\ 0
\end{pmatrix}, 
\quad ...\quad, \quad \boldsymbol{\boldsymbol{v}}_B =
\begin{pmatrix}
    0 \\ 0 \\ \vdots \\ 0 \\ c_B \\ c_B \\ c_B
\end{pmatrix}$$

If we compute the eigenvalues and eigenvectors of the matrix we will see the vectors are of this format, and this will produce a community assignment for the notes. We construct an $N\times B$ matrix which is given by $$\begin{bmatrix}
    \boldsymbol{v_1} & \boldsymbol{v_2} & \cdots & \boldsymbol{v_B} 
\end{bmatrix}$$ and the $i$-th column corresponds to the nodes in community $i$.

Now consider a small perturbation of the disconnected case, where we modify $\mathbb{L}$ by adding in random “one"s (sparse) in areas off the block diagonals. This corresponds to random links between communities. Thomas section: *Under this small perturbation, the eigenvalues should not move enough to coalesce with another one and become multiple, see Perturbation Theory for Linear Operators \[Kato\] Moreover, the corresponding normalised eigenvectors are only slightly shifted.*

- Choose $B$ from the spectral gap, i.e. $\lambda$ increases sharply.

- Take the $B$ eigenvectors associated to $\lambda_1,\cdots,\lambda_B$.

- Construct the $B\times N$ matrix.

- Then we can cluster the nodes in a $B$-dimensional Euclidean space, via $k$-means or some other algorithm. The cluster associated to the node is the community associated with this node.

## Which Method is the Best / Should be Used?

This is not a mathematically well defined problem. However there are two considerations in community detection that we need to take into account

1.  Find “best" partitions, or assortative mesoscale structures that we know exist.

2.  The more ambitious task is to decide whether community structures exist at all, within the graph. For example, is the clustering stronger than what is expected by chance. (Is the signal that we find strong enough?)

Question: why is modularity maximisation unable to identify that a Poisson random graph should not have any clusters. Recall that modularity is introduced as the expected number of edges within clusters minus the number you expect by random chance. Why does modularity maximisation find $\sqrt N$ communities?

The modularity maximisation method does not account for the fact that the number of possible partitions rises super exponentially. When maximising, we are looking over a very huge space with a big fluctuation, so it is expected that under some partition within the space with a high modularity. We need to control for the probability of the partition. The function makes sense, but when optimising over a large space, it breaks down.

- Modularity maximisation and other methods, eg. label propogation find communities even in Poisson random graphs (where there should not be any communities) because they don’t control for fluctuations of $Q$ over the space of possible partitions.

- They can find the best partition, even with noise, if there is a strong belief that the assortative communities are a dominant feature of the network. If we do not know if the network has these communities, then applying these methods blindly can result in detecting networks that do not exist and only appear due to noise.

- Methods based on statistical inference are required for problems I and II.
