# Definition

>[!Definition] Hilbert Space
>A **Hilbert Space** is a *complete*, *inner product* space (with induced norm)

## Examples

1. $\mathbb{R}^N$ with $\langle x,y\rangle= x \cdot y$
2. $\mathbb{C}^N$ with $\langle x,y \rangle = x \cdot \overline{y}$
3. $\ell^2$ with $\langle x,y \rangle = \sum_{k=1}^\infty x_k\overline{y}_k$
4. $L^2([a,b])$ with $\langle f,g \rangle = \int_a^b f(x) \overline{g(x)}\:dx$

### Non-Examples
1. $\ell^p$ for $p\neq 2$
   For $p = \infty$, take $x = (1,0,0,...)$, $y=(1,1,0,0,...)$
   $5= 4+1 = \|x+y\|^2_\infty + \|x-y\|^2_\infty \neq 2(\|x\|^2_\infty + \|y\|^2_\infty) = 4$ 
2. $L^p([a,b])$ for $p\neq 2$
3. $(C([a,b]), \|\cdot\|_\infty)$ 



# Parallelogram Identity

>[!Definition] 
>In an inner product space $$\|x+y\|^2 + \|x-y\|^2 = 2(\|x\|^2 + \|y\|^2)\qquad \forall x,y \in X$$


# Banach Space Criteria

>[!Theorem]
>A Banach space $(X, \|\cdot\|)$ is a Hilbert space $\iff$ the Parallelogram identity holds



# Orthonormal System

## Definition

>[!Definition] 
>Let $\mathcal{H}$ be a Hilbert space over $\mathbb{K}$. A set $S \subseteq \mathcal{H}$ is an **orthonormal system** if $$\langle e, e' \rangle=\begin{cases}
 1 & e' = e \\ 0 & e' \neq e
\end{cases}$$
for all $e,e' \in S$.

>[!Definition] 
>An orthonormal system $S$ is **complete** if $\overline{\text{Span}(S)} = \mathcal{H}$. 
>A complete orthonormal system is called a **Hilbert/orthonormal basis**.

### Examples
1. $\mathcal{H}= \mathbb{C}^N$, where $\langle x,y \rangle =\sum_{i=1}^N x_i \bar{y_i}$.
   Then clearly $S := \{e_i \:|\: 1 \leq i \leq N\}$ where $e_i = (0,0,...,1,...,0)$ is a basis and $\text{Span}(S) = \mathbb{C}^N$.

2. $\mathcal{H} = \ell^2(\mathbb{K})$. Then the  set $S := \{e_n \:|\: n \geq 1\}$ is orthonormal.
   Also $\text{Span}(S) = \{\text{finitely supported sequences}\}$ which we proved to be dense in $\ell^2$. Hence $S$ is a Hilbert basis

3. $\mathcal{H}= L_\mathbb{C}^2([0,2\pi])$. Then the set $S = \{\tfrac{1}{\sqrt{2\pi}}e^{int} \:|\: n \in \mathbb{Z}\}$ is orthonormal. Let $e_n(t) = \frac{1}{\sqrt{2\pi}}e^{int}$. Then 
   $$\begin{align*}
\langle e_m , e_n \rangle &= \int_0^{2\pi} e_m(t) \overline{e_n(t)}\:dt \\
&= \frac{1}{2\pi}\int_0^{2\pi}e^{i(m-n)t}\:dt \\[3pt]
&= \begin{cases}
1 & m=n  \\
0 & m \neq n
\end{cases}
\end{align*}$$
	to show that $\overline{\text{Span}(S)}= L_\mathbb{C}^2 ([0,2\pi])$ we need Stone-Weierstrass.


# General Fourier Series
Fourier series can be generalised to arbitrary Hilbert spaces with arbitrary Hilbert bases.

