# Definition

>[!Definition] Hilbert Space
>A **Hilbert Space** is a *complete*, *inner product* space (with induced norm)

## Examples

1. $\mathbb{R}^N$ with $\langle x,y\rangle= x \cdot y$
2. $\mathbb{C}^N$ with $\langle x,y \rangle = x \cdot \overline{y}$
3. $\ell^2$ with $\langle x,y \rangle = \sum_{k=1}^\infty x_k\overline{y}_k$
4. $L^2([a,b])$ with $\langle f,g \rangle = \int_a^b f(x) \overline{g(x)}\:dx$

### Non-Examples
1. $\ell^p$ for $p\neq 2$
   For $p = \infty$, take $x = (1,0,0,...)$, $y=(1,1,0,0,...)$
   $5= 4+1 = \|x+y\|^2_\infty + \|x-y\|^2_\infty \neq 2(\|x\|^2_\infty + \|y\|^2_\infty) = 4$ 
2. $L^p([a,b])$ for $p\neq 2$
3. $(C([a,b]), \|\cdot\|_\infty)$ 



# Parallelogram Identity

>[!Definition] 
>In an inner product space $$\|x+y\|^2 + \|x-y\|^2 = 2(\|x\|^2 + \|y\|^2)\qquad \forall x,y \in X$$


# Banach Space Criteria

>[!Theorem]
>A Banach space $(X, \|\cdot\|)$ is a Hilbert space $\iff$ the Parallelogram identity holds



# Orthonormal System

## Definition

>[!Definition] 
>Let $\mathcal{H}$ be a Hilbert space over $\mathbb{K}$. A set $S \subseteq \mathcal{H}$ is an **orthonormal system** if $$\langle e, e' \rangle=\begin{cases}
 1 & e' = e \\ 0 & e' \neq e
\end{cases}$$
for all $e,e' \in S$.

>[!Definition] 
>An orthonormal system $S$ is **complete** if $\overline{\text{Span}(S)} = \mathcal{H}$. 
>A complete orthonormal system is called a **Hilbert/orthonormal basis**.

### Examples
1. $\mathcal{H}= \mathbb{C}^N$, where $\langle x,y \rangle =\sum_{i=1}^N x_i \bar{y_i}$.
   Then clearly $S := \{e_i \:|\: 1 \leq i \leq N\}$ where $e_i = (0,0,...,1,...,0)$ is a basis and $\text{Span}(S) = \mathbb{C}^N$.

2. $\mathcal{H} = \ell^2(\mathbb{K})$. Then the  set $S := \{e_n \:|\: n \geq 1\}$ is orthonormal.
   Also $\text{Span}(S) = \{\text{finitely supported sequences}\}$ which we proved to be dense in $\ell^2$. Hence $S$ is a Hilbert basis

3. $\mathcal{H}= L_\mathbb{C}^2([0,2\pi])$. Then the set $S = \{\tfrac{1}{\sqrt{2\pi}}e^{int} \:|\: n \in \mathbb{Z}\}$ is orthonormal. Let $e_n(t) = \frac{1}{\sqrt{2\pi}}e^{int}$. Then 
   $$\begin{align*}
\langle e_m , e_n \rangle &= \int_0^{2\pi} e_m(t) \overline{e_n(t)}\:dt \\
&= \frac{1}{2\pi}\int_0^{2\pi}e^{i(m-n)t}\:dt \\[3pt]
&= \begin{cases}
1 & m=n  \\
0 & m \neq n
\end{cases}
\end{align*}$$
	to show that $\overline{\text{Span}(S)}= L_\mathbb{C}^2 ([0,2\pi])$ we need Stone-Weierstrass.


# General Fourier Series
Fourier series can be generalised to arbitrary Hilbert spaces with arbitrary Hilbert bases.

## Finite Dimensional Hilbert Spaces

Let $S = \{e_1,...,e_n\}$ be a Hilbert basis of $\mathcal{H}$. 

