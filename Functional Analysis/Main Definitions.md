# Compactness
Let $(X,d)$ be a metric space.

>[!definition] 
>$Y \subset X$ is **compact** if for all open covers of $Y$, there exists a finite subcover.
>i.e. $\exists\: (U_\alpha)_{\alpha \in I}$ such that $Y \subset \bigcup_{\alpha = 0}^N U_\alpha$ for some $N > 0$.


# Totally Boundedness

>[!Definition]
>$Y \subset (X,d)$ is **totally bounded** if $\forall \varepsilon > 0$, there exists a finite collection of $B_\varepsilon$ which covers $Y$.

- In a metric space: totally bounded $\implies$ bounded

# Fish's Heine-Borel Theorem

>[!Theorem]
>$(X,d)$ a metric space and $Y \subset X$. Then the following are equivalent:
>1. $Y$ is compact
>2. Every sequence in $Y$ has a convergent subsequence (i.e. $Y$ is sequentially compact)
>3. $Y$ is complete + totally bounded
##### Proof
NEED TO PROVE

## Generalised Heine-Borel Theorem

>[!Theorem]
>If $Y \subset (\mathbb{K}^N, \|\cdot\|)$. $Y$ is compact $\iff$ $Y$ is closed + bounded.
##### Proof
NEED TO PROVE


# Closed Ball

>[!Definition] Closed Ball
>
Let $(X,\|\cdot\|)$ be a [[Normed Spaces|normed vector space]] over $\mathbb{K}$. The **Closed ball** is
$$\bar{B}(0,1) = \{x \in X \:|\: \|x\| \leq 1\}$$

# Dense

>[!Definition] Dense
>$Y\subseteq X$ a metric space is **dense** in $X$ if $\bar{Y} = X$.
>Equivalently, $\forall x\in X, \exists (y_n) \subset Y$ such that $y_n \to x$.


# Cauchy-Schwarz in R^n

I keep forgetting this so here it is:
$$\left(\sum_{i=1}^n u_iv_i\right)^2 \leq \left(\sum_{i=1}^n u_i^2\right) \left(\sum_{i=1}^n v_i^2\right)$$

# Unital Associative Algebra

$C(X)= \{f: X \to \mathbb{K} \:\text{ continuous }\}$ is normed with $\|\cdot\|_\infty$, where
- $(fg)(x) = f(x)g(x)$ $\forall x \in X$, then $fg \in C(X)$
- $1(x) = 1$
- $f(\lambda g) = \lambda (fg)$  $\forall \lambda \in \mathbb{K}$

Then $C(X)$ **unital associative commutative ring** (which is also a vector space, thus an **algebra**)

## Closure of Subalgebra

>[!Claim]
Let $A \subseteq C(X)$ be a subalgebra. Then $\overline{A}$ is still an algebra.
##### Proof
Of course here we are taking the closure with respect to the same topology/norm as $C(X)$.
Take $f,g \in \overline{A}$. Then by definition of closure, there exist sequences $(f_n),(g_n) \subseteq A$ such that $f_n \to f$ and $g_n \to g$.
Since $A$ is a subalgebra, for every $n$: $f_n + g_n \in A$, $\lambda f_n \in A$, and $f_ng_n \in A$.
Then by continuity of algebra operations:
- $f_n + g_n \to f+g \in \overline{A}$
- $\lambda f_n \to \lambda f \in \overline{A}$
- $f_ng_n \to fg \in \overline{A}$
Hence $\overline{A}$ is again a subalgebra.
If $A$ is unital, then $1 \in A \subseteq \overline{A}$, so $\overline{A}$ is also unital.      $\square$

# Separating Points

>[!Definition]
>$\mathcal{A}\subseteq C(X)$ is called **separating points** of $X$ if 
>$\forall x,y \in X$ ($x\neq y$), $\exists f \in \mathcal{A}: f(x) \neq f(y)$.

