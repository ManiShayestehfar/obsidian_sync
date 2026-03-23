# Definition

>[!Definition] Inner Product
>Let $X$ be a [[Vector Space]] over $\mathbb{K}$. An **inner product** on $X$ is a function $\langle -,-\rangle: X \times X \to \mathbb{K}$ such that for $x,y,z \in X$ and $\lambda,\mu \in \mathbb{K}$:
>1. $\langle \lambda x + \mu y, z \rangle = \lambda \langle x,z \rangle + \mu \langle y,z \rangle$
>2. $\langle y,x \rangle= \overline{\langle x,y \rangle}$ 
>3. $\langle x,x \rangle \geq 0$ with equality $\iff x=0$

- $(X, \langle -,-\rangle)$ is an **inner product space**.
	- $$\begin{align*} \langle z, \lambda x+\mu y \rangle &= \overline{\langle\lambda x + \mu y, z \rangle} \\
&= \overline{\lambda}\:\overline{\langle x,z \rangle  } + \overline{\mu}\:\overline{\langle y,z \rangle  } \\
&= \overline{\lambda}\:{\langle x,z \rangle  } + \overline{\mu}\:{\langle y,z \rangle  }
\end{align*}$$
	so $\langle -,-\rangle$ is *conjugate linear* in  second variable. So $\langle-,- \rangle$ is sesquilinear

## Examples 

1. $\mathbb{R}^N$ with $\langle x,y\rangle= x \cdot y$
2. $\mathbb{C}^N$ with $\langle x,y \rangle = x \cdot \overline{y}$
3. $\ell^2$ with $\langle x,y \rangle = \sum_{k=1}^\infty x_k\overline{y}_k$
4. $L^2([a,b])$ with $\langle f,g \rangle = \int_a^b f(x) \overline{g(x)}\:dx$


# Cauchy-Schwarz Inequality

>[!Theorem] Cauchy-Schwarz Inequality
>Let $X$ be an inner product space. For all $x,y \in X$, $$|\langle x,y \rangle| \leq \|x\| \|y\|$$
##### Proof
Let $\lambda \in \mathbb{K}$. Then 
$$\begin{align*}
0 \leq \langle x - \lambda y, x - \lambda y\rangle &= \langle x,x\rangle - \overline{\lambda}\:\langle x,y \rangle - \lambda \langle y,x \rangle + |\lambda|^2 \langle y,y \rangle \\[3pt]
&= \|x\|^2 - \overline{\lambda}\:\langle x,y \rangle - \lambda \overline{\langle x,y \rangle} + |\lambda|^2 \|y\|^2 \\[3pt]
&= \|x\|^2 - 2\: \Re{(\lambda\overline{\langle x,y \rangle})} +|\lambda|^2 \|y\|^2
\end{align*}$$
Choose $\lambda = \frac{\langle x,y\rangle}{\|y\|^2}$, assuming $y \neq 0$.
Then $$0 \leq\|x\|^2 - 2 \frac{|\langle x,y \rangle|^2}{\|y\|^2} +  \frac{|\langle x,y \rangle|^2}{\|y\|^2}$$
and so $|\langle x,y \rangle| \leq \|x\| \|y\|$.

If $y=0$, then clearly $|\langle x,0\rangle| 0  = \|x\|\|0\|$.   $\square$


# Induced Inner Product

>[!Proposition]
>Let $X$ be a vector space over $\mathbb{K}$ with inner product $\langle-,-\rangle$.
>Then it induces a norm defined as $\|x\| := \sqrt{\langle x,x\rangle}$.
>
##### Proof
1. Clearly $\|x\| \geq 0$
2. $\|\lambda x\|= \sqrt{\langle\lambda x,\lambda x \rangle}= \lambda \sqrt{\langle x,x\rangle} = \lambda \|x\|$ 
3. Triangle inequality: Using Cauchy-Schwartz, $|\langle x,y \rangle|\leq \|x\| \|y\|$ with equality if $\text{Span}(x,y) = 1$
   Then $$\begin{align*}
\|x+y\|^2 = \langle x+y , x+y \rangle &= \langle x,x \rangle + 2\Re \langle x,y \rangle + \langle y,y \rangle \\[3pt]
&\leq \|x\|^2 + 2\|x\|\|y\| + \|y\|^2 \\[3pt]
&\leq \|x\|^2 + \|y\|^2
\end{align*}$$
$\square$
