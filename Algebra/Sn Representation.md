$G = S_n$, $V = \mathbb{F}^n = \left\{\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix}\::\:\lambda_i \in \mathbb{F}\right\}$.

The $S_n$-representation is given by the group action $$g\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix} = \begin{pmatrix}\lambda_{g^{-1}(1)} \\ \vdots \\ \lambda_{g^{-1}(n)}\end{pmatrix} \iff ge_i = e_{g(i)}$$
**Is $V$ irreducible?** Yes for $n=1$. Otherwise we have:

*Trivial Representation:*
$$I  = \left\{\begin{pmatrix}\lambda \\ \vdots \\ \lambda\end{pmatrix}\::\:\lambda \in \mathbb{F}\right\} \leq V$$

*Standard Representation:*
$$W = \left\{\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix}\::\: \sum_i\lambda_i = 0\right\} = \left\langle\begin{pmatrix}1 \\ 0 \\\vdots \\ -1\end{pmatrix},\begin{pmatrix}0 \\ 1 \\\vdots \\ -1\end{pmatrix},\cdots,\begin{pmatrix}0 \\ 0 \\\vdots \\ -1\end{pmatrix}\right\rangle$$
so $\dim W = n-1$


>[!Claim]
>If $\text{char } \mathbb{F} \nmid n$, then $W$ is irreducible and $V = I \oplus W$ as a $G$-module
##### Proof
Notice that $I \subseteq W \iff \text{char }\mathbb{F} \mid n$ so if $\text{char }\mathbb{F} \nmid n$ then $V = I \oplus W$.
We assume $\text{char } \mathbb{F} \nmid n$ (hence $I \not \subseteq W$) to prove that $W$ is irreducible.

Let $U$ be a nonzero submodule of $W$. Fix $u = (u_1,...,u_n) \in U$ with $u \neq0$.
Since by assumption $I \not\subseteq W$, then there exists $i < j$ with $u_i \neq u_j$ such that 
$$(i,j)\cdot u = (u_1,...,u_j,...,u_i,...,u_n) \in U$$
Hence $U - (i,j)\cdot u = (0,...,u_i-u_j,...,u_j-u_i,...,0) = (u_i-u_j)\underbrace{(0,...,1,...,-1,...,0)}_{v} \in U$.
So $v \in U$.
Now consider $(a,i)(n,j)v = (0,...,1,...,0,-1) \in U$ where we swap $i,j$ with $a,n$ respectively for $0\leq a\leq n$.
Then $U\subseteq W$ since it contains the basis vectors of $W$. $\implies U =W$.
Therefore $W$ is irreducible because every nonzero submodule of $W$ is equal to $W$.  $\square$



# $S_3$
Let $G=S_3$ and let $\text{char } \mathbb{F}=0$, or $\text{char }\mathbb{F} > 3$.

| Irreps                                   | Name         | Action                                                                                       | Dimension |
| ---------------------------------------- | ------------ | -------------------------------------------------------------------------------------------- | --------- |
| $\bf{1}$                                 | Trivial Rep  | $g \mapsto 1$                                                                                | 1         |
| $\boldsymbol{\varepsilon}_{\text{sign}}$ | Sign Rep     | $g \mapsto \text{sgn}(g)$                                                                    | 1         |
| $W$                                      | Standard Rep | $\left\{ \begin{pmatrix} x_1 \\ x_2 \\ x_3 \end{pmatrix}\: : \: x_1 + x_2 + x_3 = 0\right\}$ | 2         |
$\implies \# S_3 = 6 = |G| = 1^2 + 1^2 + 2^2$ 

# $S_4$
Let $G=S_4$ and let $\text{char } \mathbb{F}=0$, or $\text{char }\mathbb{F} > 4$.

| Irreps                             | Name                | Action                                                                                                   | Dimension |
| ---------------------------------- | ------------------- | -------------------------------------------------------------------------------------------------------- | --------- |
| $\bf{1}$                           | Trivial Rep         | $g \mapsto 1$                                                                                            | 1         |
| $\xi_{\text{sign}}$                | Sign Rep            | $g \mapsto \text{sgn}(g)$                                                                                | 1         |
| $W$                                | Standard Rep        | $\left\{ \begin{pmatrix} x_1 \\ x_2 \\ x_3 \\ x_4\end{pmatrix}\: : \: x_1 + x_2 + x_3 + x_4 = 0\right\}$ | 3         |
| $W' = \xi_{\text{sign}} \otimes W$ | Signed Standard Rep | $g \mapsto \text{sgn}(g)\rho_{\text{std}}(g)$                                                            | 3         |
| ...                                | ...                 | ...                                                                                                      | 2         |
Notice that for the last subrep, we could either have 2 x 1-dim or 1 x 2-dim irresp.
But $1$-dim reps are group homomorphisms $G \overset{\varphi}{\longrightarrow} F^{\times}$. We know
- $\ker \varphi \trianglelefteq G$ is a normal subgroup, and
- $S_4$ has only $2$ x $1$-dim irreps as its only normal subgroups are $S_4$ and $A_3$.
Therefore the dimension of the left over irrep must be $2$
