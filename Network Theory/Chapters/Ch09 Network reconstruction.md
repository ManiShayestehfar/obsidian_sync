---
tags: [data5441, chapter, ch09]
aliases: [Week 9, Chapter 9]
---
# Ch09 Network reconstruction

> [!abstract] Scope
> Lecture notes pp. 113–127 · Week 9 · ← [[Ch08 Community detection]] · [[Ch10 Resilience and percolation]] →

## Topic notes
- [[Link prediction]]: heuristics, SBM, embedding, AUC
- [[Reconstruction from node activity]]: correlation, Ising pseudolikelihood

## Key results at a glance
> [!summary]+ Memorise
> - Heuristic / inferential / embedding approaches
> - AUC $=\Pr(s_+>s_-)+\frac12\Pr(s_+=s_-)$; constant scores give $0.5$
> - Test negatives from the original non-links; features from the training graph only
> - $P(s_i\mid s_{-i})=1/(1+e^{-2s_ih_i})$; random overlap $L^2/Y$

## Tutorial focus
Compare heuristic, SBM and spectral scores on matched splits; Pearson vs pseudolikelihood reconstruction.

## Exam patterns
> [!exam] How this chapter is examined
> Identify which methods do link prediction (spectral, Jaccard/CN, SBM) vs community detection vs dynamics.
> See [[Exam patterns]] for worked trial-exam items and [[Formula sheet]] for what is provided.

## Revision checklist
- [ ] Reproduce every boxed statement in [[Link prediction]] and answer its self-test without looking.
- [ ] Reproduce every boxed statement in [[Reconstruction from node activity]] and answer its self-test without looking.

---
Up: [[00 Home]]
