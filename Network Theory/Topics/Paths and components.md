---
tags: [data5441, ch01, foundations]
aliases: [Walks, Distance, Diameter, Connected components, BFS]
---
# Paths and components

> [!abstract] Summary
> Powers of $A$ count walks. Shortest paths give distances, the average distance and the diameter. Components say who can reach whom, and must be identified before averaging distances.
> Chapter: [[Ch01 Networks and high dimensions]]

> [!definition] Walk, path, cycle
> - A **walk** of length $r$ is a sequence $(v_0,\dots,v_r)$ with $A_{v_{k-1}v_k}=1$ for every $k$. Nodes and links may repeat.
> - A **path** is a walk with no repeated nodes.
> - A **cycle** is a closed walk of length at least $3$ with no repeated nodes except the first and last.

> [!definition] Distance, average distance, diameter
> The distance $d_{ij}$ is the length of a shortest path from $i$ to $j$. It is $0$ if $i=j$ and $\infty$ if no path exists. On a connected graph,
> $$\ell=\langle d\rangle=\frac{1}{N(N-1)}\sum_{i\neq j}d_{ij},\qquad D=\max_{i,j}d_{ij}\ \ (\text{diameter}).$$

> [!definition] Connected component
> A **connected component** is a maximal set of nodes that are pairwise joined by paths. A directed graph is **strongly** connected if directed paths exist in both directions between every pair. It is **weakly** connected if it is connected once directions are ignored.

> [!theorem] Adjacency powers count walks
> For every integer $r\ge0$, $(A^r)_{ij}$ is the number of walks of length $r$ from $i$ to $j$.

> [!proof]-
> Induction on $r$. For $r=0$, $A^0=I$ counts the walk of length zero.
> Assume the claim holds for $r$. Then $(A^{r+1})_{ij}=\sum_v (A^r)_{iv}A_{vj}$. Every walk of length $r+1$ from $i$ to $j$ has a unique penultimate node $v$ adjacent to $j$, and removing its last step leaves a walk of length $r$ from $i$ to $v$. The sum therefore counts each such walk exactly once. $\square$
>
> These are walks, not paths: $(A^2)_{ii}=z_i$ counts the walks $i\to j\to i$.

> [!algorithm] Breadth-first search (BFS)
> Start at a source $s$ with distance $0$. Visit all neighbours (distance $1$), then all their unvisited neighbours (distance $2$), and so on, layer by layer.
> The first time a node is discovered, its layer is its distance from $s$. One search costs $O(N+L)$ with adjacency lists. All-pairs distances therefore cost $O(N(N+L))$.

> [!proposition] Trees
> A connected graph with $N$ nodes has $L\ge N-1$. It is a tree (connected and acyclic) iff $L=N-1$. In a tree, every pair of nodes is joined by a unique path.

## Lattice reference results (tutorial)

> [!example] $M\times M$ square lattice
> - **4 neighbours** (no diagonals): $d$ is the Manhattan distance, so $D=2(M-1)$. There are no triangles, so $C=0$.
> - **8 neighbours** (with diagonals): $L=2(M-1)(2M-1)$, $d((a,b),(c,d))=\max(|a-c|,|b-d|)$ and $D=M-1$.
>
> On a lattice, distances grow like a power of $N$ ($\ell\propto\sqrt N$ in 2D). In random graphs they grow like $\log N$; see [[Small-world networks]].

> [!remark] Giant component vs connectivity
> A **giant component** is one containing a positive fraction of the nodes as $N\to\infty$. A graph can have a giant component without being connected. When reporting $\ell$ or $D$ for a disconnected graph, say that they are computed inside the largest component.

> [!code]- NetworkX
> ```python
> Gc = G.subgraph(max(nx.connected_components(G), key=len))
> nx.diameter(Gc); nx.average_shortest_path_length(Gc)
> nx.shortest_path_length(G, source=1, target=8)
> ```

> [!selftest]- Self-test
> 1. What does $(A^3)_{ii}$ count? — Closed walks of length $3$ from $i$, i.e. $2T_i$ (each triangle at $i$ in two orientations).
> 2. Why is $\ell$ undefined for a disconnected graph without a convention? — Some $d_{ij}=\infty$.

---
Related: [[Graphs and representations]] · [[Clustering]] · [[Small-world networks]]
