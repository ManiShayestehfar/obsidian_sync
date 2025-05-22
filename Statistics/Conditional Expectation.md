>[!info] Definition
>Suppose $X$ and $Y$ are jointly distributed discrete RVs. Then $\forall x \in X(\Omega)$, the **conditional distribution/pmf** of $Y$ given $X=x$:
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


# Continuous Conditional Distribution

Suppose we have $X,Y$ with joint density $f_{XY}$. We want to make sense of $F_{X|Y}(x|y) = P(X \leq x | Y=y)$. But $P(Y=y)$ and so we are dividing by zero! 
$\implies$ need to replace $p_{X|Y}$ with $f_{X|Y} = f_{XY} / f_Y$.

Assume $f_{XY}$ and $f_Y$ are continuous functions and consider $y \in \mathbb{R}$ with $f_Y(y) > 0$, $\forall \delta > 0$,
$$P(Y \in [y,y+\delta]) = \int_{y}^{y+\delta} f_Y(t) \:dt >0$$
$$\begin{align*}
\implies P(X \leq x |y \leq Y \leq y+\delta) &= \frac{P(X\leq x, Y \in [y,y+\delta])}{P(Y \in [y, y+\delta])} \\[7pt]
&= \frac{\int_{-\infty}^x \int_y^{y+\delta} f_{XY}(s,t)\:dt\:ds}{\int_y^{y+\delta} f_Y(t)\:dt}
\end{align*}$$
which is well-defined.

![[Pasted image 20250502225646.png|250]]

![[Pasted image 20250502231155.png]]

Therefore,
$$P(X\leq x | y \leq Y\leq y+\delta) \overset{\delta\to 0}{\longrightarrow} \frac{\int_{-\infty}^x f_{XY}(s,y)\:ds}{f_Y(y)} = \int_{-\infty}^x \frac{f_{XY}(s,y)}{f_Y(y)}\:\:ds$$

>[!info] Definition
>For $y\in \mathbb{R}$ where $f_Y$ is continuous and $f_Y(y) >0$ we define the **conditional distribution** of $X$ given $Y=y$ as the distribution defined by the **conditional CDF**:
>$$F_{X|Y}(x|y) = \int_{-\infty}^x f_{X|Y}(s|y)\:ds$$
>where
>$$f_{X|Y}(x|y) = \frac{f_{XY}(x,y)}{f_Y(y)}$$
>is the conditional density of $X$ given $Y=y$.

--> You can prove $f_{X|Y}(x,y)$ is indeed a density as $\int_{-\infty}^{\infty}f_{X|Y}(x,y) = 1$.


>[!example] Remark
>If $X,Y$ are [[Independent RV|independent RVs]], then
>$$f_{X|Y}(x,y) = \frac{f_X(x)f_Y(y)}{f_Y(y)} = f_X(x)$$

>[!tip] Claim
>If $Y \in L^1$ then for "almost every" $x$ s.t. $f_X(x) > 0$, 
>$$ \int_{-\infty}^\infty |y|\:f_{Y|X}(y|x)\:dy < \infty$$
>
>In particular, for such $X$'s we can define the **conditional expectation** of $Y$ given $X=x$ as 
>$$E(Y|X=x) =  \int_{-\infty}^\infty y\:f_{Y|X}(y|x)\:dy\quad\in \mathbb{R}$$
##### Proof
![[Conditional Expectation-1747780427130.png]]
![[Conditional Expectation-1747780444182.png]]
![[Conditional Expectation-1747780464052.png]]

>[!tip] Claim
>If $X,Y$ are RVs defined on $\Omega$ and $Y \in L^1$ then $E(Y|X)\in L^1$ and 
>$$E[E(Y|X)] = E(Y)$$
##### Proof
If $X,Y$ are jointly cont. with $f_{XY}$ and if $f_X(x) > 0$ then the proof is the same as the discrete case with the replacements $p\to f$, and $\Sigma \to \int$. 


## Examples

### Joint Distribution of an Independent Uniform and Exponential Variables

$f_{XY}(x,y) = \lambda^2 e^{-\lambda y}, \quad y>x \geq 0, \lambda >0$, and we got that
$$f_X(x) = \lambda e^{-\lambda x}\cdot\mathbb{1}_{x\geq0}\:\:, \quad\quad f_Y(y) = \lambda^2 y e^{-\lambda y}\cdot\mathbb{1}_{y>0}$$

![[Pasted image 20250421141832.png|150]]

