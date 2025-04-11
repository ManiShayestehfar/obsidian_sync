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

# Example
 
-  Roll a fair die and let $Y$ = outcome and $X=1_{\{\text{even outcome}\}}$
	- Suppose $A \subset \Omega$
	- For $A = \{1,3,5\}$, $X=0 \implies E(Y|X=0) = 3$
	- For $A = \{2,4,6\}$, $X = 1\implies E(Y|X=1) = 4$
	$$E(Y|X)(\omega) \begin{cases}
3 & \omega \in \{1,3,5\} \\
4 & \omega \in \{2,4,6\}
\end{cases}$$

