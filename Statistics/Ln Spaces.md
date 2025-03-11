>[!info] Definition 
>Denote $L^1 = L^1(\Omega, \mathcal{F}, P) = L^1(\Omega)$ the space of all discrete random variables $X: \Omega \to \mathbb{R}$ such that with $\{x_n\} = X(\Omega)$,
>$$\sum_n |x_n|\cdot p_X(x_n) < \infty $$
>i.e. 
>$$\begin{align*} 
>L^1 &= \{X: \sum_k |x_k|p_X(x_k) < \infty\} \\
>L^2 &= \{X: \sum_k x_k^2 p_X(x_k) < \infty\}
\end{align*}$$

> [!tip] Claim 1
> $X \in L^2 \implies X \in L^1$    **(for finite-measure spaces only)**
#### Proof
Know that $|x| < 1+x^2 \quad \forall x \in \mathbb{R}$. Hence
$$\begin{align*}
\sum_k |x_k|\:p_X(x_k) &\leq \sum_k (1+x_k^2)\:p_X(x_k) \\
&= \sum_k p_X(x_k) + \sum_k x_k^2\:p_X(x_k) &< \infty
\end{align*}$$
where the second term is finite as $x_k \in L^2$.  $\square$

>[!tip] Corollary 1
>$X \in L^2 \iff \text{Var}(X)$ exists and is **finite**.
#### Proof
Know that for $X \in L^1$, $\text{Var}(X) < \infty \iff X \in L^2 \iff X \in L^1$, by Claim 1.
