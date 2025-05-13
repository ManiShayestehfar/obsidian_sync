Suppose $F$ is a continuous [[Cumulative Distribution Function|CDF]] which is strictly monotone. In this case, $F^{-1}:(0,1) \to \mathbb{R}$ is well-defined:

![[Pasted image 20250419225858.png]]

>[!info] Definition
>The **p-th quantile** of $F$ is $x_p = F^{-1}(p)$, or equivalently, $F(x_p) = p$. 
>
>$x_p$ is also known as the $(100p)^\text{th}$ percentile.

![[Pasted image 20250419230035.png]]

>[!info] Definition
>For $p \in(0,1)$, $x_p \in \mathbb{R}$ is *a* **p-th quantile** of $F$ if
>1. $F(x_p) \geq p$
>2. $F(x_p^-) := \lim_{x\to x_p^-} F(x) \leq p$ 

>[!tip] Corollary 1
>If $F(x_p) = p$ then $x_p$ is a p-th quantile of $F$, and in particular our new definition generalises the original one. 

![[Pasted image 20250419230400.png]]

>[!tip] Claim 1
>For $p \in (0,1)$, $x_p \in \mathbb{R}$ the following are equivalent for an RV $X$ with CDF $F$:
>1. $x_p$ is a p-th quantile of $F$:
>	i. $F(x_p) \geq p$ 
>	ii. $\lim_{x \to x_p^-} F(x) \leq p$
>2. $P(X \leq x_p) \geq p$ and $P(X < x_p) \leq p$ 
>3. Either
>   i. $F(x_p) = p$, or 
>   ii. $F(x_p) > p$ and $\forall x < x_p$, $F(x) \leq p$.

>[!info] Quantile Function
>The **qunatile function** is defined as
>$$Q_F(p) = \inf \{x:F(x) \geq p\}\quad p \in (0,1)$$
>
>-> Using right-continuity of $F$ we can show that $Q_F(p) = \min \{x : F(x) \geq p\}$


>[!tip] Claim 2
>$\forall p \in (0,1), x \in \mathbb{R}$
>$$x \geq Q_F(p) \iff F(x) \geq p$$

![[Pasted image 20250419232236.png]]


>[!tip] Claim 3
>$Q_F(p)$ is the *smallest* pth-quantile of $F$
##### Proof
Directly from the definition of the quantile:
$F(Q_F(p)) \geq p$ and if $x < Q_F(p)$ then $F(x) < p$ so $Q_F(p)$ is a pth-quantile and it is the smallest. 

>[!tip] Claim 
>If $x'_p < x''_p$ are pth-quantiles of $F$ then $\forall x \in [x'_p, x''_p)$, $F(x)=p$.
>In particular, $x$ is the pth-quantile. 
>
##### Proof
$F$ is an increasing function so $\forall x \geq x_p'$, $F(x) \geq F(x'_p) \geq p$. By Claim 1 (III), Either:
1. $F(x''_p) = p$ so  $\forall x \leq x''_p$ $F(x) \leq F(x''_p) = p$ 
	$$\implies \forall x \in [x'_p, x''_p] \quad \quad F(x) = p$$
2. Or, $F(x''_p) > p$ and $\forall x < x''_p, \:\: F(x) \leq p$ 
	$$\implies \forall x \in [x'_p, x''_p) \quad \quad F(x) = p$$
$\square$ 


>[!tip] Corollary 2
>If $F$ is continuous and strictly $\uparrow$, then $F^{-1} \equiv Q_F$ 
>i.e *the quantile function generalises the notion of $F^{-1}$* 
>
>-> Because $F$ is strictly $\uparrow$, there can only be one pth-quantile for each $p$ and both $F^{-1}(p)$ and $Q_F(p)$ are such quantiles



 

