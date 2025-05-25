Let $X$ be an RV, then $Y = e^{tX}\geq 0$ so $E(Y)$ is well-defined, albeit it can be $+\infty$.

>[!info] Definition
>The **MGF** of the RV $X$ is defined as 
>$$M(t) = E(e^{tX})$$
>for all $t$ for which the RHS $< \infty$.  
>
>- Note that $M(0) = E(e^{0\cdot X}) = 1$, so the MGF is always finite for $t=0$. 

- If $X$ is *discrete*, with pmf $\sum_{i=1}^{\infty}p_X(x_{i)}= 1$ then
$$M(t) = \sum_{i=1}^{\infty}e^{tx_i}\:p_X(x_{i)}\tag{if finite}$$
- If $X$ is *continuous*, with density $f_x$ then 
	$$M(t) = \int_{\mathbb{R}} e^{tX} \: f_{X(x)\:dx}\tag{if finite}$$

# Examples

## Poisson

$X \sim \text{Poisson}(\lambda)$ where $\lambda > 0 $.
$$\begin{align*}
M(t) &= \sum_{k=0}^{\infty}e^{tk}\:(e^{-\lambda} \frac{\lambda^k}{k!})\\[4pt]
&=  e^{-\lambda} \sum_{k=0}^{\infty} \frac{(\lambda e^t)^k}{k!}\\[4pt]
&= e^{-\lambda}e^{\lambda e^{t}}\\[4pt]\\
&= e^{\lambda(e^t-1)}
\end{align*}$$

## Standard Normal

$X \sim N(0,1)$ 
$$\begin{align*}
M(t)
\end{align*}$$
