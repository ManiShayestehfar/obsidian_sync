>[!info] Definition 
>Denote $L^1 = L^1(\Omega, \mathcal{F}, P) = L^1(\Omega)$ the space of all discrete random variables $X: \Omega \to \mathbb{R}$ such that with $\{x_n\} = X(\Omega)$,
>$$\sum_n |x_n|\cdot p_X(x_n) < \infty $$
>i.e. 
>$$\begin{align*} 
>L^1 &= \{X: \sum_k |x_k|\:p_X(x_k) < \infty\} \\
>L^2 &= \{X: \sum_k x_k^2\:p_X(x_k) < \infty\}
\end{align*}$$
![[Screenshot 2025-03-12 at 10.18.05 am.png]]


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


>[!tip] Claim 2
>$$X,Y \in L^2 \implies XY\in L^1$$
#### Proof
From the AM-GM inequality, for $x,y\in \mathbb{R}$
$$|xy| \leq \frac{x^2+y^2}{2}.$$
Let $Z = g(X,Y) = XY$, then
![[Screenshot 2025-03-12 at 2.20.27 pm.png]]$\square$ 

>[!tip] Corollary 2 
>If $X,Y \in L^2$, then $\forall \alpha,\beta \in \mathbb{R}$
>$$\alpha X + \beta Y \in L^2.$$
>i.e. $L^2$ is a [[Vector Space|vector subspace]] of $L^1$
>
#### Proof
$$Z^2 = (\alpha X + \beta Y)^2 = \alpha^2 X^2 + 2\alpha\beta XY + \beta^2 Y^2 \in L^1$$

As proved above, $Z \in L^2 \iff Z^2 \in L^1$. This is true as $X^2,Y^2, XY \in L^1$.  $\square$ 


