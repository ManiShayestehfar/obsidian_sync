---
tags: [data5441, chapter, ch04]
aliases: [Week 4, Chapter 4]
---
# Ch04 Sampling random graphs

> [!abstract] Scope
> Lecture notes pp. 45–61 · Week 4 · ← [[Ch03 Random graph models]] · [[Ch05 Mechanistic models]] →

## Topic notes
- [[Markov chain Monte Carlo on graphs]]: detailed balance, moves, burn-in
- [[Configuration model]]: fixed degrees, $z_iz_j/2L$, Molloy–Reed

## Key results at a glance
> [!summary]+ Memorise
> - Detailed balance $\pi(g)W(g\to h)=\pi(h)W(h\to g)$ ⇒ stationarity
> - Edge replacement keeps $L$; double-edge swap keeps every $z_i$; symmetric ⇒ accept all for uniform target
> - Configuration model: $\mathbb E A_{ij}\approx z_iz_j/2L$
> - Giant component iff $\langle z^2\rangle/\langle z\rangle>2$

## Tutorial focus
Les Misérables null ensembles: fixed $N$; fixed $N,L$; fixed degree sequence (stub matching vs swaps). Burn-in and correlation.

## Exam patterns
> [!exam] How this chapter is examined
> Read an MCMC trace ($t=0$ is $g^*$, plateau is the null value, ergodicity gives probability-1 visits); which null model preserves a broad degree sequence.
> See [[Exam patterns]] for worked trial-exam items and [[Formula sheet]] for what is provided.

## Revision checklist
- [x] Reproduce every boxed statement in [[Markov chain Monte Carlo on graphs]] and answer its self-test without looking.
- [x] Reproduce every boxed statement in [[Configuration model]] and answer its self-test without looking.

---
Up: [[00 Home]]