>[!Theorem]
>For $x \in \mathcal{H}$,
>1. **Fourier Series:** $x = \sum_{j=1}^n \langle x,e_j \rangle e_j$ 
>2. **Parseval's Identity:** $\|x\|^2 = \sum_{j=1}^n |\langle x,e_j \rangle |^2$ 
>If $S' \subseteq S$ and $M = \text{Span}(S')$, then
>3. **Projection Formula:** $P_M x = \sum_{e \in S'} \langle x,e \rangle e$
>4. **Bessel's Inequality:** $\|x\|^2 \geq \sum_{e \in S'} |\langle x,e \rangle|^2$
##### Proofs
###### Fourier Series
Let $x \in \mathcal{H}$. Since $S$ is a basis, there exist unique $\alpha_1,...,\alpha_n \in \mathbb{K}$ such that $x = \sum_{j=1}^n \alpha_j e_j$.
Fix $k \in \{1,...,n\}$. Taking inner products with $e_k$, we get $$\langle x, e_k \rangle = \sum_{j=1}^n \alpha_j \langle e_j, e_k \rangle = \alpha_k$$
Now substituting this back to the basis expansion of $x$ gives $$x = \sum_{j=1}^n \langle x, e_j \rangle e_j\qquad \square$$
###### Parseval's Identity

Using the Fourier series, write $$\begin{align*}
\|x\|^2 = \langle x,x \rangle = \left \langle \sum_{j=1}^n \langle x,e_j \rangle e_j\:,\: \sum_{j=1}^n\langle x,e_j \rangle e_j \right \rangle &= \sum_{j=1}^n \sum_{k=1}^n \langle x,e_j \rangle \overline{\langle x,e_k \rangle} \langle e_j, e_k \rangle \\[3pt]
&=  \sum_{j=1}^n \langle x, e_j \rangle \overline{\langle x, e_j \rangle} \\
&= \sum_{j=1}^n |\langle x,e_j \rangle|^2  \qquad \square
\end{align*}$$
###### Projection Formula

