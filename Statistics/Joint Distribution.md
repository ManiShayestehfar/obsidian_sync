Suppose two measurements $X$ and $Y$ are take for each $\omega \in \Omega$

The **joint pmf** of $X$ and $Y$ is 
$$p_{XY}(x,y) = P(X=x,Y=y)\quad x,y\in \mathbb{R}$$
where $\{X=x, Y=y\} = \{\omega: X(\omega)= x, Y(\omega)=y\}$ .

If $X$ and $Y$ are discrete RV:

![[Pasted image 20250304231100.png|600]]
Similarly
![[Pasted image 20250304231214.png]]

- $p_X$ and $p_Y$ are called the **marginal [[Probability Mass Function|pmf]]**.
- The RV $X$ is [[Independence|independent]] from $Y$ if the [[Distributions|distribution]] of $X$ is the same, regardless of which value $Y$ attains

## Examples

### Simple Example
A fair coin is tossed 3 times

- $\Omega = \{HHT, HTH, ...\}$
- $|\Omega| = 2^3 = 8$ 

Let $X = 1_{\{\text{heads on first toss}\}} = \# \:\: \text{of heads in first toss}$,  $Y = \text{total}\:\#\:\text{of heads}$.

![[Pasted image 20250304231833.png]]

>[!info] Definition
>The **joint pmf factors** of the [[Random Variables| random variables]] $X_1,...,X_n$ is 
>$$p_{X_1,...,X_n}(x_1,...,x_n) = P(X_1=x_1,...,X_n=x_n)$$

>[!tip] Claim 1
>The discrete [[Random Variables| random variables]] $X_1,...,X_n$ are independent if the joint pmf factors:
>$$p_{X_1,...,X_n}(x_1,...,x_n) = p_{X_1}(x_1)...p_{X_n}(x_n)\quad \forall x_1,...,x_n \in \mathbb{R}$$ 



 
# Continuous Case

>[!warning] Context
>Think of jointly distribute RVs $(X,Y)$ as selecting a random point in a subset of $\mathbb{R}^2$. Their joint distribution consists of $P((X,Y) \in B)$ for any *reasonable* $B \subset \mathbb{R}^2$. 
>
>However in the continuous case the pmf provides partial/no information. Instead the joint distribution of two $\mathbb{R}$-valued RVs is determined by the joint distribution function:
>$$F_{XY}(x,y) = P(X\leq x, Y \leq y)$$

![[Pasted image 20250421101837.png]]

- $F_{XY}$ explicitly specifies the probability that $(X,Y) \in (x_1,x_2] \times (y_1,y_2]$ 

![[Pasted image 20250421122453.png]]

>[!info]  Result
>$$P((X,Y) \in (x_1,x_2] \times (y_1,y_2]) = F(x_2,y_2) - F(x_1,y_2) - F(x_2,y_1) + F(x_1,y_1)$$ 

## Jointly Continuous 

>[!info] Definition
>The $\mathbb{R}$-valued RVs $X,Y$ are **jointly continuous** if $\exists f:\mathbb{R}^2 \to \mathbb{R}^+$ such that $\forall (x,y) \in \mathbb{R}^2$:
>$$F_{XY}(x,y) = \int_{-\infty}^x \int_{-\infty}^y f(s,t) \: dt\:ds = \iint_{B_{xy}} f(s,t) \:ds\:dt$$
>In this case $f$ is the **joint density** of $X,Y$.

### Comments

1. By *Tonelli’s Theorem*, the iterated/repeated integral of a non-negative function is the same as the double integral:

$$
\int_{-\infty}^x \int_{-\infty}^y f(s,t) \, dt \, ds = \iint_{B_{xy}} f(s,t) \, ds \, dt = \int_{-\infty}^y \int_{-\infty}^x f(s,t) \, ds \, dt
$$

*Fubini’s extension*: For any integrable $f$, if when $f$ is replaced by $|f|$, one of the above three integrals is finite, then the equalities still hold. _Assuming all these improper Riemann integrals are well-defined._


