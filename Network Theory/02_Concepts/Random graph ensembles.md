---
type: study-note
tags: [DATA5441]
---

# Random graph ensembles

[[00_HOME]]

Sources: Weeks 3–4 and 6; Newman Chapters 11–12.

| Model | Fixed exactly | Random | Key use |
| --- | --- | --- | --- |
| Uniform all simple graphs | $N$ | Each dyad Bernoulli$(1/2)$ | Maximum-entropy baseline with only $N$ |
| $G(N,q)$ | $N,q$ | Edges independently present | Expected-density baseline |
| $G(N,L)$ | $N,L$ | Locations of exactly $L$ edges | Edge-count controlled baseline |
| Uniform simple fixed degrees | Every labelled vertex degree | Allowed edge wiring | Test structure beyond degrees |
| Stub configuration model | Stub count at each vertex | Pairing, including possible defects | Analytically tractable degree baseline |
| WS | $N$, initial ring parameter, edge count | Rewiring | Clustering plus shortcuts |
| BA | Growth rule and attachment parameter | Attachment histories | Degree heterogeneity through growth |
| ERGM | Chosen support and parameters | Weighted graphs | Match expected statistics |
| SBM | Allocation and block probabilities when generating | Independent dyads conditional on blocks | Mesoscale inference |

With $Y=\binom N2$, there are $2^Y$ simple labelled graphs and $\binom YL$ with $L$ edges. In $G(N,q)$,
$$P(g)=q^{L(g)}(1-q)^{Y-L(g)},\quad L\sim\mathrm{Binomial}(Y,q),\quad K_i\sim\mathrm{Binomial}(N-1,q).$$
Conditioning $G(N,q)$ on its edge count yields the uniform $G(N,L)$ distribution for $0<q<1$. The unconditional models are not identical.

Dense limit: fixed $q>0$, so mean degree is order $N$. Sparse limit: $q=c/(N-1)$, so mean degree is $c$ and $K_i$ converges in distribution to Poisson$(c)$. A finite graph remains binomial.

The two vertex degrees at the ends of an edge are not independent measurements of graph structure merely because dyad indicators are independent. Shared-edge contributions create dependence between degrees.

**Model critique:** matching an observed mean does not show that the model explains the data. Fit chosen statistics, then test other structure. Specify whether a discrepancy is measured against ensemble spread or uncertainty in the estimated ensemble mean; see [[Simulation and uncertainty]].
