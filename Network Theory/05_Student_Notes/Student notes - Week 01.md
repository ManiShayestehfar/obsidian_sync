---
type: student-source
week: 1
status: supplementary-unverified-source
---

# Student notes - Week 01

[[Student notes index]] · [[Corrections and caveats]]

> [!warning] Secondary source
> Format conversion of Jeny Yuan’s supplied LaTeX notes (identified by the user as last year’s notes). Mathematical errors in the source are retained here, not endorsed. Use the checked 2026 lecture notes for Weeks 1–7. Missing figures are labelled. Formatting has been normalised; the original TeX is retained in `06_Sources/student_notes_original.tex`.

# Introduction

**Definition 1**. Let $\mathcal N$ be a set $n=1,2,...,N=|\mathcal N|$ be the **nodes** or ***vertices***. Let $\mathcal L$ be a set $\ell=1,2,...,L=|\mathcal L|$ be **links** or ***edges***. If all links $\ell\in\mathcal L$ are such that $\ell=\{n_j,n_k\}$, with $n_j, n_k\subset \mathcal N$, we say $\mathcal N$ and $\mathcal L$ build a **network** or simple ***graph***. Networks can be represented *graphically*, with an **adjacency matrix**, or with a **list of links**. With $N$ nodes, there can exist $2^{\frac{N(N-1)}{2}}$ networks.

Some examples of networks:

- **Lattice**: Start with points in $\mathbb Z^d$ as nodes, and link all nodes within a lattice distance $r$.

- **Trees**: Networks with no loops (single path between any two nodes).

- **Complete graph**: All-to-all connections.

Basic concepts and network measurements:

- **Local** measures: nodes, edges, or values around them.

- **Global** measures: the network as a whole.

- **Path**: any sequence of nodes such that there is a link between consecutive nodes.

- **Length** of a path: the number of links in the path.

- **Simple path**: no repeated nodes in the path.

- **Shortest (geodesic) path**: the smallest distance for which there is a path.

- **Closed path**: path that finishes at the starting node.

- **Neighbourhood** of node $i$: all nodes $j$ such that $A_{ij}=1$.

- **Path distance**: to characterise the closeness of a node to others.

  - Local measure: $d_i=\langle d_{ij}\rangle_j\equiv\frac{1}{N-1}\sum_{k=1,\ k\neq i}^Nd_{ik}$

  - Global measure: $d=\langle d_{i}\rangle_i\equiv\frac{1}{N}\sum_{i=1}^Nd_{i}$

- **Diameter**: $d_{diam}=\max_{\{i,j\}}\{d_{ij}\}$

- **Components**: all nodes for which $d_{ij}<\infty$ defines a connected component.

- **Degree** of node $i$:

  - Local measure: $z_i=\sum_{j=1}^N A_{ij}\equiv$ number of neighbours of node $i$.

  - Global measure: $\langle z_i\rangle_i\equiv \frac{1}{N}\sum_{i=1}z_i=\frac{2L}{N}$ where $L=$ number of links in the network.

- **Sparse** networks: a network where most $A_{ij}=0$, more precisely $\langle z\rangle\xrightarrow[N\rightarrow\infty]{}\text{constant}$.

- **Clustering coefficient**:

  - Local clustering: $C_i\equiv \frac{\text{Number of neighbours of $i$ that are connected}}{\text{Number of pairs of neighbours}}=\frac{2\times\text{Number of 'triangles' involving $i$}}{z_i(z_i-1)}$

  - Global clustering:

    - $\langle C_i\rangle_i=\frac{1}{N}\sum_{i=1}^NC_i$

    - $C_{net}\equiv \frac{\text{Number of closed paths of length $r=3$}}{\text{Number of simple paths of length $r=2$}} = \frac{6\times\text{Numbers of triangles in the network}}{\text{Number of simple paths of length $r=2$}}$
