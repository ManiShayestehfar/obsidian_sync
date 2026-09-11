The review is categorised as: Comment, Typo, or Suggestions.

## Major mathematical / theoretical issues

  

- Comment (Page 3, Proposition 3; proof on Page 11): The excess-risk decomposition in Proposition 3 appears to omit an $O(n^{-1})$ variance term arising from model misspecification. Let

$$

A=(I-\Pi_k)W^\star,\qquad W_0=\Pi_kW^\star.

$$

Then

$$

y=W_0x+Ax+\sigma\xi,

$$

so the effective regression residual is $Ax+\sigma\xi$, not merely $\sigma\xi$. For an orthonormal basis $B_1,\ldots,B_{p_k}$ of $V_k$, the score contains $x^\top B_a^\top Ax$. Frobenius orthogonality gives

$$

\mathbb E[x^\top B_a^\top Ax]=\langle B_a,A\rangle_F=0,

$$

but this term generally has non-zero variance. Consequently, the asymptotic covariance should contain an additional contribution

$$

Q(A)_{ab}=\mathbb E[(x^\top B_a^\top Ax)(x^\top B_b^\top Ax)],

$$

and the corresponding risk expansion is

$$

\mathbb E\|\widehat W_k-W^\star\|_F^2=\delta_k^2+\frac{\sigma^2p_k+\tau_k(A)}{n}+o(n^{-1}),

$$

where $\tau_k(A)=\operatorname{tr}Q(A)$. The current proof appears to use the fact that the omitted component has zero mean contribution to the normal equations as if it implied zero contribution to the estimator variance. This affects the main risk formula, rather than merely the proof technique.

  

- Comment (Page 11, Proof of Proposition 3): The statement that the constrained least-squares estimator is “unbiased for $\Pi_kW^\star$” is not established by showing that the omitted component has mean-zero population score. Since the finite-sample estimator involves the inverse random Gram matrix $G^{-1}$, one cannot in general replace $\mathbb E[G^{-1}b]$ by $(\mathbb EG)^{-1}\mathbb Eb$. The argument directly establishes that $\Pi_kW^\star$ is the population least-squares solution. The finite-sample unbiasedness claim should either be proved separately or removed.

  

- Comment (Page 3, Proposition 3): A simple $d=2$ example shows that the omitted variance term is genuinely non-zero. For $k=2$, take

$$

B_1=I/\sqrt2,\qquad A=\frac1{\sqrt2}\begin{pmatrix}1&0\\0&-1\end{pmatrix}\in V_2^\perp.

$$

Then

$$

x^\top B_1^\top Ax=\frac12(x_1^2-x_2^2),

$$

which has non-zero variance. Thus the symmetry-breaking component contributes estimation variance even though it is Frobenius-orthogonal to $V_2$.

  

- Suggestion (Page 3, Proposition 3): I recommend replacing Proposition 3 by the appropriate misspecified-regression expansion

$$

\delta_k^2+\frac{\sigma^2p_k+\tau_k(A)}{n}+o(n^{-1}),

$$

and then analysing $\tau_k(A)$ under the isotropic generic-defect ensemble. In the cyclic setting of the paper, this extra calculation appears tractable.

  

- Comment (Page 4, Theorem 5): The stated reason for the all-or-nothing theorem — exact affineness of the expected risk in $1/k$ — does not survive the correction to Proposition 3. After averaging the additional misspecification-variance term over a uniformly random $R\in S(V_d^\perp)$, the risk acquires an additional $k$-dependent term at order $1/n$, including $1/k^2$-type dependence. Thus the claimed exact affineness is not correct at first asymptotic order.

  

- Suggestion (Page 4, Theorem 5): The qualitative endpoint result may nevertheless be salvageable. The corrected generic-risk expansion appears to have the form

$$

\begin{aligned}

\mathbb E_{R,\mathcal D}\|\widehat W_k-W^\star\|_F^2

={}&\varepsilon^2\frac d{d-1}\left(1-\frac1k\right)+\frac{\sigma^2d^2}{nk}\\

&+\frac{\varepsilon^2}{n}\frac{d[(k-1)(d+1)-\chi_k]}{k^2(d-1)}+o(n^{-1}),

\end{aligned}

$$

where $\chi_k=1$ for even $k$ and $0$ for odd $k$. The additional term is non-affine but appears to place interior subgroup risks above the endpoint chord, so endpoint optimality may still hold. If confirmed, this would provide a corrected and arguably stronger theorem.

  

