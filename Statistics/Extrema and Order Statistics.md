# PDF and CDF

>[!warning] Motivation
>Let $X_1,...,X_n$ be i.i.d RVs with CDF $F$. 
>Let $U = X_{(n)} = \max\{X_1,...,X_n\}$, $V = X_{(1)} = \min\{X_1,...,X_n\}$.
>
>*What are the distributions of $U$ and $V$?*

$$\begin{align*}
F_U(u) &= P(U \leq u) \\[4pt]
&= P(X_1\leq u, ...,X_n \leq u)\\[4pt]
&= \prod_{i=1}^n P(X_i \leq u) \\[4pt]
&= [F_X(u)]^n
\end{align*}$$
If $F$ has a density $f$, then by chain rule so does $F_U$
$$f_U(u) = n[F_X(u)]^{n-1}\:f(u)$$

Similarly,
$$\begin{align*}
F_V(v) &= 1 - P(V>v) \\[4pt]
&= 1 - P(X_1 > v, ..., X_n >v) \\[4pt]
&= 1 - \prod_{i=1}^n P(X_i>v)\\[4pt]
&= 1-[1-F_X(v)]^n
\end{align*}$$
If $F$ has a density $f$, then by chain rule
$$f_V(v) = n[1-F_V(v)]^{n-1} f(v)$$


- Generally, let $X_{(1)} \leq X_{(2)} \leq ...\leq X_{(n)}$ be the sorted values of $X_1,...,X_n$. 
  Then $X_{(i)}$ are called the **order statistics**. 
- *What is the distribution of $X_{(k)}$?*

>[!tip] Claim
>If $F$ is a continuous function (i.e. $\forall x, \:P(X=x) = 0$), then 
>$$X_{(1)} \leq X_{(2)} \leq ...\leq X_{(n)}$$
>with probability 1. 

>[!tip] Corollary
> There is no ambiguity which of the $X_i$s is $X_{(k)}$

![[Pasted image 20250508220939.png]]
$$\implies F_{X_{(k)}} (x) = \sum_{j=k}^n \binom{j}{k} [F(x)]^j[1-F(x)]^{n-j}$$
![[Pasted image 20250508221144.png]]
$$\implies f_{X_{(k)}} (x) = k \binom{n}{k} [F(x)]^{k-1}[1-F(x)]^{n-k}f(x)$$

# Examples

## Uniform 

$X_i \sim U(0,1)$. $\implies F_X(x) = x, f_X(x) = 1$ for $x\in(0,1)$. 

$\implies f_{X_{(k)}}(X) = k\binom{n}{k}x^{k-1}(1-x)^{n-k}\cdot\mathbb{1}_{x\in (0,1)}$         $\implies X_{(k)}\sim \text{Beta}(k, n-k+1)$