for $y > 0,$
$$\begin{align*}
f_{X|Y}(x,y) &= \frac{f_{X|Y}(x|y)}{f_Y(y)} \\[6pt]
&= \begin{cases}
\frac{1}{y} & x \in [0,y) \\[3pt]
0 & x \not\in [0,y)
\end{cases}
\end{align*}$$
$\implies X|Y = y \sim U(0,y)$


### Bivariate Standard Normal

![[Pasted image 20250503141459.png]]

$\implies Z|W = w \sim N(\rho w, 1- \rho^2)$ for $\rho\in (-1,1)$


## Sum of RVs

Let $Z = X+Y$ where $X,Y$ have a joint pdf $f_{XY}$. *We want to find the distribution of $Z$*. 

$F_Z(z) = P(X+Y\leq z) = P((X,Y)\in A_z)$ where 

![[Pasted image 20250503154429.png|550]]
so 
$$\begin{align*}
F_Z(z) &= P((X,Y) \in A_z)\\[4pt]
 &= \iint_{A_z}f_{XY}(x,y)\:dx\:dy \\[4pt]
&= \int_{x=-\infty}^\infty \int_{y=-\infty}^{z-x} f_{XY}(x,y) \:dy\:dx \\[4pt]
&= \int_{x=-\infty}^\infty \int_{v=-\infty}^z f_{XY}(x,v-x) \:dv\:dx \tag{set $v = x+y$}\\[4pt]
&\overset{\text{Fubini}}{=} \int_{v=-\infty}^{z}\underbrace{\left[ \int_{x=-\infty}^{\infty}\:f_{XY} (x,v-x)\:dx\right]}_{g(v)} \:dv 
\end{align*}$$
$\implies Z$ is a continuous RV with density
$$f_Z(v) = g(v) = \int_{-\infty}^\infty f_{XY}(x,v-x)\:dx = \int_{-\infty}^\infty f_{XY}(v-y,y)\:dy$$

- If $X,Y$ are [[Independent RV]], then
$$f_Z(z) = \int_{-\infty}^\infty f_X(x)\:f_Y(z-x)\:dx$$
	- Note that the integrand is $f_X \star f_Y$ the convolution of $f_X,f_Y$ 



### Examples

#### Gamma dist.
$X \sim \Gamma(\alpha, \lambda)$ independent of $Y \sim \Gamma(\beta,\lambda)$. Then for $z > 0$,

$$\begin{align*}
f_{X+Y}(z) &= \int_{-\infty}^\infty f_X(x)f_Y(z-x)\:dx \\
&= \int_0^z \frac{\lambda^\alpha x^{\alpha-1}}{\Gamma(\alpha)} e^{-\lambda x}\cdot \frac{\lambda^\beta (z-x)^{\beta-1}}{\Gamma(\beta)} e^{-\lambda (z-x)}\:dx \\
&= \frac{\lambda^{\alpha+\beta}}{\Gamma(\alpha)\Gamma(\beta)} e^{-\lambda z} \cdot \int_0^z x^{\alpha-1}(z-x)^{\beta-1}\:dx
\end{align*}$$
with $x=zt$,
$$\int_0^z x^{\alpha-1}(z-x)^{\beta-1}\:dx = z^{\alpha+\beta-1}\underbrace{\int_{0}^1 t^{\alpha-1} (1-t)^{\beta-1}\:dt}_{B(\alpha,\beta); \text{ Beta function}}$$
$$\implies f_{X+Y}(z) = \frac{\lambda^{\alpha+\beta}}{\Gamma(\alpha)\Gamma(\beta) / B(\alpha,\beta)}\cdot z^{\alpha+\beta-1}\cdot e^{-\lambda z} \cdot \mathbb{1}_{z>0}$$
$$\implies X+Y \sim \Gamma(\alpha+\beta,\lambda)$$

>[!tip] Corollary 
>$$\Gamma(\alpha+\beta) = \frac{\Gamma(\alpha)\Gamma(\beta)}{B(\alpha,\beta)},\quad \text{or}\quad B(\alpha,\beta) = \frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha+\beta)}$$

>[!tip] Corollary
>Recall that $\text{Exp}(\lambda) \equiv \Gamma(1,\lambda)$.
>If $X_1,...,X_n$ are iid $\text{Exp}(\lambda)$ RVs then
>$$\sum_1^n X_i = ((((X_1+X_2)+X_3)+X_4)+...+X_{n-1})+X_n \sim \Gamma(n,\lambda)$$
##### Proof
We saw that $X_i \sim \Gamma(1,\lambda)$ so by induction $\sum_{1}^n X_i \sim \Gamma(n,\lambda)$ 

![[Pasted image 20250504100854.png|500]]
