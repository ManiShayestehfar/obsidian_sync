---
type: lecture-export
week: 1
source_pages: 14
status: visually-checked-paraphrase
tags: [DATA5441, lecture]
---

# Week 1 - Graph representations and measurements

[[00_HOME]] · [[Tutorial 1 - guide]] · [[Newman reading map]] · [[Corrections and caveats]]

Source: `Notes Week 1 - 2026.pdf`; page numbers below refer to this supplied PDF.

Page-by-page mathematical transcription and paraphrase of the supplied handwritten lecture. Equations have been typeset; diagrams and the complete original page are retained in each image. Added explanations, corrections and ambiguities are identified in the text. This is not a verbatim diplomatic transcription.

## Page 01 - Definitions and representations

Lecturer: Eduardo G. Altmann. Week 1 introduces networks as mathematical representations of data and systems.

Let $V=\{1,\ldots,N\}$ be a labelled vertex set and $E\subseteq\{\{i,j\}:i,j\in V,\ i\ne j\}$ the edge set. A **simple undirected graph** is $G=(V,E)$: no self-loops and no parallel edges. The lecture uses $\mathcal N,\mathcal L$ for the sets and $N,L$ for their sizes.

Three equivalent representations are a drawing, an adjacency matrix and an edge list. For a simple graph,
$$A_{ij}=\begin{cases}1,&\{i,j\}\in E,\\0,&\text{otherwise}.\end{cases}$$
Thus $A=A^\top$ and $A_{ii}=0$. The illustrated example has edges $12,14,23,24,34$ and matrix
$$A=\begin{pmatrix}0&1&0&1\\1&0&1&1\\0&1&0&1\\1&1&1&0\end{pmatrix}.$$

> [!example]- Original page 1
> ![[w1-p01.jpg]]

## Page 02 - Edge lists and elementary examples

The previous graph has $E=\{\{1,2\},\{1,4\},\{2,3\},\{2,4\},\{3,4\}\}$.

- **Lattice:** use points of $\mathbb Z^d$ as vertices and connect points within a specified lattice distance $r$. Boundary conditions and the distance convention are part of the model. The drawing gives $d=1,r=2$.
- **Tree:** a connected graph with no cycles, equivalently exactly one simple path between each pair of vertices. The drawing is a branching tree/Bethe-lattice example. “No loops” here means no cycles, not merely no self-loops.
- **Complete graph $K_N$:** every pair of distinct vertices is joined. For $N=3$, $A_{ij}=1-\delta_{ij}$.

> [!example]- Original page 2
> ![[w1-p02.jpg]]

## Page 03 - Why model data as networks

The lecture’s examples translate a system into vertices and edges:

| System | Vertices | Edges |
| --- | --- | --- |
| Online social network | Users | Friendship, followers, connections |
| Ecological network | Species | Interactions |
| Air transport | Airports | Direct flights |
| Chess | Positions | Legal moves |
| World Wide Web | Pages | Hyperlinks |
| Internet | Computers/servers | Physical connections |
| Power grid | Producers/consumers | Electrical connections |
| Sports tournament | Teams/competitors | Played matches |

The world-map figure illustrates the geographical pattern of social connections. The modelling choice determines direction, weight and what counts as a vertex.

> [!example]- Original page 3
> ![[w1-p03.jpg]]

## Page 04 - Structure affects processes

The page juxtaposes an Australian flight network, a historical Black Death map and a coronavirus case map. Its message is that network connections can affect how a process spreads. These are motivating illustrations, not a derivation or a dataset analysed in this vault. Their original labels and graphics are retained in the page image.

> [!example]- Original page 4
> ![[w1-p04.jpg]]

## Page 05 - A high-dimensional sample space

A labelled simple undirected graph has $Y=\binom N2=N(N-1)/2$ possible edges. Each can independently be absent or present when counting possibilities, so
$$|\Omega_N|=2^Y=2^{N(N-1)/2}.$$
This is a counting statement, not yet a probabilistic assumption. Networks exemplify large, noisy and interdependent datasets: an adjacency matrix has quadratically many entries, and there are exponentially many graph configurations in $N^2$. The lecture compares this with configuration spaces in statistical physics, genetic sequences and language.

**Notation clarification:** the handwritten $\sim e^{N^2}$ expresses exponential order informally. Precisely, $\log|\Omega_N|=(\log2)N(N-1)/2$.

> [!example]- Original page 5
> ![[w1-p05.jpg]]

## Page 06 - Beyond simple undirected graphs

- **Directed graph:** edges have orientations; generally $A_{ij}\ne A_{ji}$.
- **Multigraph:** more than one edge may connect a pair.
- **Weighted network:** edges carry values $w_{ij}$; their interpretation matters.
- **Multilayer network:** several kinds of edge or vertex are represented in layers.
- **Temporal network:** edges or vertices have associated times.
- **Bipartite network:** $V=V_1\sqcup V_2$ and every edge crosses between the two parts. Multipartite networks generalise this partition.

The page provides small drawings for directed, multiple and weighted edges.

> [!example]- Original page 6
> ![[w1-p06.jpg]]

## Page 07 - Coauthorship and hypergraphs

A coauthorship dataset can be represented as a bipartite author–paper graph. Its author projection joins authors who share a paper. An author’s **Erdős number** is their graph distance from Paul Erdős in that projection, if a connecting path exists. A distance in the author–paper graph counts alternating author/paper steps and must not be confused with the projected distance.

A **hypergraph** allows an edge $e\subseteq V$ to contain more than two vertices; one paper with several authors can be represented as one hyperedge rather than many pairwise edges.

> [!example]- Original page 7
> ![[w1-p07.jpg]]

## Page 08 - Historical motivation and Euler trails

