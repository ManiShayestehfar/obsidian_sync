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
