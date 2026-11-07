---
tags: [data5441, chapter, ch05]
aliases: [Week 5, Chapter 5]
---
# Ch05 Mechanistic models

> [!abstract] Scope
> Lecture notes pp. 62–73 · Week 5 · ← [[Ch04 Sampling random graphs]] · [[Ch06 ERGMs and Metropolis–Hastings]] →

## Topic notes
- [[Small-world networks]]: Milgram, WS, three conditions, Kleinberg
- [[Power laws]]: moments, natural cutoff, CCDF
- [[Preferential attachment]]: BA growth, $\gamma=3$

## Key results at a glance
> [!summary]+ Memorise
> - Small world = sparse + $\ell\sim\log N$ + high $C$
> - WS: $C(0)=\frac{3(Q-1)}{2(2Q-1)}$, $C(p)\approx C(0)(1-p)^3$
> - $\langle z^n\rangle<\infty$ iff $\gamma>n+1$; $z_{max}\sim N^{1/(\gamma-1)}$
> - BA: $\pi_i=z_i/2L$, $z_i=m\sqrt{t/t_i}$, $P(z)\approx2m^2z^{-3}$, $\langle z\rangle\to2m$

## Tutorial focus
WS rewiring sweeps; degree-preserving lattice swaps; BA vs density-matched ER; political-blog degree variability.

## Exam patterns
> [!exam] How this chapter is examined
> Match BA to ER via $m=\langle z\rangle/2$; compare $\sigma_z/\langle z\rangle$; assess each small-world condition.
> See [[Exam patterns]] for worked trial-exam items and [[Formula sheet]] for what is provided.

## Revision checklist
- [ ] Reproduce every boxed statement in [[Small-world networks]] and answer its self-test without looking.
- [ ] Reproduce every boxed statement in [[Power laws]] and answer its self-test without looking.
- [ ] Reproduce every boxed statement in [[Preferential attachment]] and answer its self-test without looking.

---
Up: [[00 Home]]