The Königsberg bridge question asks for a traversal using every bridge exactly once. In the multigraph shown, the four vertex degrees are $3,3,5,3$.

An edge-by-edge traversal has paired arrivals and departures at every internal vertex. Consequently, only its two endpoints can have odd degree (or none for a closed traversal). Four odd-degree vertices therefore make the requested traversal impossible.

**Precise theorem:** an undirected graph with at least one edge has an Euler trail iff all non-isolated vertices belong to one component and the number of odd-degree vertices is zero or two. The lecture only needs the necessary parity condition. It also notes Erdős–Rényi random graphs (1959) and social network analysis in the 1950s, illustrated by ego and alter nodes.

> [!example]- Original page 8
> ![[w1-p08.jpg]]

## Page 09 - Historical strands continued

The lecture lists economic input–output networks associated with Leontief; the late-1990s growth of network science combining statistical physics and large datasets; and computer-science applications including PageRank, graph neural networks and causal discovery.

The organising question is the relationship between **structure** (connections) and **function** (dynamics). These historical remarks motivate the course rather than supply assessed formulas.

> [!example]- Original page 9
> ![[w1-p09.jpg]]

## Page 10 - Walks, adjacency powers and shortest paths

A sequence $(v_0,\ldots,v_r)$ with $A_{v_{a-1},v_a}=1$ for each $a$ is a **walk** of length $r$. The lecture calls this a “path”, permitting repeated vertices. In this vault “simple path” explicitly forbids repetitions.

The number $W_{ij}^{(r)}$ of length-$r$ walks from $i$ to $j$ is
$$W_{ij}^{(1)}=A_{ij},\qquad W_{ij}^{(2)}=\sum_kA_{ik}A_{kj},\qquad W_{ij}^{(r)}=(A^r)_{ij}.$$
**Reason:** split each length-$r+1$ walk at its penultimate vertex and sum over that vertex; this is matrix multiplication.

For $i\ne j$, $d_{ij}=\min\{r\ge1:(A^r)_{ij}>0\}$, with $d_{ij}=\infty$ when there is no walk. Set $d_{ii}=0$. The example distinguishes a valid vertex sequence from one containing a missing edge. See [[Walks and clustering]].

> [!example]- Original page 10
> ![[w1-p10.jpg]]

## Page 11 - Paths, neighbourhoods and distance measures

A geodesic is a shortest path; a closed walk finishes at its starting vertex; a simple path has no repeated vertices. The neighbourhood is $\Gamma(i)=\{j:A_{ij}=1\}$.

For a connected graph with $N\ge2$,
$$d_i=\frac1{N-1}\sum_{j\ne i}d_{ij},\qquad \bar d=\frac1N\sum_i d_i=\frac1{N(N-1)}\sum_{i\ne j}d_{ij},$$
$$d_{\mathrm{diam}}=\max_{i,j}d_{ij}.$$
Average distance and diameter are different statistics. On a disconnected graph these whole-graph distances can be infinite; the tutorials use the largest connected component and should report that restriction explicitly.

> [!example]- Original page 11
> ![[w1-p11.jpg]]

## Page 12 - Components, degrees and sparsity

A connected component is a maximal set of mutually reachable vertices. In the drawing, two disconnected groups form two components.

The degree is $z_i=\sum_jA_{ij}$. Each edge contributes one degree at each endpoint, yielding the handshaking identity
$$\sum_i z_i=2L,\qquad \langle z\rangle=\frac{2L}{N}.$$
The lecture uses **sparse** to mean bounded limiting mean degree, hence $L=O(N)$ and $L/\binom N2\to0$. A broader convention calls any $L=o(N^2)$ sparse; this need not have bounded mean degree. State the convention in scaling arguments.

The source uses $A\sim B$ for a ratio approaching a nonzero constant. In standard asymptotic notation $A\sim B$ often means the ratio tends specifically to one; this vault spells out the intended limit.

> [!example]- Original page 12
> ![[w1-p12.jpg]]

## Page 13 - Local clustering and transitivity

Let $\Delta_i$ be the number of triangles containing vertex $i$ and $\Delta$ the total number of triangles. For $z_i\ge2$,
$$C_i=\frac{\Delta_i}{\binom{z_i}{2}}=\frac{2\Delta_i}{z_i(z_i-1)}.$$
We use $C_i=0$ for $z_i<2$, matching the usual tutorial convention. Two global measures are
$$\bar C=\frac1N\sum_iC_i,\qquad C_{\mathrm{net}}=\frac{3\Delta}{\sum_i\binom{z_i}{2}}.$$
The second is **transitivity**. Its denominator counts unordered neighbour pairs centred at a vertex. Every triangle supplies three such closed triples, or six oriented length-three closed walks. Therefore the lecture’s ratio “closed length-three walks / oriented simple length-two paths” gives the same result.

If the denominator is zero, the ratio is mathematically undefined; software may assign zero. State this convention. In general $\bar C\ne C_{\mathrm{net}}$; transitivity weights $C_i$ by $\binom{z_i}{2}$.

> [!example]- Original page 13
> ![[w1-p13.jpg]]

## Page 14 - Worked clustering example

The illustrated graph is $K_4$ with one edge missing, with vertex labels different from p. 1. Its degrees are $(3,3,2,2)$ and it contains two triangles.

The two degree-three vertices have $C_1=C_2=2/3$; the degree-two vertices have $C_3=C_4=1$. Thus
$$\bar C=\frac14\left(\frac23+\frac23+1+1\right)=\frac56,$$
$$C_{\mathrm{net}}=\frac{3\cdot2}{2\binom32+2\binom22}=\frac68=\frac34.$$
The distinction is a weighting effect, not a contradiction. See [[Walks and clustering]] for a matrix formulation and additional checks.

> [!example]- Original page 14
> ![[w1-p14.jpg]]

