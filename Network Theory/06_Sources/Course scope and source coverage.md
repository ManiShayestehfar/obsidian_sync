---
type: study-note
tags: [DATA5441]
---

# Course scope and source coverage

[[00_HOME]]

The requested unit is [DATA5441 — Networks and High-dimensional Inference](https://www.sydney.edu.au/units/DATA5441), with the supplied [2026 Semester 2 offering link](https://www.sydney.edu.au/units/DATA5441/2026-S2C-ND-CC). The general university page describes mathematical network models, datasets, computation and critical model evaluation. The specific offering’s detailed outline was not retrievable during this work, and the general page did not provide a confirmed 2026 assessment schedule. Assessment weights, exam format and later-week requirements are therefore not inferred from last year’s notes.

The supplied 2026 lecture/tutorial files are the authority for this vault’s weekly coverage.

| Week | Lecture PDF pages | Notebook cells | Main topic |
| --- | ---: | ---: | --- |
| 1 | 14 | 32 | Graphs, measurements, sampling |
| 2 | 13 | 51 | Centrality, lattice and random graphs |
| 3 | 15 | 59 | ER models, sparse limit, giant component |
| 4 | 17 | 37 | MCMC, constrained ensembles, configuration model |
| 5 | 12 | 44 | Small worlds, power laws, preferential attachment |
| 6 | 11 | 46 | Metropolis–Hastings, maximum entropy, ERGMs |
| 7 | 16 | 70 | SBM likelihood, optimisation and model selection |
| **Total** | **98** | **339** | |

Every lecture page was visually inspected. Handwriting made the PDFs’ embedded text layers unreliable, so the lecture exports were prepared from page images and mathematical context. Each has a numbered Markdown section and an expandable image of the complete original page. Week 4 page 17 is blank and is identified as such. Week 5 page 6 contains an embedded article: its content is summarised, and the complete supplied page remains visible. An ambiguous Facebook edge count on Week 4 page 1 is explicitly left unresolved. Plotted curves and drawings are retained in the images, with their mathematical point described in text; plots were not digitised into invented numerical datasets.

The lecture text is a checked mathematical transcription and paraphrase, not a character-for-character archival transcription. Spelling and notation are normalised; substantive corrections and added derivations are labelled. [[Corrections and caveats]] records the main differences.

All 339 notebook cells are represented in order in the seven source exports. Python and Markdown source, stored text/table representations and available image outputs are retained. Original notebooks and their supplied input/cached files are in `06_Sources/Notebooks`. Interactive HTML/JavaScript output is not guaranteed to run in Obsidian; open the original notebook for that behaviour. Stored outputs are historical supplied results, not fresh computation.

The student LaTeX is converted into 13 weekly source notes with a warning about its status. The original TeX is retained. Four referenced external figures were absent from the supplied archive: `imgs/watts-strogatz.png`, `imgs/mesoscale.png`, `imgs/simAnn.png`, and `imgs/image.png`. Their absence is labelled; fenced TikZ source is retained where the Markdown renderer cannot reproduce it. Weeks 8–13 have no supplied 2026 lecture or tutorial corroboration.

The textbook was consulted in the sections relevant to these topics; see [[Newman reading map]]. It has not been transcribed in full. File hashes in `source_manifest.json` identify the supplied sources used.

Focused arithmetic and small-graph checks are recorded in [[Validation report]]. The full expensive simulation notebooks were not executed end to end, and no claim of such execution is made.
