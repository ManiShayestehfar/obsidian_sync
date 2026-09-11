The review is categorised as: Comment, Typo, or Suggestions.


## Major mathematical / theoretical issues

Comment (Page 3, Proposition 3; proof on Page 11): Proposition 3 appears to omit an $O(n^{-1})$ variance term from model misspecification. Writing $A=(I-\Pi_k)W^\star$, the effective residual is $Ax+\sigma\xi$, not just $\sigma\xi$. Although $\mathbb E[x^\top B_a^\top Ax]=0$, this term generally has non-zero variance. The risk should therefore contain an additional $k$-dependent contribution beyond $\sigma^2p_k/n$.

Comment (Page 11, Proof of Proposition 3): The statement that the constrained estimator is “unbiased for $\Pi_kW^\star$” is not established by showing that the omitted component has mean-zero population score. The argument shows that $\Pi_kW^\star$ is the population least-squares solution, but finite-sample unbiasedness needs a separate proof.

Comment (Page 3, Proposition 3): A simple $d=2$ example already gives a non-zero variance contribution from the symmetry-breaking component, even when it is Frobenius-orthogonal to $V_k$. This suggests the missing term in Proposition 3 is genuine rather than a technicality.

Suggestion (Page 3, Proposition 3): Replace Proposition 3 with the corresponding misspecified-regression expansion
$$
\mathbb E\|\widehat W_k-W^\star\|_F^2
=
\delta_k^2+\frac{\sigma^2p_k+\tau_k(A)}{n}+o(n^{-1}),

$$
and then analyse $\tau_k(A)$ under the generic random-defect model.


Comment (Page 4, Theorem 5): Once the missing variance term is included, the expected risk is no longer exactly affine in $1/k$. Thus the current proof of Theorem 5 does not go through as written.

Suggestion (Page 4, Theorem 5): The endpoint-optimality conclusion may still survive after correcting Proposition 3. I recommend reformulating and reproving the theorem using the corrected risk rather than relying on exact affineness.

Comment (Page 4, Theorem 5): Proposition 3 is asymptotic in $n$, but Theorem 5 claims validity “for any $(n,\varepsilon,\sigma,d)$”. This is stronger than what the stated asymptotic risk expansion supports.


Comment (Page 4, Theorem 5): Proposition 4 is an expectation over random $R$, so Theorem 5 should make clear whether its expectation is over the training data only or over both the training data and $R$.


Comment (Page 3 and Page 5): In Sections 4.1–4.2 the symmetry-breaking direction $R$ is fixed, whereas Proposition 4 is an ensemble statement over random $R$. The text should distinguish the empirical fixed-$R$ experiments from the $R$-averaged theoretical statement.


Comment (Page 4, Corollary 6): The phase boundary
$$

n^\star=\frac{\sigma^2d(d-1)}{\varepsilon^2}

$$
should not be presented as an exact finite-sample transition. The $\varepsilon^{-2}$ scaling appears to remain correct at leading order, but the boundary itself receives lower-order corrections.

  
Suggestion (Page 4, Corollary 6): State the transition asymptotically as
$$

n^\star\sim\frac{\sigma^2d(d-1)}{\varepsilon^2},

$$
unless an exact finite-sample calculation is provided.

## Claims of exactness

Comment (Page 2, Contributions, Item 1): The paper calls $\delta_k^2+\sigma^2p_k/n$ an “exact excess-risk decomposition”, but Proposition 3 itself contains an $o(1)$ term. This should be described as asymptotic rather than exact.

Comment (Page 8, Related Work): The statement that the paper has “closed-form non-asymptotic expressions” is inconsistent with Proposition 3, which is explicitly asymptotic.

Comment (Page 8, Related Work): The phrase “exact closed-form solution to the model selection problem” is too strong in the current version. The result is at best asymptotic under the stated assumptions.

Comment (Pages 8–9, Limitations): The claim that the assumptions make “Propositions 1–4 exact” is incorrect because Proposition 3 is not exact.

  

## Proposition 4 and generic symmetry breaking

Comment (Pages 3–4, Proposition 4): Proposition 4 itself appears correct, but it is an ensemble-average statement over isotropic random $R$. Individual defect realisations need not follow the affine profile exactly.

Suggestion (Page 4, after Proposition 4): The phrase “no dependence on the specific structure of $R$” should be qualified. The expectation is direction-independent because $R$ is isotropic, but individual realisations do depend on $R$.

Suggestion (Page 4, after Proposition 4): “Codimension of $V_k$ within $V_d^\perp$” is imprecise because $V_k$ is not a subspace of $V_d^\perp$. The relevant object is $V_k^\perp\subseteq V_d^\perp$.

## Structured-defect experiment

Comment (Pages 6–7, Section 4.3 / Figure 3): The paper says the optimum “halts at the true symmetry group of the target” at $k=4$. However, since $c\neq0$ and $u_1\in V_4^\perp$, the constructed target is not actually $C_4$-equivariant. It is only approximately $C_4$-equivariant.

Suggestion (Page 7, Section 4.3): Describe the intermediate regime in terms of the defect profile $k\mapsto\delta_k^2$ or the dominant approximate symmetry level, rather than a “true” symmetry subgroup.

