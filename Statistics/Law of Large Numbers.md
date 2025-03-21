Let $X_1,X_2,...$ be iid $\text{Bernoulli}(p)$ RVs and let $S_n = \sum_{i=1}^n X_i$

$S_n \sim \text{Binom}(n,p)$, and
$$\begin{align*}
E\left(\frac{S_n}{n}\right) &= \frac{1}{n}E(S_n) = \frac{1}{n}\cdot np=p=E(X_i) \\[8pt]
V\left(\frac{S_n}{n}\right) &= \frac{1}{n^2}V(S_n)=\frac{1}{n^2}np(1-p) =\frac{p(1-p)}{n} \longrightarrow 0\quad \text{as $n \to \infty$}
\end{align*}$$

>[!quote] Intuition
>$S_n/n \to p = E(S_n/n) = E(X_i)$


Using [[Convergence in Probability]], 

>[!tip] Claim 1
>The RVs $Y_n := S_n/n$ converge to the constant RV $Y:=E(X_i)=p$ in probability.
##### Proof

For any $\varepsilon > 0$,
$$\begin{align*}
P(|S_n/n-p| \geq \varepsilon) &\leq \frac{V(S_n/n)}{\varepsilon^2} \\[5pt]
 &= \frac{1}{n}\frac{p(1-p)}{\varepsilon^2} \longrightarrow 0 \quad \text{as $n \to \infty$} \quad \square
\end{align*}$$

# Weak Law of Large Numbers (WLLN)

>[!abstract] Theorem
>If $X_1,X_2,...$ are iid $L^1$ RVs with mean $\mu$, then for $S_n = \sum_{i=1}^n X_i$
>$$\frac{S_n}{n}\longrightarrow \mu \quad\quad \text{as $n \to \infty$ in probability.}$$


