# $C_3$ Representation Example

Let $G = C_3 = \{1,x,x^2\} = \langle x\:|\:x^3 = 1 \rangle$.
Let $V = \{(\lambda, \mu, \nu)\: :\: \lambda, \mu, \nu \in \mathbb{F}\}\cong \mathbb{F}^3$ be a vector space with $C_3$-action
$$x\cdot(\lambda, \mu, \nu) = (\nu, \lambda, \mu)$$
$$\implies 1\cdot(\lambda,\mu,\nu) = (\lambda,\mu,\nu),\quad x\cdot(\lambda,\mu,\nu) = (\nu,\lambda,\mu),\quad x^2\cdot(\lambda,\mu,\nu) = (\mu,\nu,\lambda)$$
Then we have the following subrepresentations:

*Trivial Representation:*
$$I = \{(\lambda,\lambda,\lambda)\::\:\lambda \in \mathbb{F}\}\leq V$$
*$L_\omega$ Representation:*
$$W = \{(\lambda,\mu,\nu) \::\: \lambda+\mu+\nu = 0\}$$

**Finding All $C_3$-Representations:**
Let $Z = \mathbb{F}z$ be a $1$-dimensional $C_3$-submodule of $V$
Then $gz = \lambda_gz$ for some $\lambda_g \in \mathbb{F}$, or equivalently $Xz = \lambda z$ for some matrix representation of the group action $X$.
- Hence $1$-dimensional subspaces are eigenspaces of $X$

For $C_3$: $$X = \begin{pmatrix}0&0&1 \\ 1 & 0 & 0 \\ 0 & 1 & 0\end{pmatrix}$$
so $X^3=I \implies \det(X-\lambda I)= \lambda^3 +1$.

*Over $\mathbb{R}$:* $I$ is the unique $1$-dimensional subspace
*Over $\mathbb{C}$:* $\lambda = 1,\omega,\omega^2$ for $\omega= e^{2\pi i /3}$ so we have three $1$-dimensional subspaces
$$I = I_{trivial}, \quad \quad L_\omega = \{\lambda (1, \omega^2, \omega)\:|\: \lambda \in \mathbb{C}\},\quad\quad L_\omega = \{\lambda (1, \omega, \omega^2)\:|\:\lambda \in \mathbb{C}\}$$
$$$$
