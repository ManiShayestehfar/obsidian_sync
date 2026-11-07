---
tags: [data5441, chapter, ch08]
aliases: [Week 8, Chapter 8]
---
# Ch08 Community detection

> [!abstract] Scope
> Lecture notes pp. 101–112 · Week 8 · ← [[Ch07 SBMs and statistical inference]] · [[Ch09 Network reconstruction]] →

## Topic notes
- [[Community detection]]: cut, Kernighan–Lin, modularity, Louvain
- [[Spectral graph theory]]: Laplacian, components, eigengap, spectral clustering

## Key results at a glance
> [!summary]+ Memorise
> - $Q=\frac1{2L}\sum_{ij}(A_{ij}-\frac{z_iz_j}{2L})\delta_{b_ib_j}$; one group gives $Q=0$
> - $\Delta Q_{merge}=l_{rs}/L-K_rK_s/2L^2$
> - $x^\top\mathbf Lx=\sum_{\text{links}}(x_i-x_j)^2$; # zero eigenvalues = # components
> - Choose $B$ at the eigengap; $k$-means on rows of $U$

## Tutorial focus
Karate: bisection, greedy, Louvain; communities in ER and in the 5-block SBM contrast sweep; spectral clustering.

## Exam patterns
> [!exam] How this chapter is examined
> Read best $B$ and $Q$ from plots; agglomerative vs divisive; heuristics are not global optima; why Louvain finds communities in ER.
> See [[Exam patterns]] for worked trial-exam items and [[Formula sheet]] for what is provided.

## Revision checklist
- [ ] Reproduce every boxed statement in [[Community detection]] and answer its self-test without looking.
- [ ] Reproduce every boxed statement in [[Spectral graph theory]] and answer its self-test without looking.

---
Up: [[00 Home]]
