> [!info] Definition
> The **expected value** or **expectation**, of the discrete random variable $X$ is defined as 
> $$E(X)=\sum\limits_kx_kp_X(x_k)$$ 
> where $\{x_k\} = X(\Omega)$, and $p_x$ is $X$'s pmf *as long as RHS is well-defined.*

# Examples

## Bernoulli
- $X \sim \text{Bernoulli}(p)$
$$E(X) = 0\cdot (1-p) + 1 \cdot p = p$$

## Poisson
- $X \sim \text{Poisson}(\lambda)$

![[Screenshot 2025-03-05 at 4.34.33 pm.png|500]]

## Binomial 
- $X \sim \text{Binomial}(n,p)$

![[Screenshot 2025-03-05 at 4.39.37 pm.png|600]]


## Geometric
- $X \sim \text{Geometric}(p)$ with $p \in (0,1)$
$$E(X) = \sum_{k=0}^\infty k\cdot (1-p)^{k-1}p$$
and $P(X=+\infty)=0$ with convention $\infty \cdot 0 = 0$.

Let $q = 1 - p$ so that $E(X) = p\sum kq^{k-1}$. Also let $f(q) = \sum^\infty_{k=0}q^k$. Since $q \in (-1,1)$, then 
$$f(q) = \frac{1}{1-q} \tag{converging power series}$$
Notice that 
$$\begin{align*}
f'(q) &= \sum_{k=0}^\infty kq^{k-1} \\[5pt]
&= \frac{d}{dq}\left(\frac{1}{1-q}\right) \\[5pt]
&= \frac{1}{(1-q^2)}
\end{align*}$$
>[!warning]
>This only true if $f_n \in C^\infty$, which the power series is 
>

Finally,
$$\begin{align*}
E(X) &= pf'(q) \\[2pt]
&= p\cdot\frac{1}{(1-q)^2} \\[2pt]
&= \frac{1}{p}
\end{align*}$$


# A Well-defined Series and Expectation

- The top definition of $E(X)$ depends on the order in which the series is summed up and the order is arbitrary

- For example, the alternating harmonic series $\sum {a_k}$ where $a_k = (-1)^{k+1}\frac{1}{k} = x_k \cdot p_X(x_k)$.
	- Converges depending on the value of $k$

>[!example] We say $E(X)$ is *well-defined* if the series $\sum_k x_kp_X(k)$ does not depend on the order of summation

Let $S^+$ and $S^-$ denote the sum of positive and minus the negative elements $a_n$ respectively where $\{a_n\}\subset \mathbb{R}$.
$$\begin{align*}
S^+ &:= \sum_n a_n1_{a_n>0}\\[4pt]
S^- &:= \sum_n (-a_n)1_{a_n<0}
\end{align*}$$

![[Pasted image 20250305232741.png]]
![[Pasted image 20250305233031.png|500]]
#### Proof
See Lecture 7 

# Fubini-Tonelli's Theorem

>[!tip] Theorem
>Let $\{a_{ij}\}$ be real numbers indexed by $i_j \in \mathbb{N}$. Then
>$$\sum_i\sum_j a_{ij} = \sum_j\sum_i a_{ij}$$
>if 
>1. $a_{ij}\geq 0\quad \forall i,j$  (or $a_{ij} \leq 0$)
>2. $\sum_i\sum_j |a_{ij}| < \infty$  (or $\sum_j\sum_i |a_{ij}| < \infty$ )


# Expectation of a Sum

>[!warning] Goal
>Find $E(X+Y) = ?$. When is it well-defined?

Let $g: \mathbb{R}^2 \to \mathbb{R}$ and let $Z = g(X,Y)$ where $X,Y$ are jointly distributed RVs with joint pmf $p_{XY}$ ($\{x_i\} = X(\Omega)$, $\{y_i\} = Y(\Omega)$)



>[!tip] Claim 1
>![[Pasted image 20250311214944.png]]



# Linearity of Expectation

$X,Y\in L^1$ jointly distributed RVs, and $\alpha,\beta \in \mathbb{R}$. Then 

1. $\alpha X + \beta Y \in L^1$
2. $E(\alpha X + \beta Y) = \alpha E(X) + \beta E(Y)$.

#### Proof
Let $g: \mathbb{R}^2 \to \mathbb{R}$ be $g(x,y)=\alpha x + \beta y$ and $Z = g(X,Y)= \alpha X + \beta Y$

Then 
![[Pasted image 20250311215337.png]]
where $X,Y \in L^1$. 
Hence, $Z = \alpha X + \beta Y \in L^1$, finishing the proof for 1.

Proof for 2. follows by removing $|\cdot|$ and following the same procedure. $\square$ 


## General case of Linearity

> [!tip] Claim 2
> If $X_1,...,X_n \in L^1(\Omega)$, then $\forall \alpha_i \in \mathbb{R}$, $\sum_{i=1}^n \alpha_i X_i \in L^1$, and 
> $$E\left(\sum_{i=1}^n \alpha_i X_i\right) = \sum_{i=1}^n \alpha_i E(X_i)$$


## Examples

