- We often model random quantities that take a continuous set of possible values. e.g. lifetime, temperature, height of individuals, etc.
- In this case the [[Probability Mass Function|pmf]] cannot be used to specify such a distribution. In fact for such RVs usually $P(X=x) = 0$ for all $x \in X(\Omega)$. We need [[Cumulative Distribution Function | CDF]].

>[!info] Definition
>An RV $X: \Omega \to \mathbb{R}$ with CDF $F$ is called a **continuous RV** if there exists an integrable function $f \leq 0$ called the *density*, aka the **pdf (probability density function)** of $X$ such that
>$$F(x) = \int_{-\infty}^x f(x') dx'$$

