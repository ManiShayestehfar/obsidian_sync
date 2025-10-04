
# Definition

>[!def] Fundamental group
>The **fundamental group** $\pi_1(X,x_0)$ of $X$ based at base point $x_0$ is the set of all homotopy classes $[f]$ of loops $f:I \to X$ based at $x_0$.

##### Proof: Group properties

*Well-definedness:* If $f_0\simeq f_1$ , $g_0\simeq g_1$ then $f_0 \circ g_0 = f_1 \circ g_1$. Also composing two paths gives a paths so we have closure.

*Associativity:* 
$$\begin{align*}
([f][g])[h] &= [f \circ g][h] \\
&= [(f \circ g) \circ h] \\
&= [f \circ (g \circ h)] \\
&= [f][g \circ h] \\
&= [f]([g][h])
\end{align*}$$
*Identity:* Let $c_0 : I \to X$ be the constant path at $x_0$. Then
$$\begin{align*}
[c_0][f] &= [c_0 \circ f] = [f] \\
[f][c_0] &= [f \circ c_0] = [f]
\end{align*}$$
and so $c_0$ is the identity element. 


## Examples

1. $X = \mathbb{R}^n$, $x_0 \in \mathbb{R}^n$, then $\pi_1(X,x_0) \cong 1$ as every loop in $\mathbb{R}^n$ is straight-line homotopic to the constant path.
2. Same for any convex subset $C \subseteq \mathbb{R}^n$ with $x_0 \in C$
3. $\pi_1(S^1,x_0) \cong \mathbb{Z}$ for all $x \in S^1$
4. $X$ the "figure-8" with $a,b$ loops based at $x_0$, then $\pi_1(X,x_0) = F(a,b)$


# Dependence of Fundamental group on basepoint

