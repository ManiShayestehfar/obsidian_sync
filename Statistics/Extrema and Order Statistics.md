>[!warning] Motivation
>Let $X_1,...,X_n$ be i.i.d RVs with CDF $F$. 
>Let $U = X_{(n)} = \max\{X_1,...,X_n\}$, $V = X_{(1)} = \min\{X_1,...,X_n\}$.
>
>*What are the distributions of $U$ and $V$?*

$$\begin{align*}
F_U(u) &= P(U \leq u) \\[4pt]
&= P(X_1\leq u, ...,X_n \leq u)\\[4pt]
&= \prod_{i=1}^n P(X_i \leq u) \\[4pt]
&= [F_X(u)]^n
\end{align*}$$
If $F$ has a density $f$, then by chain rule so does $F_U$
$$F_U(u) = n[F_X(u)]^{n-1}\:f(u)$$









