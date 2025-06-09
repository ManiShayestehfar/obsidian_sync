>[!warning]
>THIS IS NOT [[Conditional Expectation]]

>[!info] Definition
>For $y \in L^1$ we define the *RV* **Conditional Expectation** of $Y$ given $X$ as 
>$$\underbrace{E(Y|X)}_{\text{notation}}(\omega) = E[Y | X = X(\omega)]$$
>

![[Pasted image 20250411151759.png]]

- Note that $E(Y|X)$ is *constant* on the event $X = x_k$ 

>[!info] Definition
>$h: X(\Omega) \to \mathbb{R}$ as $h(x) = E(Y|X=x)$ 

>[!tip] Claim 
>$$E(Y|X) = h(X) $$
##### Proof
$$h(X(\omega)) = E(Y|X=X(\omega)) = E(Y|X)(\omega)$$

# Example
## Fair die

Roll a fair die and let $Y$ = outcome and $X=1_{\{\text{even outcome}\}}$
	- Suppose $A \subset \Omega$
	- For $A = \{1,3,5\}$, $X=0 \implies E(Y|X=0) = 3$
	- For $A = \{2,4,6\}$, $X = 1\implies E(Y|X=1) = 4$
	$$E(Y|X)(\omega) = \begin{cases}
3 & \omega \in \{1,3,5\} \\
4 & \omega \in \{2,4,6\}
\end{cases}$$

$h(0) = 3, h(1) = 4$. Note that here also 
$$\begin{align*}
E[E(Y|X)] &= E[h(X)] \\[4pt]
&= h(0) \cdot P(X=0) + h(1) \cdot P(X=1)\\[4pt]
&= 3 \cdot 1/2 + 4 \cdot 1/2 \\[4pt]
&= 3.5 = E(Y) 
\end{align*}$$

## Random Sum

$T=\sum_1^N X_i$, $X_i \in L^1$. For $n \in N(\Omega)$, 
$$\begin{align*}
h(n) &= E(T|N=n)\\[4pt]
&= nE(X_i) \tag{This is a number}
\end{align*}$$
Therefore,
$$\begin{align*}
E(T|N) &= h(N) \\[4pt]
&= NE(X_i) \tag{this is an RV}
\end{align*}$$
$\implies$ if $N \in L^1$, $E[E(T|N)] = E(N)E(X_i)$ 

>[!warning] For continuous RV
>![[Conditional Expectation _RV_-1747387079619.png]]


# Theorem

Theorem connecting to [[Conditional Expectation]]

>[!example] Theorem
>If $Y \in L^1$ then $E(Y|X) \in L^1$ and 
>$$E[E(Y|X)] = E(Y).$$
>The equation holds for $Y\geq 0$ and $Y\leq 0$. 
>
>![[Pasted image 20250411155022.png|450]]
##### Proof

Recall that $E(Y|X) = h(X)$ where $h(x) := E(Y|X=x)$. Hence $E(Y|X) \in L^1 \iff h(X) \in L^1$.
$$\begin{align*}
\sum_{x\in X(\Omega)} |h(x)| P(X=x) &= \sum_x |E(Y|X=x)|\:\cdot\:P(X=x)\\[4pt]
&= \sum_x\left|\sum_y y P(Y=y | X=x) \right |\:\cdot\: P(X=x) \\[4pt]
&\leq \sum_x \sum_y |y| \cdot |P(Y=y | X=x)| \:\cdot\: P(X=x) \\[4pt]
&\overset{\text{Fubini}}{=} \sum_y |y| \sum_x |P(Y=y|X=x)| \:\cdot\: P(X=x) \\[4pt]
&= \sum_y |y|P(Y=y) \quad < \infty

\end{align*}$$
$\implies E(Y|X) \in L^1$. Also following the same process without $|\cdot|$, 
$$\implies E[E(Y|X)] = E[h(x)] = \sum_xh(x) P(X=x) = E(Y)$$





