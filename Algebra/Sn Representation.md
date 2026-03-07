$G = S_n$, $V = \mathbb{F}^n = \left\{\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix}\::\:\lambda_i \in \mathbb{F}\right\}$.

The $S_n$-representation is given by the group action $$g\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix} = \begin{pmatrix}\lambda_{g^{-1}(1)} \\ \vdots \\ \lambda_{g^{-1}(n)}\end{pmatrix} \iff ge_i = e_{g(i)}$$
**Is $V$ irreducible?** Yes for $n=1$. Otherwise we have:

*Trivial Representation:*
$$I  = \left\{\begin{pmatrix}\lambda \\ \vdots \\ \lambda\end{pmatrix}\::\:\lambda \in \mathbb{F}\right\} \leq V$$

*Standard Representation:*
$$W = \left\{\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix}\::\: \sum_i\lambda_i = 0\right\} = \left\langle\begin{pmatrix}1 \\ 0 \\\vdots \\ -1\end{pmatrix},\begin{pmatrix}0 \\ 1 \\\vdots \\ -1\end{pmatrix},\cdots,\begin{pmatrix}0 \\ 0 \\\vdots \\ -1\end{pmatrix}\right\rangle$$
so $\dim W = n-1$


>[!Claim]
>IF $\text{char } \mathbb{F} \nmid n$, then $W$ is irreducible and $V = I \oplus W$ as a $G$-module
##### Proof
Notice that $I \subseteq W \iff \text{char }\mathbb{F} \mid n$ so if $\text{char }\mathbb{F} \nmid n$ then $V = I \oplus W$.
We prove that $W$ is irreducible.

Let $U$ be a nonzero submodule of $W$. Fix $u = (u_1,...,u_n) \in U$ with $u \neq0$