- Comment (Page 4, Theorem 5): Proposition 3 is explicitly asymptotic in $n$, with $d,k$ fixed, whereas Theorem 5 claims that no intermediate subgroup is strictly optimal “for any $(n,\varepsilon,\sigma,d)$”. An asymptotic expansion containing an $o(1)$ term does not by itself imply a statement for every finite $n$. The theorem should be stated asymptotically unless an exact finite-$n$ risk identity is provided.

  

- Comment (Page 4, Theorem 5): There is also an expectation-level ambiguity. Proposition 4 gives $\mathbb E_R[\delta_k^2]$ for $R$ uniformly distributed on the unit sphere of $V_d^\perp$; it does not state that every individual random direction has the closed-form defect profile. Theorem 5 should therefore make explicit whether the expectation is over the training data only or over both the training data and $R$. If Proposition 4 is substituted into the risk, the latter appears necessary.

  

- Comment (Page 3, experimental setup; Page 5, phase diagram): The manuscript states that $R$ is fixed in Sections 4.1–4.2 and only the training samples are resampled, whereas Proposition 4 is an ensemble statement over $R$. Thus the 60-cell phase-diagram experiment is not literally evaluating the same $R$-averaged quantity appearing in Proposition 4. It is useful empirical evidence that a particular random realisation behaves similarly, but the text should distinguish these two statements.

  

- Comment (Page 4, Corollary 6): The phase boundary

$$

n^\star=\frac{\sigma^2d(d-1)}{\varepsilon^2}

$$

should not be described as an exact finite-sample transition. Once the missing misspecification variance is retained, there is an $O(1)$ correction to $n^\star$. The leading $\varepsilon^{-2}$ scaling nevertheless appears to survive because near the transition $\varepsilon^2=O(1/n)$, making the omitted term lower order in the local crossover scaling.

  

- Suggestion (Page 4, Corollary 6): I recommend reformulating the main transition result as

$$

n^\star\sim\frac{\sigma^2d(d-1)}{\varepsilon^2}

$$

in an appropriate asymptotic regime, unless an exact finite-$n$ calculation is supplied.

  

## Claims of exactness

  

- Comment (Page 2, Contributions, Item 1): The manuscript refers to $\delta_k^2+\sigma^2p_k/n$ as an “exact excess-risk decomposition”, but Proposition 3 is stated only asymptotically with an $o(1)$ term. Even independently of the missing variance issue, this should be described as an asymptotic expansion rather than an exact identity.

  

- Comment (Page 8, Related Work): The manuscript states that it has “closed-form non-asymptotic expressions” for both the approximation error and the estimation variance, citing Propositions 3 and 4. This is inconsistent with Proposition 3, which explicitly takes $n\to\infty$ and contains an $o(1)$ term.

  

- Comment (Page 8, Related Work): The assertion that the paper provides an “exact closed-form solution to the model selection problem” is too strong in the current version. At best, the manuscript provides an asymptotic model-selection criterion under the stated idealised assumptions.

  

- Comment (Pages 8–9, Limitations): The statement that the four modelling assumptions make “Propositions 1–4 exact” is incorrect because Proposition 3 itself is stated asymptotically.

  

## Proposition 4 and “generic” symmetry breaking

  

- Comment (Pages 3–4, Proposition 4): The dimension-counting calculation in Proposition 4 appears correct:

$$

\mathbb E_R\delta_k^2=\varepsilon^2\frac d{d-1}\left(1-\frac1k\right).

$$

However, the surrounding text should make clearer that this is an ensemble-average statement over an isotropically random direction in $V_d^\perp$. Individual realisations need not have the affine defect profile exactly.

  

- Suggestion (Page 4, discussion after Proposition 4): I would avoid saying that the result has “no dependence on the specific structure of the symmetry-breaking direction $R$”. The expectation has no dependence on a preferred direction because $R$ is isotropic; individual values certainly depend on the realised direction.

  

- Suggestion (Page 4, discussion after Proposition 4): The phrase “codimension of $V_k$ within $V_d^\perp$” is geometrically imprecise because $V_k$ is not a subspace of $V_d^\perp$. The relevant object is $V_k^\perp\subseteq V_d^\perp$, whose dimension determines the projected energy.

  

## Structured-defect experiment

  

- Comment (Pages 6–7, Section 4.3 / Figure 3): The paper states that the optimum “halts at the true symmetry group of the target” at $k=4$. However, the constructed target is

$$

W^\star=u_{12}+bu_4+cu_1,

$$

with $u_1\in V_4^\perp$ and $c=0.08\neq0$. Therefore $W^\star\notin V_4$, so $C_4$ is not the true symmetry group of the target. The target is instead approximately $C_4$-equivariant and much closer to $V_4$ than to $V_{12}$. The wording should be changed accordingly.

  

