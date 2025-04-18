>[!info] Definition
>The **Exponential Distribution** is a 1-parameter family of distributions defined by the pdf
>$$f_\lambda(x) = \lambda e^{-\lambda x} \cdot \mathbb{1}_{x \geq 0},$$
>where $\lambda > 0$ is the *rate* parameter. Alternatively,
>$$f_\beta(x) = \frac{1}{\beta} e^{-x/\beta} \cdot \mathbb{1}_{x \geq 0}$$
>where $\beta >0$ is the *scale* parameter.


# Examples 

## Exponential Densities with lambda 1/2, 1, 2

*which is which?*
![[Pasted image 20250418230842.png|400]]


**CDF:**
- For $x \geq 0$
$$F(x) = \int_{-\infty}^x f(t)\: dt = \int_0^x \lambda e^{-\lambda t}\: dt = \left. -e^{-\lambda t}\right\vert^x_0 = 1 - e^{-\lambda x}.$$
$\implies F(x) = (1-e^{-\lambda x})\cdot \mathbb{1}_{x\geq 0}$  and in particular 
$$\lim_{x\to \infty} F(x) = \lim_{x\to \infty}(1-e^{-\lambda x}) = 1$$
$\therefore$ $f$ is indeed a density.

## Emission Source

Suppose $T \sim \text{Exp}(\lambda)$, then for $t > 0$, 
$$\begin{align*}
P(T > t) &= 1 - P(T \leq t) \\[4pt]
&= 1 - (1 - e^{-\lambda t}) \\[4pt]
&= e^{-\lambda t} \tag{Exponential decay}
\end{align*}$$

Conditionally for $t,s > 0$,
$$\begin{align*}
P(T>t+s \:|\: T>s) &= \frac{P(T>t+s, T>s)}{P(T>s)}\\[4pt]
&= \frac{P(T>t+s)}{P(T>s)}\\[4pt]
&= \frac{e^{-\lambda(t+s)}}{e^{-\lambda s}} \\[4pt]
&= e^{-\lambda t}\\[4pt]
&= P(T > t)
\end{align*}$$
- i.e. the exponential distribution is *memoryless*.