2. If $f : \mathbb{R}^2 \to \mathbb{R}^+$ is integrable with $\iint_{\mathbb{R}^2} f = 1,$ then
$$
F(x, y) := \int_{-\infty}^x \int_{-\infty}^y f(s,t) \, dt \, ds
$$
	is the **joint CDF** of jointly continuous random variables with the joint pdf $f$.

#### Example for 2.
$$\begin{align*}
f(x,y) &= \lambda^2 e^{-\lambda(x+y)} \:\:\mathbb{1}_{x>0}\:\mathbb{1}_{y>0} \tag{$\lambda>0$} \\[5pt]
&= \lambda e^{-\lambda x} \:\mathbb{1}_{x>0} \:\:\cdot\:\: \lambda e^{-\lambda y} \:\mathbb{1}_{y>0}
\end{align*}$$ $\implies \int_{\infty}^{\infty}f(x,y) \:dx\:dy = \int_0^\infty \lambda e^{-\lambda x} \:dx\int_0^\infty \lambda e^{-\lambda y} \:dy = 1$

$\implies f$ is a joint pdf of RVs with joint CDF
$$\begin{align*}
F(X,Y) &= \int_{-\infty}^x \int_{-\infty}^y f(s,t) \, dt \, ds \\[4pt]
&= \int_0^x \lambda e^{-\lambda s} \:ds \: \int_0^y \lambda e^{-\lambda t} \:dt \\[4pt]
 &= (1- e^{-\lambda x})(1- e^{-\lambda y})
\end{align*}$$

3. From $P((X,Y) \in B_{xy}) = F_{XY}(x,y) = \iint_{B_{xy}}f\:ds\:dt$  $\forall (x,y) \in \mathbb{R}^2$ it follows that for any (Borel measurable) set $B \subset \mathbb{R}^2$,
	$$P((X,Y) \in B) = \iint_Bf\:\:ds\:dt$$
