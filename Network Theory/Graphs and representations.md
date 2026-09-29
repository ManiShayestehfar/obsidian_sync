---
tags: [foundations]
---

# Graphs and representations

A network models which entities interact. Choosing vertices, edges, direction and weights is part of the modelling problem: changing that choice changes what the statistics mean.

> [!definition] Graph conventions
> A finite **simple undirected graph** is $G=(V,E)$, with $E\subseteq\{\{i,j\}:i,j\in V,\ i\ne j\}$. Write $N=|V|$, $L=|E|$ and $Y=\binom N2$. Its adjacency matrix has $A_{ij}=1$ for an edge and zero otherwise; $A=A^\top$ and $A_{ii}=0$.
>
> The neighbours of $i$ are $\Gamma(i)=\{j:A_{ij}=1\}$ and its degree is $k_i=|\Gamma(i)|=\sum_jA_{ij}$. Lectures also write $z_i$ for degree. Angle brackets denote a uniform vertex average: $\langle k^r\rangle=N^{-1}\sum_i k_i^r$. Model expectations use $\mathbb E$.

> [!theorem] Handshaking identity
> $\sum_i k_i=2L$, so $\langle k\rangle=2L/N$ for $N>0$. The number of odd-degree vertices is even.

> [!proof]
> Each undirected edge contributes one to the degree of each of its two endpoints. Taking the resulting even sum modulo two proves the parity statement. For a multigraph, count a loop twice in the degree.

## Representations and variants

| Representation | Storage | Useful for |
| --- | --- | --- |
| Dense adjacency matrix | $O(N^2)$ | Linear algebra; constant-time adjacency lookup |
| Adjacency lists | $O(N+L)$ | Traversal of sparse graphs |
| Edge list | $O(L)$ plus the vertex set | Loading data; processing edges |

An edge list alone does not record isolated vertices. Node order must be fixed when translating between a graph and an array.

For a **directed** graph we use $A_{ij}=1$ for $i\to j$: row sums are out-degrees and column sums are in-degrees. Some lectures and Newman use the transposed convention. For **weighted** graphs, strength $s_i=\sum_jw_{ij}$ differs from degree. A **multigraph** allows repeated edges; a simple graph does not. A **bipartite** graph has two vertex classes and edges only between classes. A **hypergraph** allows an edge to contain more than two vertices.

A coauthorship dataset may be an author–paper bipartite graph or a hypergraph with one hyperedge per paper. Its author projection joins authors who share a paper, turning a multi-author paper into a clique. Projection therefore creates triangles and loses information about which interactions occurred together. An Erdős number is distance from Paul Erdős in that author projection, not distance in the bipartite author–paper graph.

A complete graph has all $Y$ possible edges. A $k$-regular graph has every degree equal to $k$. A tree is connected and acyclic; a forest is acyclic but need not be connected. A lattice imposes a geometric neighbourhood rule.

> [!definition] Sparsity
> For a graph sequence, bounded mean degree implies $L=O(N)$ and density $L/Y=O(1/N)$. This is the sparse regime mostly used in the course. More broadly, vanishing density only requires $L=o(N^2)$ and does not force bounded mean degree. Dense models often keep a positive limiting density.

> [!code] Build a graph and preserve node order
> ```python
> import networkx as nx
> import numpy as np
>
> G = nx.Graph()
> G.add_nodes_from(range(6))  # include vertices even if isolated
> G.add_edges_from([(0, 1), (1, 2), (2, 0), (2, 3)])
> assert not G.is_directed() and not G.is_multigraph()
> assert nx.number_of_selfloops(G) == 0
> nodes = list(G)
> A = nx.to_numpy_array(G, nodelist=nodes, weight=None, dtype=int)
> degrees = np.array([G.degree(v) for v in nodes])
> assert degrees.sum() == 2 * G.number_of_edges()
> ```

A `Graph` merges duplicated edges, including repeated reverse pairs. Converting a directed or weighted dataset to this form is a substantive modelling decision. Use [[Paths and components]] and [[Clustering]] to describe the resulting topology.

> [!reference]- Sources
> Lecture Week 1; Jenny’s notes Week 1. Newman (2018), §§6.1–6.10 and 8.3. Tutorial 1, graph construction and dataset examples.
