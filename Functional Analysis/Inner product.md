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


# Cauchy-Schwartz Inequality

>[!Theorem] Cauchy-Schwartz Inequality
>Let $X$ be an inner product space. For all $x,y \in X$, $$|\langle x,y \rangle| \leq \|x\|$$
>