---
tags: [data5441, chapter, ch02]
aliases: [Week 2, Chapter 2]
---
# Ch02 Centrality measures

> [!abstract] Scope
> Lecture notes pp. 17–29 · Week 2 · ← [[Ch01 Networks and high dimensions]] · [[Ch03 Random graph models]] →

## Topic notes
- [[Centrality]]: degree, closeness, betweenness, eigenvector, Katz, PageRank
- [[Sampling and friendship paradox]]: degree bias, $\langle z^2\rangle/\langle z\rangle$

## Key results at a glance

> [!summary]+ Memorise
> - Betweenness $b_i=\sum_{s<t}\sigma_{st}(i)/\sigma_{st}$, normalised by $\binom{N-1}2$
> - Eigenvector: $x(t+1)=Ax(t)\to$ Perron vector; fails to converge on bipartite graphs
> - Katz converges iff $\alpha<1/\lambda_1$
> - PageRank $x_i\leftarrow\alpha\sum_jA_{ij}x_j/z_j^{out}+\beta$ (formula sheet)
> - Endpoint sampling: $\Pr(z)=zP(z)/\langle z\rangle$, mean $\langle z^2\rangle/\langle z\rangle\ge\langle z\rangle$

## Tutorial focus
Centralities of simple and directed examples; Les Misérables / Star Wars; lattice vs random $k$-regular clustering and distances.

## Exam patterns
> [!exam] How this chapter is examined
> Rank nodes by degree; find the max-betweenness node and its normalised value; match the measure to the question (most friends → degree; bridges → betweenness).
> See [[Exam patterns]] for worked trial-exam items and [[Formula sheet]] for what is provided.

## Revision checklist
- [ ] Reproduce every boxed statement in [[Centrality]] and answer its self-test without looking.
- [ ] Reproduce every boxed statement in [[Sampling and friendship paradox]] and answer its self-test without looking.

---
Up: [[00 Home]]
