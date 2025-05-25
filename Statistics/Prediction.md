Suppose $X,Y$ are jointly distributed RVs (two measurements from the same experiment) and suppose we know $X=x$.
$$\textit{How can we use this to predict the value of Y?}$$

- Formally, given $X$, our predictor of $Y$ is $g(X)$, where $g:\mathbb{R}\to \mathbb{R}$ (measurable).  How to measure the quality of prediction? MSE is reasonable: $E[Y-g(x)]^2$ 

>[!success] The Prediction Problem
>Find $g$ that minimises the error
>$$\text{argmin}_{g:\mathbb{R}\to \mathbb{R}}\:\: E[Y-g(X)]^2$$
>assuming $Y \in L^2$, and that we know the joint dist. of $X,Y$.  $g$ only needs to be defined on $X(\Omega)$.

## Constant $g$
Suppose $g(X) = \alpha$. Then we need to find $\text{argmin}_{g:\mathbb{R}\to \mathbb{R}}\:\: E[Y-\alpha]^2$.
$$\begin{align*}
E[(Y-\alpha)^2] &= E[Y^2] - 2 \alpha E[Y] + \alpha^2 \\[4pt]
&= E[Y^2] - \mu^2 + mu^2 - 2\alpha \mu + \alpha^2 \\[4pt]
&= V(Y) + (\mu-\alpha)^2 \\[4pt]
&\geq V(Y)
\end{align*} $$
$\implies$ the best MSE predictor of $Y$, given no other information is $E(Y)$. i.e. if $\alpha  = E(Y)$.


## General Case

![[Prediction-1747951067030.png]]
![[Prediction-1747951075951.png]]

>[!tip] Claim 
>If $\varphi: \mathbb{R}\to \mathbb{R} \:\text{s.t.}\: y\cdot\varphi(X) \in L^1$ and $Y \in L^1$ then 
>$$E[Y\cdot \varphi(X)|X] = \varphi(X)E[Y|X]$$
##### Proof

![[Prediction-1747951839049.png|600]]

>[!tip] Claim
>If $\varphi(X) \in L^1$,
>$$E[\varphi(X)|X] = E[1\cdot \varphi(X) | X] = \varphi(X)E[1|X] = \varphi(X)$$


## Conditional Case

WLOG let $g(X) = Y - (Y- g(X)) \in L^2$. 

![[Prediction-1747952253766.png|650]]

>[!tip] Claim
>If $W = E[(Y-g(X))^2\:|\:X],U = V(Y|X)\in L^1$ and $W \geq U$, then $E[W]\geq E[U]$ with equality iff $W=U$.
>
>This implies that
>$$\begin{align*}
E[(Y-g(X))^2] &= E[E[(Y-g(X))^2 | X]] = E[W_g] \\[5pt]
&\geq E(U) = E[V(Y|X)]
\end{align*}$$
with equality iff $W_g = U \iff g(X) = E[Y|X]$  
##### Proof

Let $X = W - U$, so $X \geq 0 \:\:\overset{\text{intuitively}}{\implies}\:\: E(X) \geq 0$.  Separately, the following facts are true:
1. For $X \geq 0$, $E(X) = \int_{0}^{\infty}(1-F(x))\:dx$ 
2. $E(W-U) = E(W) - E(U)$

$\implies E(X) = E(W-U) = E(W) - E(U) \geq 0$   $\implies E(W) \geq E(U)$. 

**For Equality:**

$(\Rightarrow)$ 
If $W=U$ almost surely, then $X=W-U = 0$ almost surely. So $X$ is a discrete RV and its expectation is given be $E(X) = \sum_{i=1}^{\infty}x_{i}\:p_X(x_{i})= 0$.  So $E(W) - E(U) = 0$ and $E(U) = E(W)$.  

$(\Leftarrow)$
![[Screenshot 2025-05-23 at 10.06.07 PM.png|650]]


>[!tip] Corollary
>The optimal MSE predictor of $Y$ given $X$ is $E[Y|X]$ and the MSE in this case is $E[V(Y|X)]$
>
>NOTE: If $Y$ is ind. of $X$ then $E[Y|X] = E[Y]$ and $MSE= V(Y)$


### Examples

#### Standard Bivariate

$Z,W$ are standard bivariate normal with parameter/correlation coefficient $\rho \in (-1,1)$.
Recall that $Z|W=w \sim N(\rho w, 1- \rho^2)$.

$\implies E(Z|W=w) =  \rho w$  and $E[Z|W] = \rho W$ 
$\implies \rho W$ minimises $E[(Z-g(W))^2]$ among *all* functions $g$.

Notably, the best MSE predictor of $Z$ given $W$ is *linear* in $W$.
$$\begin{align*}
MSE &= E[(Z-\rho W)^2] \\[4pt]
&= E[Z^2] - 2\rho E[ZW] + \rho^2 E[W^2]] \\[4pt]
&= 1 - 2\rho \cdot \rho + \rho^2 \\[4pt]
&= 1 - \rho^2
\end{align*}$$
Compare this with $V(Z|W) \equiv 1-\rho^2$  $\implies E[V(Z|W)] = 1- \rho^2$ 

- If $\rho = 0$, then $E(Z|W) = 0 = E(Z)$ and $MSE(Z|W) = 1$.
	- As $|\rho|\uparrow$, $MSE \downarrow$
