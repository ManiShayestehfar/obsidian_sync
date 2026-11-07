---
tags: [data5441, chapter, ch12]
aliases: [Week 12, Chapter 12]
---
# Ch12 Epidemics and games on networks

> [!abstract] Scope
> Lecture notes pp. 151–166 · Week 12 · ← [[Ch11 Cascades and binary models]] · — →

## Topic notes
- [[SIR model and epidemic threshold]]: order-0/1 mean field, percolation link
- [[Evolutionary games on networks]]: PD, Nash, imitation dynamics, hubs
- [[Synchronisation and stability]]: Laplacian modes, diffusion, Kuramoto

## Key results at a glance
> [!summary]+ Memorise
> - Order 0: $r_\infty=1-e^{-\lambda\langle z\rangle r_\infty/\mu}$; outbreak iff $\lambda/\mu>1/\langle z\rangle$
> - Order 1: outbreak iff $\lambda/\mu>\langle z\rangle/\langle z^2\rangle$
> - Transmissibility $p\approx\lambda/\mu$ ⇒ percolation; scale-free has no threshold
> - PD: $(D,D)$ Nash, $(C,C)$ collective optimum; network payoff $S_i=\sum_jA_{ij}M_{e_ie_j}$
> - Degree heterogeneity favours cooperation

## Tutorial focus
No tutorial notebook supplied for Week 12; the in-class game used $M=\begin{pmatrix}1&0\\b&0\end{pmatrix}$, $b=1.5$.

## Exam patterns
> [!exam] How this chapter is examined
> Expect derivation-style questions: the SIR ODEs, the threshold via the slope condition, the percolation analogy, PD definitions and the hub argument.
> See [[Exam patterns]] for worked trial-exam items and [[Formula sheet]] for what is provided.

## Revision checklist
- [ ] Reproduce every boxed statement in [[SIR model and epidemic threshold]] and answer its self-test without looking.
- [ ] Reproduce every boxed statement in [[Evolutionary games on networks]] and answer its self-test without looking.
- [ ] Reproduce every boxed statement in [[Synchronisation and stability]] and answer its self-test without looking.

---
Up: [[00 Home]]