4. If $f$ is a continuous function (again except possibly at finite # of points) then everywhere that $f$ is continuous we have 
	$$f(x,y) = \frac{\partial^2}{\partial x\partial y} \left. F_{XY} \right |_{(x,y)} = \frac{\partial^2}{\partial y\partial x} \left. F_{XY} \right |_{(x,y)}$$
	 and in particular $f$ is determined where it is continuous.

5. $X$ and $Y$ can be continuous RVs but *not* jointly continuous.

6. If $X$ is a cont. RV with pdf $f_X$, then if $f_X$ is continuous at $x$ and $\delta >0$ is small:
	$$\begin{align*}
P(X \in \underbrace{(x - \delta/2, \: x + \delta/2)}_{\large I_x}) &= \int_{x-\delta/2}^{x + \delta/2} f_X(s) \:ds \\
&\approx f_X(x) |I_x| = f_X(x)\cdot \delta
\end{align*} $$
	similarly if $(X,Y)$ are jointly cont. wit pdf $f_{XY}$, then of $f_{XY}$ is cont. at $(x,y)$ and $\delta,\varepsilon>0$ are small, then with
	![[Pasted image 20250421133942.png|600]]



# Marginal Distributions

Recall: $p_X(x) = \sum_y P_{XY}(x,y)$ 

>[!tip] Claim 
>If $X,Y$ have a joint pdf $f_{XY}$, then $X$ is a cont. RV and 
>$$f_X(x) = \int_\mathbb{R}f_{XY}(x,y) \:dy$$ 
>called the **marginal density**.
##### Proof
![[Pasted image 20250421141526.png|650]]


## Examples
### Joint Distribution of an Independent Uniform and Exponential Variables

$f_{XY}(x,y) = \lambda^2 e^{-\lambda y}, \quad y>x \geq 0, \lambda >0$.                               ![[Pasted image 20250421141832.png|150]]
	 $$f_X(x) = \int_{-\infty}^{\infty} f_{XY}(x,y) \:dy$$

![[Pasted image 20250421142058.png|600]]
![[Pasted image 20250421142243.png|600]]



### Uniform Distribution on an Interval

Recall that $U(a,b)$ the uniform distribution on $I=(a,b)$, has a density $f = C \cdot \mathbb{1}_{I}$ where $C = 1 / |I| = 1 / (b-a)$. 
	- This models the random selection of a random point in $I$ such that for any sub interval $A \subset I$ 
	$$P(X \in A) = \int_A f\:dx = \int_A C \:dx = C\int_A dx = \frac{|A|}{|I|}$$
	- We can extend this to a uniform distribution over *any "nice"* region $R \subset \mathbb{R}^2$ that is *"measurable"*. 

>[!info] Definition 
>A random point has a uniform distribution over $R \subset \mathbb{R}^2$ if it has a (joint) density
>$$f(x,y) = C \cdot \mathbb{1}_{R} = \begin{cases} 
>C & (x,y) \in R \\
>0 & \text{otherwise}
\end{cases}$$

- Note that $1 = \iint_{\mathbb{R}^2} \:f(x,y)\: dx\:dy = \iint_R\:C\:dx\:dy = C \cdot |R|$ 
	- hence $C = 1/|R|$ 

- Again, $\forall A \subset R$, 
	$$\begin{align*}
P((X,Y)\in A) &= \iint_A \:f\: dx\:dy \\
&= \iint_A C\:dx\:dy \\
&= C \iint_A\:dx\:dy \\
&= \frac{|A|}{|R|}
\end{align*}$$
>[!quote] Conclusion
>The probability that the randomly chosen point lies in $A \subset R$ is proportional to its area


### Uniform distribution on a unit disc
$$R = \{(x,y) \in \mathbb{R}^2 : x^2 +y^2 \leq 1\}$$ $|R| = \pi$, so uniform dist. on $R$ is given by $f_{XY}(x,y) = \frac{1}{\pi}\cdot 1_{x^2 + y^2 \leq 1}$ 

**What are the marginal distributions?**

![[Pasted image 20250501223204.png]]

$$f_X(x) = \int_{-\infty}^{\infty} f_{XY}(x,y)\:dy = 0 \quad\quad \text{if}\:\:x \not\in[-1,1]$$
if $x \in [-1,1]$
$$f_X(x) = \int_{-\sqrt{1-x^2}}^{\sqrt{1-x^2}}\:\frac{1}{\pi}\:dy = \frac{2}{\pi}\sqrt{1-x^2}$$
- The circle is axially symmetric so $f_Y$ is calculated similarly

- **NOTE:** Even though $(X,Y)$ are uniformly distributed over $R$, $X$ itself is NOT uniformly distributed on $[-1,1]$ as shown above 


### (Standard) Bivariate Normal

The random point $(Z,W)$ has a (standard) bivariate normal distribution if it has a density
$$f_{ZW}(z,w) = \frac{1}{2\pi\sqrt{1-\rho^2}} e^{-\frac{1}{2(1-\rho^2)}(z^2 - 2\rho zw + w^2)}$$
where $\rho \in (-1,1)$ is a parameter. 

**What is the marginal density?**

Firstly, $z^2 - 2\rho zw + w^2 = (w-\rho z)^2 + (1-\rho^2)z^2$. So 

$$\begin{align*}
f_Z(z) &= \int_{-\infty}^\infty \frac{1}{\sqrt{2\pi}} e^{{-z^2}/2} \cdot \frac{1}{\sqrt{2\pi (1-\rho^2)}} e^{-\frac{(w-\rho z)^2}{2(1-\rho^2)}}\: dw \\[7pt]
&= \int_{-\infty}^\infty \frac{1}{\sqrt{2\pi}} e^{{-z^2}/2} \cdot \frac{1}{\sqrt{2\pi \sigma^2}} e^{-\frac{(w-\mu)^2}{2\sigma^2}}\: dw
\end{align*}$$
where we have set $\mu := \rho z$ and $\sigma^2 = (1-\rho^2)>0$ .

So $N(\mu=\rho z, \sigma^2 = 1-\rho^2)$ has a density $f_Z(z) = \frac{1}{\sqrt{2\pi}}e^{-z^2/2}$ 
$\implies Z \sim N(0,1)$ and by symmetry $W \sim N(0,1)$ 