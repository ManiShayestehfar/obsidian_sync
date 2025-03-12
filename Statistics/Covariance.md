> [!info] Definition
> For jointly distributed RVs $X,Y \in L^1$ with $\mu_X = E(X), \mu_Y = E(Y)$, we define the **covariance** of $X$ and $Y$ as 
> $$\text{Cov}(X,Y) = E[(X-\mu_x)(Y-\mu_y)]$$
> if $(X-\mu_x)(Y-\mu_y)\in L^1$.
> 
> Note: $\text{Cov}(X,Y) = \text{Cov}(Y,X)$

 > [!tip] Claim 1
 > For $X,Y,XY \in L^1$, $\text{Cov}(X,Y)$ is well-defined and
 > $$\text{Cov}(X,Y) = E(XY) - E(X)E(Y)$$
 > 
 > --> If $X,Y \in L^2$, then the conclusion of the claim holds.
#### Proof
![[Pasted image 20250312222855.png]]

>[!tip] Corollary 1
>If $X,Y \in L^1$ are independent, then $\text{Cov}(X,Y) = 0$.
>i.e. *independent* RVs are *uncorrelated.* 

- *How about the converse?* i.e are uncorrelated RVs independent?

![[Pasted image 20250312224212.png]]
$$\text{Cov}(X,Y) = 0$$
- If $X$ and $Y$ are uncorrelated it follows that you cannot predict $Y$ using a *linear* function of $X$. i.e the regression line has a slope $=0$. 

 
