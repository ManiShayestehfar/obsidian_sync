---
tags: [data5441, chapter, ch10]
aliases: [Week 10, Chapter 10]
---
# Ch10 Resilience and percolation

> [!abstract] Scope
> Lecture notes pp. 128–143 · Week 10 · ← [[Ch09 Network reconstruction]] · [[Ch11 Cascades and binary models]] →

## Topic notes
- [[Percolation on lattices]]: site/bond, $p_c$, Bethe lattice
- [[Percolation and robustness]]: $q_c$, failures vs attacks

## Key results at a glance
> [!summary]+ Memorise
> - Tree: $p_c=1/(k-1)$
> - $q_c=1-1/(\langle z^2\rangle/\langle z\rangle-1)$ (formula sheet)
> - ER: $q_c=1-1/\langle z\rangle$; scale-free: $q_c\to1$
> - Hub removal destroys heavy-tailed networks quickly

## Tutorial focus
Lattice percolation (4 vs 8 neighbours); regular trees; ER vs BA failures; prescribed degrees; static degree attacks.

## Exam patterns
> [!exam] How this chapter is examined
> Compute $\langle z\rangle$, $\langle z^2\rangle$ for a given $P(z)$, then the giant-component and $q_c$ conditions; sketch $\theta(z^*)$, $\theta(q)$; robustness trend.
> See [[Exam patterns]] for worked trial-exam items and [[Formula sheet]] for what is provided.

## Revision checklist
- [ ] Reproduce every boxed statement in [[Percolation on lattices]] and answer its self-test without looking.
- [ ] Reproduce every boxed statement in [[Percolation and robustness]] and answer its self-test without looking.

---
Up: [[00 Home]]