- Suggestion (Page 7, interpretation of Section 4.3): The structured-defect experiment may be clearer if framed directly through the profile $k\mapsto\delta_k^2$, rather than in terms of recovering a “true” subgroup. This would avoid implying exact residual symmetry when the target deliberately contains lower-symmetry components.

  

## Experimental methodology and interpretation

  

- Comment (Page 5, Section 4.1): “The phase diagram is predicted exactly” is too strong given that the risk formula being compared is asymptotic. “Predicted by the asymptotic theory” would be more accurate.

  

- Comment (Pages 5–6, Section 4.2): The fitted exponent $-1.92$ is encouraging, but the paper reports no uncertainty for the fitted slope. Since the crossover is discretised to the first point on a 60-point logarithmic $n$-grid and only nine $\varepsilon$-values are used, the regression should report at least a standard error or confidence interval for the fitted exponent.

  

- Suggestion (Page 6, Table 2): “Parameter-free prediction” may be misleading because the expression depends on $d,\sigma,\varepsilon$. Presumably the intended meaning is “no fitted parameters”; I suggest using that wording.

  

- Comment (Appendix C): The manuscript checks the variance coefficient only at $\varepsilon=0.05$, $n=4000$, where the missing misspecification contribution is expected to be very small. This is not a strong diagnostic for the issue in Proposition 3. A more informative check would repeat the variance measurement over several $\varepsilon$-values at fixed large $n$, or directly examine

$$

n\left(\mathbb E\|\widehat W_k-W^\star\|_F^2-\delta_k^2\right)-\sigma^2p_k

$$

as a function of $\varepsilon^2$.

  

- Suggestion (Appendix B): The implementation adds a relative ridge term of $10^{-8}\operatorname{tr}(G)/p_k$, while the theory concerns unregularised constrained least squares. The ridge is extremely small, but a zero-ridge sensitivity check in well-conditioned regimes would make the comparison cleaner.

  

- Suggestion (Appendix B): The statement that the constrained least-squares “cost is independent of $n$” should be qualified. The solve from the sufficient statistics may be independent of $n$, but constructing $X^\top X$ and $Y^\top X$ still requires processing all $n$ observations.

  

## Nonlinear control

  

- Comment (Page 7, Section 4.4): The nonlinear experiment is useful as a qualitative sanity check, and the manuscript appropriately avoids fitting an exponent from five seeds and four sample sizes. However, the phrase “to check that the crossover is not an artefact of linearity” is somewhat too strong. The experiment shows that the phenomenon persists in one matched nonlinear teacher–student setting, not that linearity is irrelevant more generally.

  

- Suggestion (Page 7 / Appendix B): Please specify more clearly how the symmetry-breaking perturbation is introduced into the nonlinear teacher. “Teacher weights drawn as in (2)” leaves ambiguity as to whether both $W_1$ and $W_2$ receive independent perturbations, share a defect direction, and how $\varepsilon$ is normalised across the two layers.

  

- Suggestion (Page 7): Since the nonlinear equivariance argument relies on the coordinate-wise nonlinearity commuting with the cyclic permutation action, it may help to state explicitly that

$$

\tanh(Sx)=S\tanh(x).

$$

  

## Novelty and related work

  

- Comment (Pages 7–8, Related Work): The manuscript correctly acknowledges that the general approximation–generalisation trade-off under approximate symmetry is not itself novel. I recommend keeping the novelty claim narrowly focused on the cyclic subgroup-lattice setting and the endpoint-optimality phenomenon.

  

- Comment (Pages 7–8, Related Work): A relevant recent omission is Christie and Aston, *Estimating maximal symmetries of regression functions via subgroup lattices* (JRSSB, 2025). That work explicitly organises candidate symmetries through a subgroup lattice and develops a statistical procedure for selecting maximal symmetry. It is not the same problem — their objective is symmetry estimation rather than architecture-risk minimisation — but it is conceptually close enough to merit discussion.

  

- Comment (Pages 7–8, Related Work): The manuscript should also discuss *Any-Subgroup Equivariant Networks via Symmetry Breaking* (ICLR 2026), which studies architectures supporting arbitrary subgroup equivariance and includes subgroup/symmetry selection. The contribution is technically different from the closed-form risk analysis here, but it is directly relevant to broader claims about subgroup-level architecture selection.

  

- Suggestion (Pages 7–8, novelty statement): I recommend narrowing the novelty claim to the specific result that is genuinely distinctive here: under an isotropic random defect in the cyclic regular representation, the subgroup-indexed risk exhibits endpoint optimality and an $\varepsilon^{-2}$ transition.

  

