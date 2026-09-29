# Network Theory

A topic-based wiki for DATA5441. Each note combines relevant lectures, Jenny’s supplied notes, textbook explanations and tutorial lessons. Definitions and assumptions precede results; proofs, examples and Python sit beside the concepts they explain.

## Foundations

[[Graphs and representations]] · [[Paths and components]] · [[Clustering]] · [[Centrality]] · [[Sampling and friendship paradox]] · [[Spectral graph theory]]

## Models and computation

[[Random graph ensembles]] · [[Erdos-Renyi graphs]] · [[Configuration model]] · [[Monte Carlo sampling]] · [[Small-world networks]] · [[Power laws]] · [[Preferential attachment]] · [[Maximum entropy and ERGMs]]

## Inference

[[Stochastic block models]] · [[Statistical inference and model selection]] · [[Community detection]] · [[Network reconstruction]]

## Dynamics

[[Percolation and robustness]] · [[Binary dynamics and cascades]] · [[Epidemic models]] · [[Evolutionary games]] · [[Synchronisation and stability]]

> [!info]- Conventions and sources
> Unless a note states otherwise, graphs are finite, simple, undirected and unweighted. $N$ is vertex count, $L$ edge count and $k_i$ degree (the lectures also use $z_i$). Directed examples use $A_{ij}=1$ for $i\to j$. The Laplacian is $\mathcal L=D-A$. Logarithms are natural. Distinguish exact identities, limiting results, approximations and simulation observations.
>
> The source for this reorganisation is the supplied `Network Theory.zip`. Its lecture exports cover Weeks 1–7; later topics come from the student notes and supporting references, with no claim that their scheduling matches the current offering. The student’s author line is Jeny Yuan; these notes are called Jenny’s notes here following your description.
>
> “Newman” means Mark Newman, *Networks*, second edition, Oxford University Press, 2018, supplied PDF. Section references are used throughout; where page numbers appear they are printed pages. Source callouts identify relevant lectures, tutorial lessons and textbook sections. These are integrated study notes rather than verbatim source transcriptions. Corrections are incorporated where they matter, including the source’s power-law cutoff, posterior normalisation, cascade criterion and stability signs.

> [!code]- Using the Python boxes
> Examples use Python with NumPy, NetworkX, SciPy and, in the power-law plot, Matplotlib. Run boxes within a note in order. The ERGM example explicitly reuses the functions in **Monte Carlo sampling**; it is the only cross-note code dependency. Snippets illustrate the specified model and use small built-in or generated graphs, so no original datasets or notebooks are required. All 25 embedded Python boxes were executed during preparation (Python 3, NetworkX 3.7, NumPy 2.3.5, SciPy 1.17.0, Matplotlib 3.10.8). Internal links and code dependencies were checked. Short MCMC demonstrations are not certified mixing runs or fitted empirical results.
>
> Custom callouts such as definition, theorem, proof and code are valid Obsidian callouts and display without community plugins. No custom styling is required. Open this folder as a vault and start with this note.
