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