## Experimental methodology and interpretation

Comment (Page 5, Section 4.1): “The phase diagram is predicted exactly” is too strong because the theory used is asymptotic. “Predicted by the asymptotic theory” would be more accurate.

Comment (Pages 5–6, Section 4.2): The fitted exponent $-1.92$ is encouraging, but no uncertainty is reported. Please include a standard error or confidence interval for the fitted slope.

Suggestion (Page 6, Table 2): Replace “parameter-free prediction” with “prediction with no fitted parameters”, since the formula still depends on $d$, $\sigma$, and $\varepsilon$.

Comment (Appendix C): The variance check is performed only at $\varepsilon=0.05$, where the missing misspecification contribution should be very small. Repeating this test over several $\varepsilon$ values would provide a much stronger check of Proposition 3.

Suggestion (Appendix B): The experiments add a small ridge term, while the theory concerns unregularised least squares. A zero-ridge sensitivity check in well-conditioned settings would improve the comparison.

Suggestion (Appendix B): The statement that the computational cost is independent of $n$ should be qualified. Solving from sufficient statistics may be independent of $n$, but constructing those statistics still requires processing all samples.

  

## Nonlinear control

Comment (Page 7, Section 4.4): The nonlinear experiment is useful as a qualitative check, but it only shows that the crossover persists in one matched teacher–student tanh setting. It does not establish that the phenomenon is generally independent of linearity.

Suggestion (Page 7 / Appendix B): Clarify how the symmetry-breaking perturbation is introduced into the nonlinear teacher, including whether both layers receive independent defects and how $\varepsilon$ is normalised.

Suggestion (Page 7): It may help to state explicitly why the nonlinear network remains equivariant, namely $\tanh(Sx)=S\tanh(x)$ for the coordinate-wise permutation action.

## Novelty and related work

Comment (Pages 7–8, Related Work): The paper correctly acknowledges that the general approximation–generalisation trade-off under approximate symmetry is not new. The novelty claim should focus on the cyclic subgroup-lattice setting and the endpoint-optimality phenomenon.

Comment (Pages 7–8, Related Work): Christie and Aston, *Estimating maximal symmetries of regression functions via subgroup lattices* (JRSSB, 2025), is relevant and should be discussed. It studies subgroup-lattice symmetry selection from a different statistical perspective.

Comment (Pages 7–8, Related Work): *Any-Subgroup Equivariant Networks via Symmetry Breaking* (ICLR 2026) is also relevant to subgroup-level equivariance and architecture selection and should be discussed.

Suggestion (Pages 7–8, novelty statement): Narrow the novelty claim to the specific cyclic result: generic random defects lead to endpoint-optimal architecture selection and an $\varepsilon^{-2}$ crossover at leading order.

Comment (Page 8): The statement that Theorem 5 has “no counterpart” should be restricted to the precise endpoint-collapse result, not subgroup-lattice symmetry selection more generally.

  

## Scope and interpretation

Comment (Page 9, Conclusion): The “sharp phase transition” language should remain explicitly tied to the paper's assumptions: linear models, cyclic regular representation, isotropic Gaussian inputs, homoscedastic noise, and generic random defects.

Comment (Page 9, Impact Statement): “Choose full equivariance below a critical sample size, and no symmetry above it” is too broad. The paper's own structured-defect experiment shows that intermediate symmetry can be optimal.

Suggestion (Page 9, Conclusion): The statement that sharp transitions may be the rule rather than the exception is speculative. It would be better presented as a conjecture or direction for future work.

  

## Exposition

Suggestion (Page 1, Introduction): Qualify the statement that attention ties weights across permutations. Standard self-attention without positional information is permutation equivariant, but practical transformers often break this symmetry through positional information.

Suggestion (Page 2): Add a small explicit matrix example showing the weight-tying pattern for $k=1$, one intermediate $k$, and $k=d$.

Suggestion (Page 3): When defining $\delta_k^2$, explicitly note that it equals the population approximation error because $x\sim N(0,I)$.

Suggestion (Page 4): At the nominal leading-order boundary, all subgroup architectures tie, rather than only the two endpoints. This is worth stating explicitly.

Suggestion (Page 6, Section 4.3): Briefly explain in the main text that the divisor lattice is not a chain, so incomparable subgroups such as $C_3$ and $C_4$ need not have monotonically ordered defects.


## Typos and local inconsistencies

Typo (Page 2, Contributions, Item 1): The sentence beginning “with $\delta_k$, the symmetry defect…” is grammatically malformed and should be rewritten.

Typo (Page 3): “Proposition (4)” should be “Proposition 4”.

Typo (Pages 3–4, Table 1 discussion): The largest relative discrepancy is approximately $1.37\%$ at $k=3$, not at $k=6$.

Typo (Page 4, Table 1 discussion): The largest absolute discrepancy $0.010$ occurs at $k=3$, not at $k=4$.

Typo (Page 8): “closed, form solution” should be “closed-form solution”.

Typo (Pages 5–6): Use either $n^\star$ or $n^\ast$ consistently.

Typo (Page 9): “matched teacher, student architecture” should be “matched teacher–student architecture”.
