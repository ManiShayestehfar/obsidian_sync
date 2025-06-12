Let $X$ be an RV, then $Y = e^{tX}\geq 0$ so $E(Y)$ is well-defined, albeit it can be $+\infty$.

# Definition

>[!info] Definition
>The **MGF** of the RV $X$ is defined as 
>$$M(t) = E(e^{tX})$$
>for all $t$ for which the RHS $< \infty$.  
>
>- Note that $M(0) = E(e^{0\cdot X}) = 1$, so the MGF is always finite for $t=0$. 

- If $X$ is *discrete*, with pmf $\sum_{i=1}^{\infty}p_X(x_{i)}= 1$ then
$$M(t) = \sum_{i=1}^{\infty}e^{tx_i}\:p_X(x_{i})\tag{if finite}$$
- If $X$ is *continuous*, with density $f_x$ then 
	$$M(t) = \int_{\mathbb{R}} e^{tx} \: f_{X(x)\:dx}\tag{if finite}$$

## Examples

### Poisson

$X \sim \text{Poisson}(\lambda)$ where $\lambda > 0$.
$$\begin{align*}
M(t) &= \sum_{k=0}^{\infty}e^{tk}\:(e^{-\lambda} \frac{\lambda^k}{k!})\\[4pt]
&=  e^{-\lambda} \sum_{k=0}^{\infty} \frac{(\lambda e^t)^k}{k!}\\[4pt]
&= e^{-\lambda}e^{\lambda e^{t}}\\[4pt]\\
&= e^{\lambda(e^t-1)}
\end{align*}$$

### Standard Normal

$X \sim N(0,1)$ 
$$\begin{align*}
M(t) &= \int_{-\infty}^\infty e^{tx} \frac{1}{\sqrt{2\pi}}e^{-x^2/2}\:dx \\[4pt]
&= \frac{1}{\sqrt{2\pi}}\int_{-\infty}^\infty e^{-\tfrac{1}{2}(x^2 - 2tx + t^2) + \tfrac{t^2}{2}}\:dx \\[4pt]
&= e^{t^2/2}\int_{-\infty}^\infty\frac{1}{\sqrt{2\pi}}e^{-(x-t)^2/2}\:dx \\[4pt]
&= e^{t^2/2} \quad\quad \forall t\in\mathbb{R}
\end{align*}$$

### Gamma
$X \sim \Gamma(\alpha,\lambda)$ 

![[Moment Generating Function-1748135190587.png|650]]


# MGF Derivative to Expectation
 
>[!example] Theorem
>If $\exists\: \delta >0$ such that $M(t)<\infty$ $\forall t \in (-\delta,\delta)$, then $\forall n \in \mathbb{N}$, $M^{(n)}(0) = E(X^n)$. 
##### Sketch of Proof
$$\begin{align*}
M'(t) &= \frac{d}{dt}\sum_i e^{tx_i}p_X(x_i)\\
&= \sum_i \frac{d}{dt} e^{tx_i} p_X(x_i) \\
&= \sum_i x_ie^{tx_i}p_X(x_i)\\
\implies M'(0) &= \sum_i x_i p_X(x_i) = E(X)
\end{align*}$$
Generally,
$$\begin{align*}
M^{(k)}(t) &= \frac{d^k}{dt^k}\int_{-\infty}^\infty e^{tx} f_X(x) \: dx\\
&= \int_{-\infty}^\infty \frac{d^k}{dt^k} e^{tx} f_X(x) \: dx \\
&= \int_{-\infty}^\infty x^k\:e^{tx }f_X(x) \: dx \\
\implies M^{(k)}(0) &= \int_{-\infty}^\infty x^k\:f_X(x) \: dx = E(X^k)
\end{align*}$$

## Examples

### Poisson
$X \sim \text{Poisson}(\lambda)$,   $M(t) = e^{\lambda(e^t-1)}$
$$\begin{align*}
M'(t) &= M(t)\lambda e^t \\[4pt]
\implies M'(0) &= M(0)\lambda = \lambda = E(X)\\[8pt]
M''(t) &= M(t)
(\lambda e^t)^2 + M(t) \lambda e^t \\[4pt]
\implies M''(0) &= \lambda^2 + \lambda = E(X^2)\end{align*}$$
### Standard Normal

$X \sim N(0,1)$,   $M(t) = e^{t^2/2}$ 
$$\begin{align*}
M'(t) &= M(t)\cdot t \\[4pt]
\implies M'(0) &= M(0)\cdot 0 = 0 = E(X)\\[8pt]
M''(t) &= M(t)
\cdot t^2 + M(t) \\[4pt]
\implies M''(0) &= 1 = E(X^2)\end{align*}$$

### Gamma

![[Moment Generating Function-1748137018954.png|650]]





# Equivalence of CDFs

