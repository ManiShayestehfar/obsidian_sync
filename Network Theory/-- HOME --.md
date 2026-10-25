# Network Theory — DATA5441

This wiki brings the course together by topic. Start with [[Weekly revision guide]] when revising in teaching order; use the topic groups below when you need a concept or its prerequisites. Each chapter develops a question through definitions, results, short proofs, examples and a final revision checklist. Python boxes are folded so they do not interrupt the main argument.

## Foundations

[[Graphs and representations]] · [[Paths and components]] · [[Clustering]] · [[Centrality]] · [[Sampling and friendship paradox]] · [[Spectral graph theory]]

## Models and computation

[[Random graph ensembles]] · [[Erdos-Renyi graphs]] · [[Configuration model]] · [[Monte Carlo sampling]] · [[Small-world networks]] · [[Power laws]] · [[Preferential attachment]] · [[Maximum entropy and ERGMs]]

## Inference and reconstruction

[[Stochastic block models]] · [[Statistical inference and model selection]] · [[Community detection]] · [[Network reconstruction]] · [[Reconstruction from node activity]]

## Dynamics and robustness

[[Percolation and robustness]] · [[Binary dynamics and cascades]] · [[Threshold cascades]] · [[Epidemic models]]

## Supplementary material awaiting the next lecture upload

[[Evolutionary games]] · [[Synchronisation and stability]]

These chapters and the supplementary SIR/continuous-time section in **Epidemic models** retain material from Jenny’s notes and the earlier vault. They have not been assigned to a confirmed 2026 Week 12 schedule. The weekly guide will be completed when those notes arrive.

> [!info]- Notation and reading conventions
> Unless stated otherwise, graphs are finite, simple, undirected and unweighted. $N$ is vertex count, $L$ edge count and $k_i$ degree (the lecturer also writes $z_i$). $\mathcal L=D-A$ denotes the Laplacian. Directed examples use $A_{ij}=1$ for $i\to j$; transpose formulas when using the opposite convention. Logarithms are natural.
>
> Distinguish exact finite statements, limiting results, approximations and simulation observations. In the percolation chapter, $p$ is retention and $q=1-p$ failure. In the threshold chapter, $q$ is an adoption threshold. In Week 11’s simulations, $\lambda,\mu$ are probabilities per selected-node update; continuous-rate sections use $\beta,\delta$ instead.

> [!reference]- Sources and figures
> The base is your uploaded topic-based vault. Weeks 8–11 have now been integrated from all 50 supplied lecture pages and the relevant notebook sections; source callouts identify pages, exercises and cells where helpful. Weeks 1–7 retain the previous lecture/tutorial synthesis. Jenny’s supplied notes (author line: Jeny Yuan) provide additional context, with substantive errors corrected in the relevant chapter.
>
> “Newman” means Mark Newman, *Networks*, second edition, Oxford University Press, 2018, supplied PDF. Section references refer to that edition; stated book pages are printed pages. These are integrated study explanations, not verbatim PDF transcriptions.
>
> Captions distinguish newly drawn diagrams and analytic illustrations from plots stored in the supplied notebooks. Stored plots report the provided runs; the large notebook experiments were not re-executed. Figures and code are study aids, not evidence of a globally optimal partition or a well-mixed chain.

> [!code]- Using the examples
> Examples use Python, NumPy, NetworkX, SciPy, Matplotlib and (for clustering/AUC) scikit-learn. Read code boxes within each chapter in order and observe any stated cross-note dependency. The ERGM example uses functions from **Monte Carlo sampling**. The pseudolikelihood chapter explains how to reuse that sampler.
>
> The notes are readable without running code or installing Obsidian community plugins. Keep the `Assets` directory beside the Markdown files so diagrams remain available. Revision lists are prompts for active recall; they are not predictions of examination questions or marking criteria.
