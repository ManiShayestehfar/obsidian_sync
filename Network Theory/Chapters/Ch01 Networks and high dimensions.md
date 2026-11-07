---
tags: [data5441, chapter, ch01]
aliases: [Week 1, Chapter 1]
---
# Ch01 Networks and high dimensions

> [!abstract] Scope
> Lecture notes pp. 3–16 · Week 1 · ← — · [[Ch02 Centrality measures]] →

## Topic notes
- [[Graphs and representations]]: definitions, degree, $P(z)$, sparse vs dense
- [[Paths and components]]: walks, distance, diameter, components
- [[Clustering]]: $C_i$, $C_{net}$, $\langle C\rangle$

## Key results at a glance
> [!summary]+ Memorise
> - $\sum_iz_i=2L$, $\langle z\rangle=2L/N$, $Y=N(N-1)/2$
> - $P(z)=N_z/N$, $\sigma_z=\sqrt{\langle z^2\rangle-\langle z\rangle^2}$, relative variability $\sigma_z/\langle z\rangle$
> - $(A^r)_{ij}$ counts walks of length $r$; $T=\operatorname{tr}A^3/6$
> - $C_i=2T_i/[z_i(z_i-1)]$, $C_{net}=3T/\sum_i\binom{z_i}2$, $\langle C\rangle=\frac1N\sum_iC_i$

## Tutorial focus
Load data (`read_edgelist`, `from_pandas_edgelist`), remove self-loops, compute $N,L,\langle z\rangle$, diameter, transitivity vs average clustering; US airports.

## Exam patterns
> [!exam] How this chapter is examined
> Short answers from a drawn graph: $N$, $L$, $z_i$, $D$, $\langle z\rangle$, $C_i$, $\langle C\rangle$, $\sigma_z/\langle z\rangle$, shortest path length.
> See [[Exam patterns]] for worked trial-exam items and [[Formula sheet]] for what is provided.

## Revision checklist
- [ ] Reproduce every boxed statement in [[Graphs and representations]] and answer its self-test without looking.
- [ ] Reproduce every boxed statement in [[Paths and components]] and answer its self-test without looking.
- [ ] Reproduce every boxed statement in [[Clustering]] and answer its self-test without looking.

---
Up: [[00 Home]]
