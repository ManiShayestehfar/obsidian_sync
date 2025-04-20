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

>[!tip] Corollary
>If $F(x_p) = p$ then $x_p$ is a p-th quantile of $F$, and in particular our new definition generalises the original one. 

![[Pasted image 20250419230400.png]]

>[!tip] Claim 
>For $p \in (0,1)$, $x_p \in \mathbb{R}$ the following are equivalent for an RV $X$ with CDF $F$:
>1. $x_p$ is a p-th quantile of $F$:
>	i. $F(x_p) \geq p$ 
>	ii. $\lim_{x \to x_p^-} F(x) \leq p$
>2. $P(X \leq x_p) \geq p$ and $P(X < x_p) \leq p$ 
>3. Either $F(x_p) = p$, or $F(x_p) > p$ and $\forall x < x_p$, $F(x) \leq p$.

>[!info] Quantile Function
>The **qunatile function** is defined as
>$$Q_F(p) = \inf \{x:F(x) \geq p\}\quad p \in (0,1)$$
>
>-> Using right-continuity of $F$ we cans how that $Q_F(p) = \min \{x : F(x) \geq p\}$


>[!tip] Claim 
>$\forall p \in (0,1), x \in \mathbb{R}$
>$$x \geq Q_F(p) \iff F(x) \geq p$$

![[Pasted image 20250419232236.png]]


>[!tip] Claim 

