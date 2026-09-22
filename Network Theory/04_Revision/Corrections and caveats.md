---
type: study-note
tags: [DATA5441]
---

# Corrections and caveats

[[00_HOME]]

This note separates mathematical corrections from mere differences in notation. Source exports retain original content where appropriate; study notes use the corrected form. This is not an assertion that every error in the later student-only material has been found.

| Source | Issue | Use instead |
| --- | --- | --- |
| Week 1 terminology / student Week 1 | “Path” sometimes allows repetitions; “loop” sometimes means cycle | State conventions; $A^r$ counts walks; a tree is connected and acyclic |
| Week 2 spectral discussion | Connectedness taken to imply a strict spectral-modulus gap | Bipartite connected graphs also have eigenvalue $-\lambda_1$ |
| Week 2 Katz formula | Missing or ambiguous matrix inverse | $(I-\alpha A)^{-1}\mathbf1$, with $\alpha\rho(A)<1$ |
| Sampling examples | Random neighbour treated as uniform edge endpoint | Identify the sampling protocol; see [[Sampling and friendship paradox]] |
| Week 3 approximations | Exact finite graph and sparse limiting claims mixed | Binomial before Poisson; giant component does not mean connected |
| ER clustering | $q$ used for every definition of expected clustering | Conditional local mean is $q$; all-vertex mean includes $\Pr(K\ge2)$ |
| Week 4 convergence | Reachability and detailed balance without aperiodicity | Pure edge-flip chain has period two; add holding or resample a dyad |
| Week 4 one-step condition | $L$ differs by one used as enough for an edge flip | The adjacency indicators must differ at exactly one dyad |
| Configuration model | $k_i k_j/(2L-1)$ called an edge probability | It is expected multiplicity; simplicity approximation needs assumptions |
| Week 5 p.8 | Maximum estimated with probability mass $p(k_{max})\sim1/N$ | Use survival tail: $N\Pr(K\ge k_{max})\sim1$ |
| Week 5 preferential-attachment density | Derivative of survival function without minus sign | Density is minus its derivative |
| Week 5 clustering sketch | A single decay power treated as a universal BA law | State qualitative vanishing; $m=1$ tree case has zero clustering |
| Week 6 graph weighting | Expectation constraint read as exact per-graph equality | Graphs fluctuate around the fitted expected statistic |
| Week 6 swap discussion | Repeated successful swaps assumed exactly symmetric | Use the single-attempt kernel or derive the Hastings ratio |
| Week 7 likelihood | Edge counts used as number of observations | Include all possible dyads and non-edges |
| Week 7 degree correction | Product of degrees used as an unrestricted probability | Distinguish a Poisson intensity from a bounded Bernoulli probability |
| Week 7 Bayes formula | Evidence sign ambiguous/wrong in a log expression | $\log\text{posterior}=\log\text{likelihood}+\log\text{prior}-\log\text{evidence}$ |
| Week 7 model selection | Best profiled fit described as exact Bayesian evidence | Sum over allocations and integrate probabilities for full evidence |
| Tutorial 7 cell 22 | Ratio of expectations labelled expected transitivity | It is generally an approximation to expectation of the ratio |
| Tutorial 7 cells 9,44 | List-only likelihood receives NumPy array | Move/adapt the general likelihood from cell 47 before MCMC |
| Tutorial 7 cell 59 | Seed 5441 used where exercise asks for 13 | Use explicit `seed=13` for that requested dataset |

See the individual tutorial guides for runtime issues, cached files, row-versus-step burn-in, and plotting details.

**Later student notes: use with particular care.**

- Week 9’s Ising reconstruction discussion drops a normalising factor that generally depends on the graph. For $P(s\mid g)=e^{-E_g(s)}/Z(g)$, the negative log-likelihood includes $\log Z(g)$ for each observation. Minimising observed energy alone is not generally maximum-likelihood graph inference. The same section repeats the incorrect positive sign for log evidence and confuses a negative log posterior with a log posterior.
- Week 10 writes a maximum-degree scale with a negative power of $N$ in its targeted-removal discussion. The independent-tail natural maximum grows as $N^{1/(\gamma-1)}$; dependent graph constraints can change the regime.
- Week 13’s removal threshold has misplaced parentheses. For independent uniform bond retention on a suitable locally tree-like configuration model, $p_c=\langle k\rangle/(\langle k^2\rangle-\langle k\rangle)=1/\kappa$. If $q$ denotes removal, $q_c=1-p_c$, assuming the original graph is supercritical. This is not a formula for arbitrary targeted attacks or arbitrary clustered graphs.
- Week 11’s “all viruses lead to an outbreak” overstates an asymptotic zero-threshold result. Outcomes depend on model, finite size, parameters and stochastic extinction. Keep SI, SIS and SIR distinct; a homogeneous mean-field threshold is not automatically an exact network threshold.
- Week 12 contains inconsistent diffusion and stability signs. With $L=D-A$, diffusion with positive rate is $\dot x=-\beta Lx$. If a linearisation is $\dot\epsilon=(\alpha I+\beta L)\epsilon$, asymptotic stability requires $\alpha+\beta\lambda_r<0$ for every mode. If the matrix is $\alpha I-\beta L$, its eigenvalues are $\alpha-\beta\lambda_r$. One cannot mix these conventions.
- “Exam key facts” in the student’s final section describes the prior offering, not a verified 2026 assessment guide.
