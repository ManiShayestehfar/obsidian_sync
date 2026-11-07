---
tags: [data5441, index]
aliases: [Home, DATA5441]
---
# DATA5441 — Networks and High-dimensional Inference

> [!abstract] How to use this vault
> - **Chapters/** has one hub per lecture chapter (= teaching week): scope, key results, tutorial focus, exam patterns, checklist.
> - **Topics/** has the atomic notes, where every statement sits in a callout:
>   - `[!definition]`, `[!theorem]`, `[!proposition]`, `[!algorithm]` for the course statements;
>   - `[!proof]-` for folded proofs;
>   - `[!exam]` for how the topic appears in trial exams;
>   - `[!selftest]-` for folded active-recall questions.
> - **Exam/** has the [[Formula sheet]] (what you are given) and [[Exam patterns]] (what you are asked).
>
> To colour the custom callouts, enable the CSS snippet `data5441-callouts` (Settings → Appearance → CSS snippets).

## Chapters
| Wk | Chapter | Topics |
|---|---|---|
| 1 | [[Ch01 Networks and high dimensions]] | [[Graphs and representations]] · [[Paths and components]] · [[Clustering]] |
| 2 | [[Ch02 Centrality measures]] | [[Centrality]] · [[Sampling and friendship paradox]] |
| 3 | [[Ch03 Random graph models]] | [[Random graph ensembles]] · [[Erdos-Renyi graphs]] |
| 4 | [[Ch04 Sampling random graphs]] | [[Markov chain Monte Carlo on graphs]] · [[Configuration model]] |
| 5 | [[Ch05 Mechanistic models]] | [[Small-world networks]] · [[Power laws]] · [[Preferential attachment]] |
| 6 | [[Ch06 ERGMs and Metropolis–Hastings]] | [[Metropolis–Hastings]] · [[Maximum entropy and ERGMs]] |
| 7 | [[Ch07 SBMs and statistical inference]] | [[Stochastic block models]] · [[Statistical inference and model selection]] |
| 8 | [[Ch08 Community detection]] | [[Community detection]] · [[Spectral graph theory]] |
| 9 | [[Ch09 Network reconstruction]] | [[Link prediction]] · [[Reconstruction from node activity]] |
| 10 | [[Ch10 Resilience and percolation]] | [[Percolation on lattices]] · [[Percolation and robustness]] |
| 11 | [[Ch11 Cascades and binary models]] | [[Binary-state dynamics]] · [[Threshold model and cascades]] · [[SI and SIS models]] |
| 12 | [[Ch12 Epidemics and games on networks]] | [[SIR model and epidemic threshold]] · [[Evolutionary games on networks]] · [[Synchronisation and stability]] |

## Exam
- [[Formula sheet]]: the sheet printed on the last page of the exam. Do not memorise these formulas; know when to use them.
- [[Exam patterns]]: question types from both trial exams, with the method for each.

## The one idea that recurs everywhere

> [!summary] Degree-biased branching
> Following a random link reaches degree $z$ with probability $zP(z)/\langle z\rangle$, leaving $z-1$ onward links. The mean excess degree is $\kappa=\langle z^2\rangle/\langle z\rangle-1$, and $\kappa$ (times a transmission or retention probability) $>1$ is the threshold condition in:
> - the friendship paradox ([[Sampling and friendship paradox]]);
> - the giant component ([[Configuration model]]);
> - robustness, $q_c$ ([[Percolation and robustness]]);
> - cascades ([[Threshold model and cascades]]);
> - epidemics, $\lambda/\mu>\langle z\rangle/\langle z^2\rangle$ ([[SIR model and epidemic threshold]]).
>
> Heavy tails ($2<\gamma\le3$, [[Power laws]]) make $\kappa\to\infty$.

> [!info]- Notation
> - **Counts:** $N$ nodes, $L$ links, $Y=N(N-1)/2$ node pairs.
> - **Degrees:** $z_i$ (the lecturer's symbol), $P(z)$, $\langle z^n\rangle$.
> - **Clustering:** $T$ triangles, $C_i$, $C_{net}$, $\langle C\rangle$.
> - **Laplacian:** $\mathbf L=D-A$, written in bold so it is not confused with the link count $L$.
> - **Dynamics:** $\rho(t)$ is the active or infected fraction. SIR uses rates $\lambda$ (infection) and $\mu$ (recovery).
> - **Percolation:** $p$ is the retention probability and $q=1-p$ the failure probability. In the threshold model, $q_i$ is instead an adoption threshold.
>
> **Sources:** lecture notes 2026 (E. G. Altmann), tutorials 1–11, two trial exams, Jeny's 2025 notes, and Newman, *Networks* (2018).