Let $m := \sum_{e \in S'} \langle x,e \rangle e \in M$ since $m$ is a finite linear combination of vectors in $S$'.
We show that $x-m \in M^\perp$. Since $S'$ spans $M$, it is enough to show $$\langle x-m , e_0 \rangle=0\quad\forall e_0 \in S'.$$
Fix $e_0 \in S'$. Then $$\langle x-m, e_0 \rangle = \left \langle x- \sum_{e \in S'} \langle x, e \rangle e, e_0 \right \rangle = \langle x, e_0 \rangle - \sum_{e \in S'} \langle x,e \rangle \langle e, e_0 \rangle.$$
Because $S' \subseteq S$ and $S$ is orthonormal, $\langle e,e_0 \rangle = 1 \iff e = e_0$. Then $$\langle x-m, e_0 \rangle= \langle x,e_0\rangle - \langle x,e_0 \rangle = 0.$$
So $x-m$ is orthogonal to every vector in $S'$, hence $x-m \in M^\perp$, and so by the defining property of $P_M x$, the projection formula holds. $\square$  

###### Bessel's Inequality

By the Projection formula, $m := P_Mx = \sum_{e \in S'} \langle x,e \rangle e$.
Since $x-m \in M^\perp$ and $m \in M$, we have $x = \underbrace{m}_{M} + \underbrace{(x-m)}_{M^\perp}$ .
Then by Pythagoras' Theorem, $\|x\|^2 = \|m\|^2 + \|x-m\|^2 \geq \|m\|^2$.
Now since vectors in $S'$ are orthonormal, 
$$\|m\|^2 = \left\| \sum_{e \in S'} \langle x,e \rangle e \right\| = \sum_{e \in S'} |\langle x,e \rangle|^2$$
by Parseval's identity. Therefore 
$$\|x\|^2 \geq \sum_{e \in S'} |\langle x,e \rangle|^2\qquad \square$$

## General Hilbert Spaces

*Issue:* $S$ may be uncountable

### Lemmas & Corollaries

>[!Lemma] Lemma 1
>Let $\mathcal{H}$ be a Hilbert space. 
>1. If $x_n \to x$ in $\mathcal{H}$, then $\langle x,y \rangle = \lim_{n \to \infty} \langle x_n, y \rangle \qquad \forall y \in \mathcal{H}$ 
>2. If $(x_n)$ is such that $s = \sum_{n=1}^\infty x_n$ converges in $\mathcal{H}$, then $\langle s,y \rangle = \sum_{n=1}^\infty \langle x_n, y \rangle \qquad \forall y \in \mathcal{H}$
>3. If $\{e_n \: |\: n \geq 1\}$ is orthonormal, then $$\sum_{n=1}^\infty \alpha_ne_n \text{ converges in } \mathcal{H} \iff \sum_{n=1}^\infty |\alpha_n|^2 \text{ converges in } \mathbb{R}$$
>   moreover if $\sum|\alpha_n|^2$ converges, then $\left\| \sum_{n=1}^\infty \alpha_n e_n \right\|^2 = \sum_{n=1}^\infty |\alpha_n|^2$
##### Proofs
NEED TO PROVE


>[!Lemma] Lemma 2
> If $\{e_1,...,e_n \}$ is orthonormal, then $$\sum_{j=1}^n |\langle x, e_j \rangle|^2 \leq \|x\|^2 \qquad x \in \mathcal{H}$$
##### Proof
Let $y = \sum_{j=1}^n \langle x,e_j \rangle e_j$. By Pythagoras', $\|y\|^2 = \sum_{j=1}^n |\langle x,e_j \rangle|^2$. 
But then 
$$\begin{align*}
\langle x-y,y \rangle &= \langle x,y \rangle - \langle y,y\rangle \\
&= \left\langle x, \sum_{j=1}^n \langle x,e_j\rangle e_j \right\rangle - \|y\|^2 \\
&= \sum_{j=1}^n \overline{\langle x,e_j \rangle} \langle x,e_j \rangle - \|y\|^2 \\
&= \|y\|^2 - \|y\|^2 = 0
\end{align*}$$
Hence $\|x\|^2 = \|y\|^2 + \|x-y\|^2 \geq \|y\|^2$ by Pythagoras' theorem. $\square$


>[!Corollary] Corollary 1
>If $S \subseteq \mathcal{H}$ is orthonormal, then for each $x \in \mathcal{H}$, the set $\{e \in S \:|\: \langle x,e \rangle\neq 0\}$ is countable.
##### Proof
Let $k \geq 1$. If $e_1,...,e_N \in S$ with $|\langle x,e_j \rangle| > \frac{1}{k}$ for $j =1,...,N$, then $|\langle kx, e_j \rangle|>1$ and so by Lemma 2: 
$$N < \sum_{j=1}^N |\langle kx, e_j \rangle|^2 \leq \|kx\|^2$$
and so $N < k^2 \|x\|^2$. Thus the set $\{e \in S \: | \: |\langle x,e \rangle|> \frac{1}{k} \}$ is *finite* for each fixed $x$, and each $k \geq 1$.
So 
$$\{e \in S \:|\:  \langle x,e \rangle \neq 0\} = \bigcup_{k\geq 1} \{e \in S \:|\: |\langle x,e \rangle|>\frac{1}{k}\}$$
is a countable union of finite sets, and hence is countable. $\square$


### Bessel's Inequality

>[!Theorem]
>If $S \subseteq \mathcal{H}$ is orthonormal, then 
>$$\sum_{e\in S} |\langle x,e\rangle|^2 \leq \|x\|^2.$$
>This is a *countable* sum of nonnegative terms, and so can be taken in any order.
##### Proof
By Corollary 1, we enumerate $\{e \in S \: |\: \langle x,e \rangle \neq 0\} = \{e_1,e_2,...\}$
and by Lemma 2, 
$$\sum_{j=1}^N |\langle x,e_j \rangle|^2 \leq \|x\|^2 \qquad \forall N \geq 1$$
and use monotone convergence. $\square$

### Projection Formula

>[!Theorem] 
>Let $S \subseteq \mathcal{H}$ be orthonormal. let $M = \overline{\text{Span}(S)}$. Then
>$$P_Mx = \sum_{e \in S} \langle x,e \rangle e$$
>where the *countable* sum can be taken in any order.
##### Proof
Same proof as before, except for countable sum instead of finite.

### Fourier + Parseval

> [!Theorem] 
> Let $S$ be orthonormal in $\mathcal{H}$. The following are equivalent:
> 1. $S$ is complete (i.e. a Hilbert basis)
> 2. $x = \sum_{e \in S} \langle x,e \rangle e \qquad \forall x \in \mathcal{H}\:\:\text{ (Fourier Series) }$
> 3. $\|x\|^2 = \sum_{e \in S} | \langle x,e \rangle|^2 \qquad \forall x \in \mathcal{H} \:\: \text{ (Parseval's Identity) }$
>    
> In (2,3), the *countable* sum can be taken in any order.
##### Proof
###### 1 -> 2
Since $S$ is complete, $M = \overline{\text{Span}(S)}= \mathcal{H}$, so $P_Mx =x$ for all $x \in \mathcal{H}$.
and so $x = \sum_{e \in S} \langle x,e \rangle e$ by the projection formula.

###### 2 -> 3 
Directly just Lemma 1 (??)

###### 3 -> 1
Suppose $\|x\|^2 = \sum_{e \in S} |\langle x,e\rangle|^2$ for all $x \in \mathcal{H}$. Let $M = \overline{\text{Span}(S)}$. 
Let $z \in M^\perp$. Then $z = 0 + z \in M \oplus M^\perp$, hence $P_M z = 0$.
Thus
$$\begin{align*}
0 = \|P_Mz\|^2 &= \|\sum_{e \in S} \langle z,e \rangle e\|^2 \tag{Projection formula} \\
&= \sum_{e \in S} |\langle z,e \rangle|^2 \\[2pt]
&= \|z\|^2 \tag{Parseval's Identity}
\end{align*}$$
$\square$


# Separability

## Definition

>[!Definition]
>Let $(X,d)$ be a metric space. Then $X$ is **separable** $X$ contains at most countable subsets $S \subseteq X$ such that $\overline{S}= X$.

## Examples

1. $(\mathbb{K}^N, \|\cdot\|)$ is separable if 
   $$S = \begin{cases}
\mathbb{Q}^N & \mathbb{K} = \mathbb{R}  \\[2pt]
\mathbb{Q} + i \mathbb{Q} & \mathbb{K} = \mathbb{C}
\end{cases}$$
2. $\ell^2(\mathbb{K})$ is separable. Take $\{e_n\}_{n \in \mathbb{N}}$ to be the standard orthonormal basis in $\ell^2$. Then every $x \in \ell^2$ is the limit of its finite partial sums $x^{(N)} = \sum_{n=1}^N x_n e_n$. Hence the set we need is 
   $$S = \left\{\sum_{n=1}^N x_ne_n \::\:N \in \mathbb{N},\: x_n \in \mathbb{Q}, \mathbb{Q} + i \mathbb{Q}\right\}$$
   $S$ is countable, and it is also dense since we can truncate any $x$ to finitely many coordinates and approximate those coordinates with rationals.

*Non-example:* $(\ell^\infty, \|\cdot\|_\infty)$ is a non-separable Banach space.
It is sufficient to find $S \subseteq X$ such that:
4. $|S| > |N|$
5. $\exists \varepsilon >0$ such that $\forall x_1,x_2 \in S$, $\|x_1-x_2\|_\infty \geq \varepsilon$ 

In the case for $\ell^\infty$, take $S = \{x_A \:|\: A \subseteq \mathbb{N}\}\subseteq \ell^\infty$ 
$\implies |S| = |2^\mathbb{N}| = |\mathbb{R}|$.

Claim: For any $A,B \subseteq \mathbb{N}$ and $A \neq B$, $\|x_A - x_B\|_\infty = 1$


## Separability and Hilbert Basis

>[!Theorem]
>Let $\mathcal{H}$ be a Hilbert space over $\mathbb{K}$. Then 
>$$\mathcal{H} \text{ is separable } \iff \mathcal{H}\:\: \substack{\large\text{contains at most countable} \\ \large \text{complete orthonormal set} \\ \large\text{(i.e. Hilbert basis)}} $$
>Moreover if $\mathcal{H}$ is separable, then $H$ is isometrically isomorphick to $\ell^2(\mathbb{K})$
>


