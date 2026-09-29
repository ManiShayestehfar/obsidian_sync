---
tags: [foundations]
---

# Paths and components

> [!definition] Walks, paths and distance
> A **walk** of length $r$ is a sequence $(v_0,\ldots,v_r)$ with adjacent consecutive vertices; vertices and edges may repeat. A **path** has no repeated vertices. A **cycle** is a closed walk with no repeated vertices except the first/last, of length at least three in a simple undirected graph.
>
> The distance $d(i,j)$ is the minimum path length, zero for $i=j$, and infinity if no path exists. A connected component is a maximal vertex set whose vertices are mutually reachable.

> [!theorem] Powers of adjacency count walks
> For every integer $r\ge0$, $(A^r)_{ij}$ counts walks of length $r$ from $i$ to $j$.

> [!proof]
> For $r=0$, $A^0=I$ counts the empty walks. If the claim holds at $r$, then $(A^{r+1})_{ij}=\sum_v(A^r)_{iv}A_{vj}$ extends each length-$r$ walk by one edge. Each longer walk has a unique penultimate vertex, so this counts it once. These are not necessarily simple paths.

On a connected graph with $N\ge2$, mean distance and diameter are
$$\bar d=\frac1{N(N-1)}\sum_{i\ne j}d(i,j),\qquad D=\max_{i,j}d(i,j).$$
A connected tree has $L=N-1$ and a unique path between each pair. Conversely, a connected graph with $N-1$ edges is a tree: a cycle would permit removing an edge without disconnecting it, contradicting the minimum $N-1$ edges needed for connectivity.

> [!theorem] Euler trails
> An undirected graph with at least one edge has a trail using every edge exactly once if and only if all non-isolated vertices lie in one component and the number of odd-degree vertices is zero or two. A trail may revisit vertices but not edges.
>
> **Proof.** Necessity follows because arrivals and departures pair at every internal vertex; only the two endpoints may be odd, and all used edges must be reachable. If all degrees are even, follow unused edges until returning to the start, then splice in further closed trails wherever an unused edge touches the current trail. Connectivity ensures this eventually uses every edge. If exactly two vertices are odd, add one auxiliary edge between them, construct such a circuit in the resulting multigraph, and remove the auxiliary edge to obtain an open trail. Four odd vertices, as in the Königsberg bridge graph, rule out the traversal.

For directed graphs, **strong** connectivity requires directed paths both ways; **weak** connectivity means connectivity after ignoring directions. A layout’s Euclidean distance is not graph distance.

> [!algorithm] Breadth-first search
> Start from a source, discover its neighbours, then their undiscovered neighbours, and continue by layers. The first discovery of a vertex occurs at its shortest unweighted distance: any shorter route would have discovered it in an earlier layer. With adjacency lists, one search takes $O(N+L)$ time. Weighted nonnegative edge lengths instead call for a weighted shortest-path algorithm, such as Dijkstra’s.

> [!code] State the component convention
> ```python
> import networkx as nx
>
> G = nx.Graph([(0, 1), (1, 2), (2, 0), (3, 4)])
> G.add_node(5)
> components = list(nx.connected_components(G))
> H = G.subgraph(max(components, key=len)).copy()
> distances = dict(nx.single_source_shortest_path_length(H, 0))
> mean_distance = nx.average_shortest_path_length(H)
> diameter = nx.diameter(H)
> print(len(H) / len(G), mean_distance, diameter)
> ```
> The reported distances describe the largest component, not the entire disconnected graph. Ties between largest components need a convention if their statistics differ.

## Lattice lesson
For an $M\times M$ lattice with horizontal, vertical **and diagonal** nearest-neighbour edges, $M\ge2$,
$$L=2(M-1)(2M-1),\qquad d((a,b),(c,d))=\max(|a-c|,|b-d|),\qquad D=M-1.$$
Each step changes either coordinate by at most one, giving the lower bound; diagonal steps followed by axial steps attain it. Without diagonals the distance is Manhattan distance and the diameter is $2(M-1)$.

Compare this polynomial distance growth with logarithmic typical distances in [[Erdos-Renyi graphs]] and [[Small-world networks]]. A giant component is a positive limiting fraction of a graph sequence, not simply the largest component of one small graph.

> [!reference]- Sources
> Lectures Weeks 1–3; Jenny’s notes Weeks 1–3. Newman §§6.11–6.13 and 8.5–8.6. Tutorial 2, lattice and random-regular comparisons; Tutorial 3, component conventions.
