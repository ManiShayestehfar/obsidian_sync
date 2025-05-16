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

 
# Continuous RV

>[!tip] Claim
>If $X,Y,Z \in L^2$, $\alpha,\beta\in \mathbb{R}$ then
>$$\text{Cov}(\alpha X+\beta Y,Z) = \alpha \text{Cov}(X,Z) + \beta \text{Cov}(Y,Z)$$
>$\text{Cov}(\beta,Z) = 0$ so $\text{Cov}(\alpha X + \beta, Z) = \alpha \text{Cov}(X,Z)$.

If $X_1,...,X_n \in L^2$ then $\sum_1^n X_i \in L^2$ and 
$$V\left(\sum_1^N X_i\right) = \sum_1^n V(X_i) + \sum_{i\neq j} \text{Cov}(X_i,X_j)$$
If $X_i\in L^2$ are ind. then the covariance part = 0.

## Correlation Coefficient

>[!info] Definition
>The standard deviation is defined as $\sigma_X = \sqrt{V(X)}$. The **Correlation coefficient** is defined as 
$$\rho_{XY} = \frac{\text{Cov}(X,Y)}{\sigma_X\sigma_Y}$$
provided that $\sigma_X\sigma_Y > 0$. 

>[!tip] Claim
>Suppose $X,Y \in L^2$ with $\sigma_X\sigma_Y>0$. Then $\rho_{XY} \in [-1,1]$ and $|\rho_{XY}| = 1 \iff \:\exists\:a,b \in \mathbb{R} \:\text{s.t.}\:P(Y = a+bX)=1$ 
>
#### Proof

Replace $X,Y$ with $X' = X/\sigma_X$ and $Y' = Y/\sigma_Y$. We then have
$$\rho_{X'Y'} = \frac{\text{Cov}(X'Y')}{\sigma_{X'}\sigma_{Y'}} = \text{Cov}(X/\sigma_X, Y/ \sigma_Y)= \frac{\text{Cov}(X,Y)}{\sigma_X\sigma_Y} = \rho_{XY}$$
and $Y = a+bX \iff Y' = \underbrace{\frac{a}{\sigma_Y}}_{a'} + \underbrace{\frac{b\sigma_X}{\sigma_Y}}_{b'}X'$ .

![[Covariance-1747392645137.png]]
