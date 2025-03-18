
- Let $X \in L^1$ and denote $\mu = E(X) \in \mathbb{R}$ 

> [!info] Definition
> The **variance** of $X$ is defined as 
> $$\begin{align*} \text{Var}(X) &= E[(X-\mu)^2] \\[7pt]
> &= \sum_k (x_k - \mu)^2 \cdot p_X(x_k)
\end{align*} $$

>[!tip] Claim 1
>For $X \in L^1$,
>$$\text{Var}(X) = E(X^2) - E^2(X)$$
#### Proof
Let $g(x) = (x-\mu)^2 \geq 0$. So
$$\text{Var}(X) = E[(X-\mu)^2] = E[g(X)] = \sum_k (x_k-\mu)^2\cdot p_X(x_k)$$
It follows that 
![[Pasted image 20250310213055.png|650]]
$\square$ 

- The $(+)$ is important when the summands are not convergent and the sum is to $\infty$. i.e.
![[Pasted image 20250310213649.png]]


# Examples of Variance
## Bernoulli
$X \sim \text{Bernoulli}(p)$, $E(X) = p$.

$$\begin{align*}
E(X^2) &= \sum_{k}x_k^2p(x_k) \\
&= 0^2 \cdot (1-p) + 1^2 \cdot p \\
&= p
\end{align*}$$

So $\text{Var}(X) = E(X^2) - E(X)^2 = p^2 - p = p(1-p)$

![[Pasted image 20250310221242.png|450]]


## Binomial
![[Pasted image 20250312225419.png]]

## Geometric

$X \sim \text{Geometric}(p)$ with $p \in (0,1)$. $E(X) = 1/p$.
$$\begin{align*}
E(X^2) &= \sum_{k=1}^\infty k^2 \cdot P(X=k) \\
&=  \sum_{k=1}^\infty k^2 \cdot (1-p)^{k-1}p \\
&=  \sum_{k=1}^\infty k^2 q^{k-1}p \tag{$q=p-1$}
\end{align*}$$
![[Pasted image 20250310221641.png|700]]
![[Pasted image 20250310221740.png]]
So 
$$E(X^2)=p\left(\frac{2q}{p^3}+\frac{1}{p^2}\right) = \frac{2-p}{p^2}$$
$$\text{Var}(X) = E(X^2)-E(X)^2 = \frac{2-p}{p^2}-\frac{1}{p^2} = \frac{1-p}{p^2}$$
$$\implies \text{Var}(X) = \frac{1-p}{p^2}$$

## Poisson
$X \sim \text{Poisson}(\lambda)$ for $\lambda >0$. $E(X) = \lambda$

![[Pasted image 20250310222112.png|600]]
So
$$\begin{align*}
\text{Var}(X) &= E(X^2) - E(X)^2\\
&= \lambda(\lambda+1)- \lambda^2 \\
&= \lambda
\end{align*}$$

## Negative Binomial
$r \in N_1$ (number of successs) and $p\in(0,1)$ (probability of success).

>[!tip] Claim
>If $X_i$ are iid $\text{Geometric}(p)$ random variables then $\sum_{i=1}^r X_i$ is a $\text{NegBinom}(r,p)$.
>
>Conversely, if $X$ counts the number of iid $\text{Bernoulli}(p)$ trials until the $r$th success, then $X = \sum_{i=1}^r X_i$ where $X_i$ are iid $\text{Geometric}(p)$. 

>[!tip] Corollary
>$X \sim \text{NegBin}(r,p)$, then
>$$\begin{align*}
>E(X) &= E\left(\sum_{i=1}^r X_i\right) = \sum_{i=1}^r E(X_i) = r\cdot\frac{1}{p} \\[10pt]
>V(X) &= V\left(\sum_{i=1}^r X_i\right) = \sum_{i=1}^r E(X_i) = r\cdot\frac{1-p}{p^2} \end{align*}$$

![[Screenshot 2025-03-19 at 9.55.28 am.png]]






# Variance of Linear Transformations

>[!tip] Claim 2
>Let $V(X) = \sigma^2 < \infty$ then $\forall \alpha,\beta \in \mathbb{R}$
>$$V(\alpha X + \beta) = \alpha^2 \sigma^2.$$
>i.e. Variance is shift-invariant, and scales quadratically.
#### Proof
Let $\mu = E(X) \in \mathbb{R}$. Recall the $E(X)$ is linear. Then 
$$E(\alpha X + \beta) = \alpha \mu + \beta$$
Therefore,
$$\begin{align*}
V(\alpha X + \beta)&= E[((\alpha X + \beta) - (\alpha \mu + \beta))^2] \\[4pt]
&= E[(\alpha (X -\mu))^2] \\[4pt]
&= \alpha^2E[(X-\mu)^2] \\[4pt]
	&= \alpha^2\sigma^2
\end{align*}$$
>[!tip] Claims 3,4,5
>1. If $X,Y \in L^1$ are *independent*, then $XY \in L^1$ and $E(XY) = E(X)E(Y)$
>
>1. If $X,Y \in L^2$, then $XY \in L^1$
>   
>5. If $X \in L^2$ and $\alpha,\beta \in \mathbb{R}$, then
>$$B(\alpha X + \beta) = \alpha^2 \sigma^2$$



# Variance of a Sum

>[!tip] Claim 6
>If $X,Y \in L^2$, then 
>$$V(X+Y) = V(X) + V(Y) + 2 \text{Cov}(X,Y)$$
>
>Generally for $X_1,...,X_n \in L^2$,
>$$V\left(\sum_{i=1}^n X_i\right) = \sum_{i=1}^{n}V(X_i) + \sum_{i\neq j}\text{Cov}(X_i,X_j).$$
#### Proof
![[Pasted image 20250312224525.png]]

>[!tip] Claim 7 
>If $X_i$ are *(pairwise) independent* $L^2-$RVs then
>$$V\left(\sum_{i=1}^n X_i\right) = \sum_{i=1}^{n}V(X_i)$$


