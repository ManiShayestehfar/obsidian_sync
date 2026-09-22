---
type: study-note
tags: [DATA5441]
---

# Walks and clustering

[[00_HOME]]

**Prerequisites:** adjacency matrices, matrix multiplication. Sources: Week 1; Newman §§6.11–6.12, 7.3.

A walk may revisit vertices and edges; a path does not revisit vertices. Expanding a matrix product shows
$$ (A^r)_{ij}=\sum_{v_1,\ldots,v_{r-1}}A_{iv_1}\cdots A_{v_{r-1}j}, $$
which counts length-$r$ walks, not simple paths. In a simple undirected graph,
$$T=\frac{\operatorname{tr}(A^3)}6,\qquad T_i=\frac{(A^3)_{ii}}2.$$
A triangle contributes three starting vertices and two directions to the trace.

Local clustering and transitivity are
$$C_i=\frac{T_i}{\binom{z_i}2},\quad \bar C=\frac1N\sum_iC_i,\quad C_{net}=\frac{3T}{\sum_i\binom{z_i}2}.$$
Consequently transitivity is the wedge-weighted average of local clustering, not the uniform vertex average. If no wedges exist, the ratio is undefined mathematically; a program may return zero by convention.

**Worked example:** join a hub to five leaves and add two disjoint leaf–leaf edges. Then $N=6,L=7$, degrees $(5,2,2,2,2,1)$, and there are two triangles. Local coefficients are $(1/5,1,1,1,1,0)$, giving $\bar C=7/10$ but $C_{net}=6/14=3/7$. This is Tutorial 1’s first quiz.

Breadth-first search gives distances from a source in $O(N+L)$ time for an adjacency-list graph. The diameter is the maximum finite distance only if the component convention is stated; the usual whole-graph diameter requires connectedness. Reachability is a topological property; a layout’s Euclidean distance is not graph distance.

**Check yourself:** why does $\operatorname{tr}(A^2)=2L$? Each edge supplies one two-step return walk from each endpoint.