- Comment (Page 8): The statement that Theorem 5 has “to our knowledge, no counterpart” may be reasonable if restricted to the precise endpoint-collapse theorem. It should not be used to imply novelty of subgroup-lattice symmetry selection more broadly.

  

## Scope and interpretation

  

- Comment (Page 9, Conclusion): The conclusion repeatedly describes the transition as a “sharp phase transition” and the subgroup lattice as collapsing to its endpoints. This is reasonable within the idealised model, but the mathematical scope should remain explicit: cyclic regular representation, isotropic Gaussian inputs, homoscedastic noise, linear hypothesis classes, and generic defects averaged over $R$.

  

- Comment (Page 9, Impact Statement): The recommendation to “choose full equivariance below a critical sample size, and no symmetry above it” is too broad without qualification. The paper's own structured-defect experiment demonstrates a setting where this prescription fails. The statement should explicitly be restricted to the generic cyclic linear model analysed in the paper.

  

- Suggestion (Page 9, Conclusion): The final statement that “sharp transitions rather than smooth interpolations may be the rule rather than the exception when symmetries are discrete” is interesting but not established by the present results. The manuscript itself notes that the dimension-counting cancellation may be special to the cyclic regular representation. I recommend presenting this as a conjectural direction rather than a conclusion.

  

## Exposition

  

- Suggestion (Page 1, Introduction): The statement that “attention ties [weights] across permutations” should be qualified. Standard self-attention without positional information is permutation equivariant, whereas practical transformers commonly introduce positional information that breaks that symmetry.

  

- Suggestion (Page 2, architecture family): An explicit small matrix example, for example $d=6$ or $d=12$, illustrating the orbit-tying patterns for $k=1$, an intermediate $k$, and $k=d$ would make the “symmetry budget” interpretation more intuitive.

  

- Suggestion (Page 3): When defining

$$

\delta_k^2=\|(I-\Pi_k)W^\star\|_F^2,

$$

it would help to state explicitly that this equals the population approximation error because $x\sim N(0,I)$:

$$

\mathbb E\|(W^\star-\Pi_kW^\star)x\|^2=\delta_k^2.

$$

  

- Suggestion (Page 4): At the nominal boundary where the leading affine term is constant in $1/k$, all subgroup architectures tie at leading order, rather than only the two endpoints. Since Theorem 5 says that no intermediate subgroup is *strictly* optimal, this is not a contradiction, but spelling it out would improve clarity.

  

- Suggestion (Page 6, Section 4.3): The non-chain nature of the divisor lattice is important. Since $C_3$ and $C_4$ are incomparable, quantities such as $\delta_3$ and $\delta_4$ need not be monotonically ordered. A short explanation in the main text would help readers interpret Figure 3.

  

## Typos and local inconsistencies

  

- Typo (Page 2, Contributions, Item 1): The sentence beginning “with $\delta_k$, the symmetry defect…” is grammatically malformed: “building on the parameter count in Propositions 1 and Propositions 2–3 give an exact risk decomposition”. This should be rewritten.

  

- Typo (Page 3): “Proposition (4)” should be “Proposition 4”.

  

- Typo (Pages 3–4, Table 1 discussion): The manuscript states that the largest relative discrepancy is approximately $1.4\%$ at $k=6$. From the displayed table,

$$

\frac{|0.7373-0.7273|}{0.7273}\approx1.37\%,

$$

which occurs at $k=3$, whereas the relative discrepancy at $k=6$ is approximately $0.70\%$.

  

- Typo (Page 4, Table 1 discussion / footnote): The manuscript states that the largest absolute discrepancy $0.010$ occurs at $k=4$. From the displayed values,

$$

|0.7373-0.7273|=0.0100

$$

occurs at $k=3$, whereas the discrepancy at $k=4$ is only

$$

|0.8170-0.8182|=0.0012.

$$

  

- Typo (Page 8): “closed, form solution” should be “closed-form solution”.

  

- Typo (Pages 5–6): Use either $n^\star$ or $n^\ast$ consistently for the crossover sample size.

  

- Typo (Page 9): “matched teacher, student architecture” should be “matched teacher–student architecture”.

  

## Recommended score

  

- Comment (Overall assessment): **4/10 — Weak Reject. Confidence: 4/5.** The paper asks an interesting question and develops a clean subgroup-lattice model, but the main theoretical contribution currently relies on an incomplete first-order risk calculation. This invalidates the claimed exact affineness and leaves Theorem 5 and Corollary 6 unproved as stated. The central qualitative phenomenon nevertheless appears potentially salvageable after correcting the regression theory, so I would regard the work as promising but not yet ready in its present form.