>[!example] Theorem
>Let $F,G$ be CDFs and suppose $\exists \delta >0$ such that $\forall t \in (-\delta,\delta)$,  $M_F(t) = M_G(t) < \infty$.
> Then $F \equiv G$. 
> 
> - Note: the converse is false

>[!tip] Corollary
>$$M(t) = E(e^{tX}) = 0 \iff P(X=-\infty) = P(e^{tX} = 0) = 1$$
>In particular, if $X$ is real-valued, then $M(t)>0 \quad \forall t$.

>[!tip] Claim
>If $X,Y$ are ind. $\mathbb{R}-valued$ RVs with MGFs $M_X$, $M_Y$, then
>$$M_{X+Y} \equiv M_X\cdot M_Y$$
>That is, $M_{X+Y}(t) < \infty \iff M_X(t)$ and $M_Y(t) < \infty$ and in this case $M_{X+Y}(t)=M_X(t)M_Y(t)$
##### Proof
If $Z,W \in L^1$ are ind. then $E(ZW) = E(Z)E(W)$. The same proof as in Lecture 8 can extend that identity for real, non-negative valued RVs $Z,W$ with $E(Z)E(W) >0$ where the equality also holds between $\infty$'s. Therefore
$$\begin{align*}
M_{X+Y} &= E\left[e^{t(X+Y)}\right] \\[4pt]
&= E\left[e^{tX}e^{tY}\right] \\[4pt]
&= E[e^{tX}]E\left[e^{tY}\right] \\[4pt]
&= M_X(t)M_Y(t)
\end{align*}$$
By induction, if $X_1,...,X_n$ are ind. RVs then $M_{\sum X_i} = \prod_{i=1}^n M_{X_i}(t)$


## Example

### Gamma
$X\sim \Gamma(\alpha, \lambda)$ is ind. of $Y \sim \Gamma(\beta, \lambda)$ where $\alpha,\beta, \lambda > 0$. For $t < \lambda$,
$$M_{X+Y} = M_X(t)M_Y(t) = \left(\frac{\lambda}{\lambda -t}\right)^\alpha\left(\frac{\lambda}{\lambda -t}\right)^\beta = \left(\frac{\lambda}{\lambda -t}\right)^{\alpha+\beta}$$
and for $t \geq \lambda, \quad M_{X+Y}(t) = \infty \cdot \infty = \infty$. 
$\implies X+Y \sim \Gamma(\alpha+\beta,\lambda)$

![[Moment Generating Function-1748259133082.png|650]]

#### Sub-Example - Standard Normal 
 $Z \sim N(0,1)$ and $Y = \sigma Z + \mu \sim N(\mu, \sigma^2)$ 
$$\begin{align*}
M_Y(t) &= e^{t\mu} M_z(t\sigma) \\[4pt]
&= e^{t\mu} e^{t^2\sigma^2/2} \\[4pt]
&= e^{t\mu \:+\: t^2 \sigma^2 /2} \quad \forall t \in \mathbb{R}
\end{align*}$$

#### Sub-Example - Normal 

![[Moment Generating Function-1748259352855.png|650]]


# Characteristic Function 

There are distribution for which the MGF exists only for $t=0$. i.e. Cauchy distribution
$$\int_{-\infty}^\infty e^{tx} \frac{1}{\pi} \frac{1}{1+x^2}\:dx = +\infty \quad\forall t\neq 0.$$
Hence we prefer to work with the **characteristic function (CF)** 
$$\phi_X(t) := E[e^{itX}] = M_X(it)$$
where $E[e^{itX}] = E[\cos(tX) + i\sin(tX)]$.

- Since $\cos$ and $\sin$ are bounded, the expectations are well-defined $\forall t \in \mathbb{R} \implies$ the characteristic function is defined $\forall t \in \mathbb{R}$.
- If $X,Y$ are ind. RVs then 
$$\begin{align*}
\phi_{X+Y}(t) &= E[e^{it(X+Y)}] \\[4pt]
&= E[e^{itX}]\:E[e^{itY}] \\[4pt]
&= \phi_X(t)\:\phi_Y(t)
\end{align*}$$

- If $E(|X|^k) < \infty$, then $\phi^{(k)}(t) = i^kE[X^k]$ 
- If $Y = aX + b\quad \forall a,b \in \mathbb{R}$, then 
	$$\phi_Y(t) = e^{itb}\phi_X(at)$$
- Similar to the MGF, $X\sim N(\mu,\sigma^2)$ then $Y = aX + b \sim N(a\mu+b, a^2\sigma^2)$

## Example
### Standard Normal
$Z \sim N(0,1)$, then 
$$\phi_Z(t) = M_Z(it) = e^{(it)^2/2} = e^{-t^2/2}$$
### Normal
$X \sim N(\mu,\sigma^2)$ then $X = \sigma Z + \mu$ so 
$$\phi_X(t)= e^{it\mu - \sigma^2 \frac{t^2}{2}}$$
