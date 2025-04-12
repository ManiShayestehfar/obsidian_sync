- Suppose $X$ and $Y$ are jointly distributed discrete RVs. Then $\forall x \in X(\Omega)$, the **conditional distribution/pmf** of $Y$ given $X=x$:
$$P_{Y|X}(y|x) = P(Y=y|X=x)$$

**Some Properties:**
$$P(Y=y|X=x) \geq 0$$
$$\sum_y P(Y=y|X=x) = 1$$

>[!info] Definition
>The **conditional [[Expectation|expectation]]** of $Y$ given $X=x$ is
>$$E(Y|X=x) = \sum_y y \:P(Y=y|X=x)$$
>*provided that* the sum is well defined (order invariant)

![[Pasted image 20250411103343.png]]


# Example

-  Roll a fair die and let $Y$ = outcome and $X=1_{\{\text{even outcome}\}}$
	- Suppose $A \subset \Omega$
	- For $A = \{1,3,5\}$, $X=0 \implies E(Y|X=0) = 3$
	- For $A = \{2,4,6\}$, $X = 1\implies E(Y|X=1) = 4$


# Well-Defined-ness

- *How to guarantee the existence of conditional expectation?*

1. Split the sum into negative and positive sums and analyse as per unconditioned expectation
2. If $y \geq 0$, then $\forall x \in X(\Omega)$, $P(Y=y|X=x)=0$ for all $y <0$. Hence the condition holds by property of positive series (same applies for $y \geq 0$)
3. See below:
>[!tip] Claim
>If $y \in L^1$, then $\forall x \in X(\Omega)$, $E(Y|X=x)$ is well-defined and real.
##### Proof
$$\begin{align*}
\sum_y |y| P(Y=y|X=x) &= \sum_y |y| \frac{P(Y=y, X=x)}{P(X=x)}\\[4pt]
&\leq \frac{1}{P(X=x)} \sum_y |y| \cdot P(Y=y)\\[4pt]
&\leq \infty 
\end{align*}$$
The 1st equality holds as $P(X=x)\neq 0$, and the 2nd equality holds as $P(Y=y) \geq P(Y=y,X=x)$. Then

$$\implies \left|\sum_y y\:P(Y=y|X=x)\right| \:\:\leq\:\: \sum |y| \:\:P(Y=y|X=x)\:\:\leq\:\: \infty$$
$\square$ 


# Variance of means

What is $V[E(Y|X)]$?
## Faulty Monitor Examples

$N \sim \text{Poisson}(\lambda), \quad X_i \sim \text{Bernoulli}(p)$ where $T = \sum_1^N X_i$. 
- $\implies T \sim \text{Poisson}(\lambda p) \implies Var(T) = \lambda p$

$$\begin{align*}
V[E(T|N)] &= V[NE(X_i)] \\[3pt]
&= p^2 V(N)\\[3pt]
&= p^2\lambda\\[3pt]
&\leq p\lambda \tag{Since $p \in (0,1)$} \\[3pt]
&= V(T)
\end{align*}$$
**Why does this make sense?** Averaging by reducing the sample size to $T|N$ reduces the variance

