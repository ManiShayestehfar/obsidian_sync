> [!info] Definition
> The **expected value** or **expectation**, of the discrete random variable $X$ is defined as 
> $$E(X)=\sum\limits_kx_kp_X(x_k)$$ 
> where $\{x_k\} = X(\Omega)$, and $p_x$ is $X$'s pmf *as long as RHS is well-defined.*

# Examples

## Bernoulli
- $X \sim \text{Bernoulli}(p)$
$$E(X) = 0\cdot (1-p) + 1 * p = p$$

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

- The top definition of $E(X)$ depends on the order in which te series is summed up and the order is arbitrary

- For example, the alternating harmonic series $\sum {a_k}$ where $a_k = (-1)^{k+1}\frac{1}{k} = x_k \cdot p_X(x_k)$.
	- Converges depending on the value of $k$

>[!example] We say $E(X)$ is *well-defined* if the series $\sum_k x_kp_X(k)$ does not depend on the order of summation

Let $S^+$ and $S^-$ denote the sum of positive and minus the negative elements $a_n$ respectively where $\{a_n\}\subset \mathbb{R}$.
$$\begin{align*}
S^+ &:= \sum_n a_n1_{a_n>0}\\[4pt]
S^- &:= \sum_n (-a_n)1_{a_n<0}
\end{align*}$$
>[!info] Definition 
>Denote $L^1 = L^1(\Omega, \mathcal{F}, P) = L^1(\Omega)$ the space of all discrete random variables $X: \Omega \to \mathbb{R}$ such that with $\{x_n\} = X(\Omega)$,
>$$\sum_n |x_n|\cdot p_X(x_n) < \infty $$ 
>

![[Pasted image 20250305232741.png]]
![[Pasted image 20250305233031.png|500]]
#### Proof
See Lecture 8 

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
>![[Pasted image 20250310222816.png]]



# Linearity of Expectation

$X,Y\in L^1$ jointly distributed RVs, and $\alpha,\beta \in \mathbb{R}$. Then 

1. $\alpha X + \beta Y \in L^1$
2. $E(\alpha X + \beta Y) = \alpha E(X) + \beta E(Y)$.