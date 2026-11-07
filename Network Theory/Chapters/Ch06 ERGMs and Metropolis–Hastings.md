---
tags: [data5441, chapter, ch06]
aliases: [Week 6, Chapter 6]
---
# Ch06 ERGMs and Metropolis–Hastings

> [!abstract] Scope
> Lecture notes pp. 74–84 · Week 6 · ← [[Ch05 Mechanistic models]] · [[Ch07 SBMs and statistical inference]] →

## Topic notes
- [[Metropolis–Hastings]]: acceptance rule, detailed balance, $Z$ cancels
- [[Maximum entropy and ERGMs]]: exponential family, moments from $\ln Z$

## Key results at a glance
> [!summary]+ Memorise
> - $A=\min\{1,\frac{p(g')\Pi(g'\to g)}{p(g)\Pi(g\to g')}\}$
> - Max entropy ⇒ $p(g)=e^{\beta\cdot x(g)}/Z$
> - $\partial_\beta\ln Z=\langle x\rangle$, $\partial^2_\beta\ln Z=\operatorname{Var}x$
> - $x=L$ on $\Omega_N$ gives ER with $p=e^\beta/(1+e^\beta)$

## Tutorial focus
Metropolis for $p(x)=2x$ on $[0,1]$ (role of the proposal width); Metropolis on graphs with weights $1,C,C^{10}$; ERGM for the November 17 network.

## Exam patterns
> [!exam] How this chapter is examined
> Sizes of graph spaces; $\beta=0$ gives uniform; symmetric edge-replacement proposal $1/[L(Y-L+1)]$; derive acceptance probabilities for $p\propto L^2$, $e^{\beta L}$, $e^{\beta T}$.
> See [[Exam patterns]] for worked trial-exam items and [[Formula sheet]] for what is provided.

## Revision checklist
- [ ] Reproduce every boxed statement in [[Metropolis–Hastings]] and answer its self-test without looking.
- [ ] Reproduce every boxed statement in [[Maximum entropy and ERGMs]] and answer its self-test without looking.

---
Up: [[00 Home]]
