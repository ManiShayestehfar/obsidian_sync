# Definition

>[!Definition]
>Let $X$ be a normed vector space. Then its **Dual** is defined as:
>$X' := \mathcal{L}(X, \mathbb{K})$, also
>$X^* := \text{Hom}(X, \mathbb{K})$

## Example

>[!Example]
>If $\dim X < \infty$, then $X^* = X'$.
##### Proof
Take $\varphi \in X^*$. Let $e_1,e_2,...,e_n$ be a basis for $X$. Then $\varphi\left(\sum_{i=1}^n x_ie_i\right)= \sum_{i=1}^nx_i \varphi(e_i)$
We know that $$\|\varphi(x)\| = \left|\sum_{i=1}^n x\varphi(e_i)\right|\leq \sum_{i=1}^n|x_i|\cdot \underbrace{\max_{1\leq i\leq n} |\varphi(e_i)|}_{=:M} = M \sum_{i=1}^n|x_i| \leq MC\|x\|$$
by equivalence of norms on $\mathbb{K}^n$ since $\left\|\sum_{i=1}^n x_ie_i\right\| := \sum_{i=1}^n|x_i|$ is a norm on $X$.  
$\therefore \varphi \in X'$.

The other direction is obvious.

Also, take $\varphi(x) = \varphi_a(x)= \sum_{i}x_ia_i \:\:(=a\cdot x)$  where $a = (\varphi(e_1),...,\varphi(e_n))$.
The map $X'\to \mathbb{K}^n$ for $n$-dimensional $X'$ given by $\varphi_a \mapsto a$ is an isomorphism (but NOT an isometry).
So $X' \simeq X^*$.

### Remark

>[!Remark] 
>If $\dim X = \infty$, then $X' \subsetneq X^*$

As an example, take $(C([0,1]), \|\cdot\|_1)$ which is NOT Banach and consider $\varphi \in X^*$ given by $\varphi(f) = f(1)$.
Let $f_n := nx^{n-1}$. Then $\|f\|_1 = \int_0^1 |f_n(x)|\:dx = \int_0^1 nx^{n-1}\:dx = 1$. 
But $\varphi(f_n) = f_n(1) = n$. 
Hence $|\varphi(f_n)| \geq n \cdot \|f_n\|_1 \implies \varphi \not\in X'$.   $\square$


# Isometric Isomorphism of $\ell^p$ Spaces and Duals

>[!Theorem]
>Let $1<p<\infty$ and $1<q<\infty$ such that $\tfrac{1}{p}+ \tfrac{1}{q}=1$. 
>Then $(\ell^p)' \simeq \ell^q$ (isometric isomorphism)

#### Proof

We need to construct a $\Theta: \ell^a \to (\ell^p)'$ via $y \mapsto \varphi_y$ where $\varphi_y: \ell^p \to \mathbb{K}$ and show that $\Theta$ is an isometric isomorphism.

Consider $\Theta(y,x) := \varphi_y(x)$ and so we can instead consider $\Theta: \ell^q\times \ell^p \to \mathbb{K}$ which is bilinear.
The best natural choice for $\varphi_y$ is the "dot product": $\varphi_y(x) = \sum_{i=1}^\infty x_iy_i$ 
##### 1. Well-Defined
By Holder's inequality: $\sum_{k=1}^\infty |x_ky_k| \leq \|x\|_p\|y\|_q$ so the series converges and so $\Theta$ is well-defined.

But $\Theta$ should be continuous as well. Take $\varphi_y \in (\ell^p)'$ for each $y \in \ell^q$. 
Clearly $\varphi_y \in (\ell^p)^*$, so $|\varphi_y(x)|\leq\|y\|_q\|x\|_p \implies |\varphi_y(x)|\leq \|y\|_q$ so $\Theta$ is continuous.

##### 2. Injective
If $\Theta(y) = \Theta(y')$ then $\varphi_y(x) = \varphi_{y'}(x)$ for all $x \in \ell^p$.
But $\sum_{i=1}^\infty y_ix_i = \sum_{i=1}^\infty y_i'x_i \iff \sum_{i=1}^\infty (y_i-y_i')x_i = 0 \iff y_i = y_i' \quad \forall i$ .
So $y=y'$ and therefore $\Theta$ is injective.

##### 3. Surjective
We need to prove: $\forall \varphi \in (\ell^p)', \exists y \in \ell^q$ such that $\varphi = \varphi_y$.
Notice that for the natural basis vector $e_i$, $\varphi(e_i) = \varphi_y(e_i) = y_i$. 
It remains to prove two things:

###### $\varphi_y = \varphi$
Assume $y_0 = (\varphi(e_i))_{i=1}^\infty \in \ell^q$. i.e. $y_i = \varphi(e_i)$.
Then $\forall x \in \ell^p$ $$\begin{align*}
\varphi_{y_0}(x) &= \sum_{i=1}^\infty x_iy_i \\
&= \sum_{i=1}^\infty x_i \varphi(e_i) \\
&= \lim_{N\to \infty}\left(\sum_{i=1}^N x_i \varphi(e_i)\right) \\\\
&= \lim_{N\to \infty}\varphi\left(\sum_{i=1}^N x_i e_i\right) \\
&= \varphi\left(\lim_{N\to \infty}\sum_{i=1}^N x_i e_i\right) \:=\: \varphi(x)
\end{align*}$$
where the last step was valid due to continuity of $\varphi$.
###### $y_0 = (\varphi(e_i))_{i=1}^\infty \in \ell^q$
We know $y_i = \varphi(e_i)$ so $y_0 = (y_i)_{i=1}^\infty$. 
Let $$x^{(n)}_k := \begin{cases}
\frac{|y_k|^q}{y_k} & k\leq n \text{ and } y_k\neq0  \\
0 & k > n \text{ or } y_k = 0
\end{cases}$$
Then $\varphi(x^{(n)})$







##### 4. Isometry

##### 5. Linearity
Obvious since $\varphi_y$ is linear itself.
