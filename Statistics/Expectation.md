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

>[!info] !
>$$E(Y) = \sum_x E(Y=X=x)P(X=x)$$

