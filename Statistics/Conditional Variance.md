We discussed one summary of conditional probabilities, that is [[Conditional Expectation]].

>[!info] Definition
>The **conditional variance** of $Y$ given $X=x$ is
>$$V(Y|X=x) = E(Y^2|X=x) - E^2(Y|X=x)$$
>Note that if $Y \in L^2$, then $Y,Y^2 \in L^1 \implies$ RHS is well-defined for $X \in X(\Omega)$

![[Pasted image 20250413083319.png]]

- Note that $E(\varphi(y)) = \sum_y \varphi(y) P(Y=y|X=x) = \sum_y \varphi(y) q_x(y)$

For $Y \in L^2$, and $X \in X(\Omega)$,
$$\begin{align*}
g(x) &:= E(Y^2|X=x) = \sum_y y^2 q_x(y) \tag{$<\infty$} \\[5pt]
h(x) &:= E(Y|X=x) = \sum_y y q_x(y) \tag{$\in \mathbb{R}$} \\[5pt]
&\implies v(x) := V(Y|X=x) = g(x) - h(x)^2 \in \mathbb{R}
 
 \end{align*}$$

# Conditional Variance (RV)

Similar to [[Conditional Expectation (RV)]],

>[!info] Definition
>$$\underbrace{V(Y|X)}_{\text{notation}}(\omega) := V(Y|X=X(\omega))$$

![[Pasted image 20250413085918.png]]


# Theorem 

>[!tip] Theorem
>For $y \in L^2$,
>$$V(Y) = V[E(Y|X)] + E[V(Y|X)]$$

![[Pasted image 20250413090433.png]]
##### Proof
Firstly, note that $Y \in L^2 \implies g(x) \in L^1$, and $0 \leq h^2(x) \leq g(x) \implies h(x) \in L^1$. Then
$$\begin{align*}
E[V(Y|X)] &= E[g(x) - h^2(x)] \\[4pt]
&= E[g(x)] - E[h^2(x)] \tag{since $g,h \in L^1$}
\end{align*}$$
Also
$$V[\underbrace{E(Y|X)}_{h(X)\in L^1}] = E[h^2(X)] - E^2[h(x)]$$
$$\begin{align*}
\implies E[V(Y|X)] + V[E(Y|X)] &= E[g(x)] - E^2[h(x)] \\[5pt]
&= E[E(Y^2|X)] - E^2[E(Y|X)] \\[5pt]
&= E[Y^2] - E^2(Y)\\[5pt]
&= V(Y) \quad\quad \square
\end{align*}$$


# Examples

## Random Sums

$T = \sum_1^N X_i$ a random sum, $N$ is ind. of the iid $X_i \in L^2$, $n\in N(\Omega)$

- Recall that the conditional distribution of $T$ given $N=n$ is the same as that of $S_n = \sum_1^n X_i$.
$$\implies V(T|N=n) = V(S_n) = nV(X_i).$$
$$V(Y|X)(\omega) = v(X(\omega)) = g(X(\omega)) - h^2(X(\omega))$$
so for $T = \sum_1^N X_i$ 
$$V(T|N) = v(N) = N\cdot V(X_i) \tag{an RV}$$

- If $T \in L^2$,
$$\begin{align*}
V(T) &= V[E(T|N)] + E[V(T|N)]\\[4pt]
&= V[N\cdot E(X_i)] + E[N\cdot V(X_i)] \\[4pt]
&= E^2(X_i)V(N) + V(X_i)E(N)
\end{align*}$$
In our Faulty monitor case,
$$V(T) = p^2\cdot \lambda + p(1-p)\cdot \lambda = \lambda p$$