### Sum of Bernoulli RVs
Let $X_i \sim \text{Bernoulli}(p_i)$ (not necessarily independent). Let $S_n = \sum_{i=1}^n X_i$. Then
$$\begin{align*}
E(S_n) &= E(\sum_{i=1}^n X_i) \\
&= \sum_{i=1}^n E(X_i)\\
&= \sum_{i=1}^n p \\
&= np \end{align*}$$
--> If $X \sim \text{Binomial}(n,p)$ then $X = \sum_{i=1}^n X_i$ where $X_i \sim \text{Bernoulli}(p)$


# Expectation of a Product of RVs

Does $E(XY) = E(X)E(Y)$? **Not generally**. 

**Counter example:** $X = Y \sim \text{Bernoulli}(p)$

>[!tip] Claim 3
>Suppose $X,Y \in L^1$ are *independent* then $XY \in L^1$ and 
>$$E(XY) = E(X)E(Y)$$
#### Proof
Let $g: \mathbb{R}^2 \to \mathbb{R}$ be $g(x,y) = x\cdot y$ and define $Z = g(X,Y) = XY$. Then

![[Pasted image 20250311223746.png]]

Therefore $Z=XY \in L^1$. Following Fubini (ii) proves the statement. $\square$ 


# Total Expectation Law

>[!info] Defintion
>$$E(Y) = \sum_x E(Y=X=x)P(X=x)$$


# Expectation of a Continuous RV

>[!info] Definition
>For a continuous RV $X$
>$$E(X) = \int_{-\infty}^\infty xf_X(x)\:dx$$
>provided 
> - $E^+(X) := \int_{0}^\infty xf_X(x)\:dx < \infty$ or
> - $E^-(X) := \int_{-\infty}^0 xf_X(x)\:dx < \infty$ 
>   and then $E(X) = E^+-E^-$ 

## Examples

### Gamma

$X \sim \Gamma(\alpha,\lambda)$, $\alpha,\lambda >0$
$$\begin{align*}
E(X) &= E^+(X) \\[4pt]
&= \int_0^\infty x \cdot \frac{\lambda^\alpha}{\Gamma(\alpha)} x^{\alpha - 1} e^{-\lambda x} \, dx \quad (E^- = 0) \\[4pt]
&= \frac{1}{\Gamma(\alpha)} \int_0^\infty (\lambda x)^\alpha e^{-\lambda x} \, dx \\[4pt]
&= \frac{1}{\Gamma(\alpha)} \int_0^\infty t^\alpha e^{-t} \cdot \frac{dt}{\lambda} \quad \text{(let } t = \lambda x \text{)} \\[4pt]
&= \frac{1}{\Gamma(\alpha)} \cdot \frac{1}{\lambda} \int_0^\infty t^\alpha e^{-t} \, dt \\[4pt]
&= \frac{\Gamma(\alpha + 1)}{\Gamma(\alpha)} \cdot \frac{1}{\lambda} \\[4pt]
&= \frac{\alpha \Gamma(\alpha)}{\Gamma(\alpha)} \cdot \frac{1}{\lambda} = \frac{\alpha}{\lambda} \\[4pt]
\\[4pt]
\implies\quad \text{If } X \sim \text{Exp}(\lambda) \text{ then } E(X) &= \frac{1}{\lambda}
\end{align*}$$

### Uniform 
$X \sim U(0,1)$
$$E(X) = E^+(X) = \int_0^1 x \cdot 1\:dx = \frac{1}{2}$$

### Beta
$X \sim \text{Beta}(a,b)\quad a,b>0$

![[Pasted image 20250508230641.png|600]]
![[Pasted image 20250508230944.png|600]]


### Cauchy 

$X \sim \text{Cauchy}$,  $f_X(x) = \frac{1}{\pi} \frac{1}{1 + x^2}$ 
$$E(X) = \int_{-\infty}^\infty \underbrace{x\:\frac{1}{\pi} \frac{1}{1+x^2}\:dx}_{\text{odd}}$$
The distribution is symmetric about 0. 

By [[Law of Large Numbers|SLLN]], if $X_i\sim\text{Cauchy}$ Then $S_n/n \to 0$ as $n \to \infty$ with probability 1. 
In particular $S_n/n$ should increasingly concentrate about 0. 
But it can be shown that $S_n/n$ is itself a Cauchy RV!

$P(S_n/n < -1) \equiv F_C(-1) > 0 \forall n$ and in particular $S_n/n$ does *not* converge (even weakly) to 0.

*What is wrong?*

$$\begin{align*}
E^+(X) &= \int_0^\infty x \frac{1}{\pi}\frac{1}{1+x^2}\:dx \\[4pt]
&\geq \int_1^\infty \frac{1}{\pi}\frac{x}{1+x^2}\:dx \\[4pt]
&\geq \int_1^\infty \frac{1}{\pi}\frac{x}{2x^2}\:dx \\[4pt]
&= \frac{1}{2\pi} \int_1^\infty \frac{1}{x}\:dx &= \infty
\end{align*}$$
and similarly $E^-(X) = \infty$.

$\therefore$ **Cauchy distribution does not have a well-defined expectation.**




