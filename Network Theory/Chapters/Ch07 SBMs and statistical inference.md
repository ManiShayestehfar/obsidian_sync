---
tags: [data5441, chapter, ch07]
aliases: [Week 7, Chapter 7]
---
# Ch07 SBMs and statistical inference

> [!abstract] Scope
> Lecture notes pp. 85–100 · Week 7 · ← [[Ch06 ERGMs and Metropolis–Hastings]] · [[Ch08 Community detection]] →

## Topic notes
- [[Stochastic block models]]: definition, $\hat p_{rs}=l_{rs}/y_{rs}$, search
- [[Statistical inference and model selection]]: overfitting, $S(N,B)$, choosing $B$

## Key results at a glance
> [!summary]+ Memorise
> - $\Pr(A_{ij}=1)=p_{b_ib_j}$; $\hat p_{rs}=l_{rs}/y_{rs}$
> - $y_{rr}=\binom{n_r}2$ (undirected) or $n_r(n_r-1)$ (directed); $y_{rs}=n_rn_s$
> - Assortative / disassortative / core–periphery
> - Greedy → local minima; Metropolis with $e^{-\beta\Delta F}$
> - Penalty $\ln[B!S(N,B)]$; $B=N$ overfits

## Tutorial focus
Karate Club partitions (one block, random, club split); greedy and local minima; MCMC; comparing $B$.

## Exam patterns
> [!exam] How this chapter is examined
> Compute every $p_{rs}$ (bipartite, directed, planted groups); probabilities of joint events $=$ products; real data show **more** repeated co-authorships and reciprocity than the SBM.
> See [[Exam patterns]] for worked trial-exam items and [[Formula sheet]] for what is provided.

## Revision checklist
- [ ] Reproduce every boxed statement in [[Stochastic block models]] and answer its self-test without looking.
- [ ] Reproduce every boxed statement in [[Statistical inference and model selection]] and answer its self-test without looking.

---
Up: [[00 Home]]
