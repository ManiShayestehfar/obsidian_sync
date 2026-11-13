# DATA5441 — Weeks 10–12 (revised Obsidian notes)

This package replaces the eight supplied Markdown files while preserving their original titles, frontmatter, chapter links and related-note wiki-links. All new diagrams live in `Assets/`, referenced as `![[Assets/name.png|width]]` from notes in the same directory. **Copy these files alongside your existing chapter files**, or update the embeds to the path where you store your assets. No replacement for the full vault is implied.

## Recommended study order

| Week | Read in this order | Main exam skill |
|---|---|---|
| **10 — Percolation / resilience** | [[Percolation on lattices]] → [[Percolation and robustness]] | Understand site/bond percolation; derive $p_c$ from branching; calculate $q_c$ from degree moments; distinguish failures from attacks |
| **11 — Cascades / discrete dynamics** | [[Binary-state dynamics]] → [[Threshold model and cascades]] → [[SI and SIS models]] | Specify an update algorithm; explain consensus versus cycles; identify vulnerable nodes and cascades; distinguish finite SIS extinction from mean-field persistence |
| **12 — Continuous dynamics / games** | [[SIR model and epidemic threshold]] → [[Evolutionary games on networks]] → [[Synchronisation and stability]] (supplementary) | Derive homogeneous and degree-based epidemic thresholds; explain percolation analogy; calculate payoffs and strategy updates; understand Laplacian modes if assessed |

## Sources and methodological notes

**Primary source:** *DATA5441 Lecture Notes 2026*, Week 10 pp. 128–143, Week 11 pp. 144–150 and Week 12 pp. 151–167, with **Tutorial 10 (completed)** and **Tutorial 11** supplied in the notebooks ZIP. Material labelled *supplementary* in `Synchronisation and stability.md` comes from Jeny Yuan's course notes from the previous year; it is not documented as a worked derivation in the 2026 lecture-notes PDF. No Week 12 notebook was present in the supplied notebook bundle.

The notes include several **explicit qualifications** where classroom shortcuts should not be mistaken for general theorems:

1. The Watts vulnerable-cluster criterion needs a branching factor with the mean degree of the **original** network in the denominator. A moment ratio using original degrees of vulnerable nodes alone is not a generally valid site-percolation test.
2. The order-1 **degree-based SIR mean-field threshold** and the **edge-based percolation threshold** need not be identical for finite degree moments. Transmission probability and the exclusion of the arrival edge matter.
3. SIS's endemic mean-field fixed point describes a large-network/finite-time approximation; **finite closed SIS** almost surely reaches the disease-free absorbing state.
4. The supplementary diffusion and Kuramoto formulas use a consistent **attractive-coupling sign** and explicitly describe the sign/normalisation convention; the 2026 PDF does not provide these proofs.
5. Finite-network simulation illustrations are marked as such. They should not be treated as exact critical curves or a substitute for ensemble averages.

## Figures

| Figure | Used in | What it illustrates |
|---|---|---|
| `w10-site-percolation.png` | Percolation on lattices | Coupled site-percolation realisation at three $p$ values |
| `w10-robustness-curves.png` | Percolation and robustness | ER and BA edge failures, with ER theoretical threshold |
| `w11-update-schedules.png` | Binary-state dynamics | Synchronous cycle versus asynchronous consensus |
| `w11-threshold-cascade.png` | Threshold model and cascades | Same graph, different threshold, different outcome |
| `w11-si-sis-meanfield.png` | SI and SIS models | Homogeneous mean-field infection curves |
| `w12-sir-threshold.png` | SIR model and epidemic threshold | SIR trajectories and order-0 final-size transition |
| `w12-game-hubs.png` | Evolutionary games | Cooperative and defecting hub payoffs |
| `w12-diffusion-synchronisation.png` | Synchronisation and stability | Consensus diffusion and Kuramoto phase coherence |

Every image is a newly generated explanatory visual, not an imported empirical plot. The source code for reproducing the figures is included under `Figures_source/generate_figures.py` (requires `numpy`, `scipy`, `networkx` and `matplotlib`).
