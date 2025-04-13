- We often model random quantities that take a continuous set of possible values. e.g. lifetime, temperature, height of individuals, etc.
- In this case the [[Probability Mass Function|pmf]] cannot be used to specify such a distribution. In fact for such RVs usually $P(X=x) = 0$ for all $x \in X(\Omega)$. We need [[Cumulative Distribution Function | CDF]].

>[!info] Definition
>An RV $X: \Omega \to \mathbb{R}$ with CDF $F$ is called a **continuous RV** if there exists an integrable function $f \leq 0$ called the *density*, aka the **pdf (probability density function)** of $X$ such that
>$$F(x) = \int_{-\infty}^x f(x') dx'$$

# Comments on Properties

For continuous RV $X$ with CDF $F$ and pdf $f$,

1. $X$ is absolutely convergent
2. $f$ is not uniquely defined, but it is unique whenever it is continuous. 
3. $F$ is a cont. function, and by Fundamental theorem of calculus, for any $x$ where $f$ is cont. at $x$, $F'(x) = f(x)$.
4. If $F_X$, the CDF of some RV $X$, is differentiable and $f = F_X'$ is Riemann-integrable, then $X$ is a cont. RV and $f$ is its density (same holds if $F_X$ is cont. and differentiable everywhere except on a finite set of points).
5. *What can we compute with the density?*
	 For $a,b$,  
$$\begin{align*}
\int_a^b f(t)\:dt &= \int_{-\infty}^b f(t)\:dt - \int_{-\infty}^a f(t)\:dt \\[5pt]
&= F(b) - F(a) \\[5pt]
&= P(X\leq b) - P(X \leq a) \\[5pt]
&= P(X \in [a,b])
\end{align*}$$
$\implies$ For any (measurable) set $B \subset \mathbb{R}$, $P(X \in B) = \int_B f(t) \: dt$.  
**$\implies f$ determines the distribution of $X$**

6. See below
>[!tip] Claim
>For *any* RV $X$, and $b \in \mathbb{R}$, 
>$$P(X=b) = F(b) - \lim_{n\to\infty} F(b - \tfrac{1}{n}) = F(b) - F(b^-)$$
>![[Pasted image 20250413214540.png]]

---

>[!tip] Corollary
>a. $P(X=b) = 0$ if $F$ is continuous at $b$.
>b. If $X$ is a cont. RV then for any $x \in \mathbb{R}$, $P(X=x) = 0$. 

