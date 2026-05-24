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


# Topological vector spaces over $\mathbb{R}$

> [!Definition] Topological vector space
> A topological vector space over $\mathbb{R}$ is a real vector space $X$ equipped with a topology such that the two maps $X \times X \to X$, $(x,y) \mapsto x+y$, and $\mathbb{R} \times X \to X$, $(t,x) \mapsto tx$, are continuous.

- Thus the topology and the linear structure are compatible. Normed spaces are examples, but many important topological vector spaces are *not* *normable*.

## Hausdorf 

> [!Definition] Hausdorff topological vector space
> A topological vector space $X$ is Hausdorff if for any two distinct points $x,y \in X$, there exist disjoint open sets $U,V \subseteq X$ such that $x \in U$ and $y \in V$.
>
> Equivalently, in a topological vector space, $X$ is Hausdorff if and only if $\{0\}$ is closed.

## Convex Set

> [!Definition] Convex set
> A subset $C \subseteq X$ is convex if for every $x,y \in C$ and every $t \in [0,1]$, $tx + (1-t)y \in C$.

## Locally Convex Topological Vector Space

> [!Definition] Locally convex topological vector space
> A Hausdorff topological vector space $X$ over $\mathbb{R}$ is called locally convex if there is a neighbourhood basis of $0$ consisting of convex sets.
>
> Equivalently, for every neighbourhood $U$ of $0$, there exists a convex neighbourhood $V$ of $0$ such that $0 \in V \subseteq U$.

### Examples

1. Every normed vector space is locally convex: the open balls around $0$ are convex.
2. If $X$ is compact Hausdorff, then $C(X)$ with the supremum norm is locally convex. Its dual space $C(X)^*$, equipped with the weak-* topology, is also locally convex.


## Extreme points and faces

> [!Definition] Extreme point
> Let $K \subseteq X$ be convex. A point $x \in K$ is called an extreme point of $K$ if whenever $x = ty + (1-t)z$ with $y,z \in K$ and $0 < t < 1$, then $y = z = x$.
>
> The set of extreme points of $K$ is denoted by $\operatorname{Ext}(K)$.

> [!Definition] Face
> Let $K \subseteq X$ be convex. A convex subset $F \subseteq K$ is called a face of $K$ if whenever $tx + (1-t)y \in F$, $x,y \in K$, and $0 < t < 1$, then $x,y \in F$.
>
> Singleton faces are precisely extreme points: $x \in \operatorname{Ext}(K)$ if and only if $\{x\}$ is a face of $K$.

> [!Definition] Convex hull
> For $A \subseteq X$, the convex hull of $A$ is
>
> $$\operatorname{co}(A)=\left\{\sum_{j=1}^n t_j a_j : n \in \mathbb{N},\ a_j \in A,\ t_j \geq 0,\ \sum_{j=1}^n t_j = 1\right\}.$$
>
> The closed convex hull is denoted by $\overline{\operatorname{co}}(A)$.
