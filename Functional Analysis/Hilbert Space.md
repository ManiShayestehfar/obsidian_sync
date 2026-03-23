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


