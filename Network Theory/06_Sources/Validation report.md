---
type: validation
---

# Validation report

[[00_HOME]] · [[Course scope and source coverage]]

Preparation date: 22 September 2026.

All 98 lecture pages were visually inspected, and every page has a numbered export section and its source image. The seven original notebook files were compared byte-for-byte with the supplied copies. All 339 cells are represented in the source exports, and every code-cell source string is retained. Lecture and notebook image files were checked for successful decoding. Internal note/image links and local Markdown image paths were checked; no unresolved deliverable links remain.

Focused calculations verified the short worked examples independently of the long simulation runs:

| Check | Computed value |
| --- | --- |
| Tutorial 1: N, L, diameter, hub C, mean C, transitivity | `[6, 7, 2, 0.2, 0.7000000000000001, 0.42857142857142855]` |
| Tutorial 2: diagonal-grid L, diameter, mean distance, mean C, transitivity | `[20, 2, 1.4444444444444444, 0.7587301587301587, 0.6]` |
| WS ring Q=1: local clustering | `0.0` |
| WS ring Q=2: local clustering | `0.5` |
| WS ring Q=3: local clustering | `0.6` |
| WS ring Q=4: local clustering | `0.6428571428571429` |
| Worked SBM negative log-likelihood | `4.612909758082266` |
| Tutorial 1 strict graph-count inequality: minimum N | `12` |
| ER giant fraction at c=2 | `0.7968121300` |
| ER giant fraction at c=3 | `0.9404797907` |
| Tutorial 7 NLL: one group, random seed 13, club split | `[np.float64(226.20209580225185), np.float64(224.08815629080152), np.float64(198.49936742452917)]` |

The Karate likelihood check executes only the supplied small likelihood functions on the three specified fixed partitions. The grid, ring and quiz examples use direct NetworkX graph measurements. These checks support the stated arithmetic; they do not validate all source code or establish any MCMC mixing claim.

**Limits:** the notebooks were not executed end to end; cached plots are labelled as supplied results. Four student figures are missing from the original archive. Ambiguous handwriting and substantive mathematical corrections are called out in the lecture exports. Later student-only weeks have been converted and selected errors flagged, but they are not certified as a current-course textbook. Obsidian-specific interaction was not tested in the desktop app; the vault uses standard Markdown, dollar-delimited mathematics, wikilinks and callouts without plugins.
