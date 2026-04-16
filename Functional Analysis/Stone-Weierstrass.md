# Motivation
- Used to show completeness of various orthonormal systems in $L^2$
- The theorem is really about uniformly approximating functions $f:X \to \mathbb{K}$ with $X$ being compact and Hausdorff (e.g. $X = [a,b]$, closed unit disc, unit circle, etc.)

# Weierstrass Approximation Theorem (1885)

>[!Theorem]
>Let $f \in C[a,b]$ and let $\varepsilon >0$.
>There exists a polynomial $p(x)$ such that $|f(x) - p(x)|< \varepsilon$ for all $x \in [a,b]$.
>i.e. $\|f-p\|< \varepsilon$ 

- This implies that $\overline{\mathcal{P}[a,b]} = C[a,b]$ (w.r.t $\|\cdot\|_\infty$)


# Stone-Weierstrass

>[!Theorem]
>Let $X$ be a compact, Hausdorff normed vector space and let $\mathcal{A}$ be a subalgebra of $C(X)$. 
>If:
>1. $\mathcal{A}$ is unital
>2. $f \in \mathcal{A} \implies f^* \in \mathcal{A}$ where $f^*(x) = \overline{f(x)}$
>3. $\mathcal{A}$ is separating points of $X$
>Then, $\overline{\mathcal{A}} = C(X)$ (w.r.t $\|\cdot\|_\infty$)

>[!Remark]
>The general Weierstrass theorem holds:
>1. $1 \in \mathcal{P}[a,b]$
>2. If $p(x) = \sum_{i=0}^n a_ix^i$, then $p^*(x) = \sum_{i=0}^n \overline{a_i}x^i \in \mathcal{P}[a,b]$ 
>3. If $x \neq y$, then $p(x) = x$ has $p(x) \neq p(y)$

## Absolute Value 

>[!Lemma]
>$f(t) = |t|$ can be uniformly approximated by $\mathcal{P}[-1,1]$.
##### Proof
$|t| = \sqrt{1 + (t^2-1)} = \sum_{n=0}^\infty \binom{1/2}{n}(t^2-1)^n$   if $|t^2-1|\leq 1$.
So for $t \in [-\sqrt{2}, \sqrt{2}]$, define $P_N(t) := \sum_{n=0}^N \binom{1/2}{n}(t^2-1)^n$ which is a polynomial.
Then $||t|-p_N(t)| = \left|\sum_{n=N+1}^\infty \binom{1/2}{n} (t^2-1)^n\right| \leq \sum_{n=N+1}^{\infty} \left|\binom{1/2}{n}\right| \longrightarrow 0$ as $N \to \infty$.

Thus $\||\cdot| - p_N\|_\infty \to 0$ as $N \to \infty$.  $\square$


>[!Lemma]
>Let $\mathcal{A}$ be a unital subalgebra of $C_\mathbb{R}(X)$.
>Let $f,f_1,...,f_n \in \mathcal{A}$. Then:
>1. $|f| \in \overline{\mathcal{A}}$,
>2. $\min(f_1,...,f_n), \max(f_1,...,f_n \in \overline{\mathcal{A}})$.
##### Proof
###### 1)
Replace $f$ with $\frac{f}{\|f\|}$ so assume $\|f\|_\infty =1$. 
By the previous lemma, for $n \geq 1$, there exists a polynomial $p_N:[-1,1]\to \mathbb{R}$ such that $||t| - p_N| < \frac{1}{n}$ for all $t \in [-1,1]$.

Since $|f(x)|\leq \|f\|_\infty = 1$, then we are guaranteed that $p_N(f(x))$ has valid input.
Then $|f(x) - p_N(f(x))| < \frac{1}{n}\qquad \forall n \geq 1, x \in X$.
$\implies \||f| - p_N(f)\|_\infty < \frac{1}{n}$.
But $p_N(f) = \sum_{i=0}^n \alpha_i f^i$ and so $p_n(f) \in \mathcal{A}$ (a *unital* subalgebra). 
Hence $|f| \in \overline{\mathcal{A}}$. $\square$

###### 2)
We can use $\max(f,g) = \frac{f+g + (f-g)}{2}$ and $\min(f,g) = \frac{f+g - (f-g)}{2}$ and induction (also using part $(a)$). $\square$


## Proof of Stone-Weierstrass Theorem

- We first consider $\mathbb{K} = \mathbb{R}$. Let $f \in C_\mathbb{R}(X)$ and let $\varepsilon > 0$.
- We want to find $p \in \mathcal{A}$ such that $|f(z) - p(z)| < \varepsilon$     $\forall z \in X$.
- Assume $\mathcal{A}$ is closed. If not, Call $\mathcal{A} = \overline{\mathcal{A}}$ which is still a subalgebra.

>[!Lemma] Lemma 1
> Let $x,y \in X$ be fixed. Then there is $p_{xy} \in \mathcal{A}$ such that $p_{xy}(x) = f(x)$ and $p_{xy}(y)= f(y)$.
> 



