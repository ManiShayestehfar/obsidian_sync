---
tags: [data5441, chapter, ch03]
aliases: [Week 3, Chapter 3]
---
# Ch03 Random graph models

> [!abstract] Scope
> Lecture notes pp. 30–44 · Week 3 · ← [[Ch02 Centrality measures]] · [[Ch04 Sampling random graphs]] →

## Topic notes
- [[Random graph ensembles]]: $\Omega_N$, $\Omega_{N,L}$, null-model logic
- [[Erdos-Renyi graphs]]: binomial/Poisson degrees, $C\approx p$, giant component

## Key results at a glance
> [!summary]+ Memorise
> - $|\Omega_N|=2^Y$, $|\Omega_{N,L}|=\binom YL$
> - $P(g)=p^L(1-p)^{Y-L}$, $\hat p=2L/[N(N-1)]$, $\langle z\rangle=p(N-1)$
> - Sparse: $p=c/(N-1)$ → Poisson$(c)$, $\sigma_z/\langle z\rangle\to1/\sqrt c$
> - Giant component $S=1-e^{-\langle z\rangle S}$, threshold $\langle z\rangle=1$
> - $\ell\approx\log N/\log\langle z\rangle$

## Tutorial focus
Compare an empirical network with repeated ER draws; dense (fixed $p$) vs sparse (fixed $\langle z\rangle$); largest-component transition.

## Exam patterns
> [!exam] How this chapter is examined
> Fit ER to $(N,L)$; sparse or dense for $p=c/N$; $N$ for given $C$; which properties ER fails to reproduce (clustering, broad degrees).
> See [[Exam patterns]] for worked trial-exam items and [[Formula sheet]] for what is provided.

## Revision checklist
- [ ] Reproduce every boxed statement in [[Random graph ensembles]] and answer its self-test without looking.
- [ ] Reproduce every boxed statement in [[Erdos-Renyi graphs]] and answer its self-test without looking.

---
Up: [[00 Home]]
