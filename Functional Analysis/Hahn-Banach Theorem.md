- A tool that allows us to take a a bounded linear functional from $Y \subsetneq X$ and extend it to the whole of $X$.

# Main Idea

>[!Theorem] Hahn-Banach Theorem
>If $\varphi: Y \to \mathbb{K}$ is a linear functional, then $\exists \bar{\varphi}: X \to \mathbb{K}$ such that:
>1. $\bar{\varphi}\mid_{Y} = \text{id}$
>2. $\|\bar{\varphi}\| = \|\varphi\|$

# Corollary
## Corollary A

>[!Corollary]
>Let $X$ be a normed vector space, and $0 \neq x \in X$. Then there exists $\varphi \in X'$ such that 
>1. $\varphi(x) = \|x\|$ 
>2. $\|\varphi\| = 1$

### Application of Corollary A (Existence of Completion)

>[!Theorem]
>Every normed vector space embeds isometrically into a double dual, $X'' = \mathcal{L}(X',\mathbb{K})$.
##### Proof
Let $\Theta: X \to X''$ is defined naturally as $$\Theta(x)(\varphi) = \varphi(x) \quad\quad \forall x \in X,\:\varphi \in X'$$
###### Linearity
Clearly $\Theta(x) \in (X')^*$ so it is definitely linear
###### Continuity
$|\Theta(x)(\varphi)|= |\varphi(x)| \leq \|\varphi\|\|x\|$.     $\implies \|\Theta(x)\|_{X^*} \leq \|x\|$
###### Isometry
By corollary A, $\forall 0\neq x \in X$, $\exists \varphi_x \in X'$ with $\|\varphi_x\|=1$ and $\varphi_x(x) = \|x\|$ so
$|\Theta(x)(\varphi_x)| = |\varphi_x(x)| = \|x\| = \|x\|\|\varphi_x\|$.     $\implies \|\Theta(x)\|_{X^*}\geq \|x\|$.

Using the inequality from continuity, $\|\Theta(x)\|_{X^*} = \|x\|$
###### Injectivity
$\Theta(x)(\varphi) = 0 \implies \varphi(x) = 0 \implies \|\varphi\| = 0 \implies \|x\|=0 \implies x = 0$.
So $\ker \Theta = \{0\}$. Hence $\Theta$ is injective.  $\square$


>[!Result]
>Every normed vector space has a completion

We just showed that $\Theta:X \to X''$ is an isometric embedding. Define $\hat{X} := \overline{\Theta(x)} \subseteq X''$. Since $X''$ is complete and $\hat{X}$ is closed by definition, then $\hat{X}$ is complete as well. $\square$

## Corollary B

>[!Corollary]
>Let $X$ be a normed vector space, and $Y \subsetneq X$ a subspace. If $\varphi \in Y'$, then there exists $\tilde{\varphi} \in X'$ such that
>1. $\tilde{\varphi}\mid_Y = \text{id}$
>2. $\|\tilde{\varphi}\|_{X'} = \|\varphi\|_{Y'}$

## Corollary C

>[!Corollary]
>Let $X$ be a normed vector space, and $Y \subsetneq X$ a *closed* subspace. For each $x_0 \in X\setminus Y$, there exists $\varphi \in X'$ such that 
>1. $\varphi\mid_Y = 0$
>2. $\varphi(x_0) = \text{dist}(x_0,Y) = \inf_{y \in Y} \|x_0-y\|$



# Sublinearity

>[!Definition]
>Let $X$ be a vector space over $\mathbb{R}$ (*NOT* necessarily a normed space)
>A function $p: X \to \mathbb{R}$ is sublinear if:
>1. $p(x+y) \leq p(x) + p(y)$
>2. $p(\lambda x) = \lambda p(x)$

## Examples

1. If $X$ is a normed vector space, then $p(x) = \|x\|$ is sublinear
2. On $\ell^\infty(\mathbb{R})$, $p(x) = \lim \sup_{n \to \infty} x_n$ is sublinear (not trivial)


# Hahn-Banach Theorem ($\mathbb{R}$-Version)

>[!Theorem]
>Let $X$ be a vector space over $\mathbb{R}$. Let $p:X \to \mathbb{R}$ be a sublinear function.
>Let $Y \subseteq X$, and suppose $\varphi_0 \in Y^*$ satisfying:
>$$\varphi_0(y)\leq p(y) \quad\forall y \in Y$$
>Then $\exists \varphi \in X^*$ such that
>1. $\varphi\mid_Y = \varphi_0$
>2. $\varphi(x) \leq p(x)$    $\forall x \in X$.

- Naturally we need to prove this using induction on $\dim Y$.

>[!Lemma]
>Let $X$ be a vector space over $\mathbb{R}$ and $p:X \to \mathbb{R}$ be sublinear.
>Suppose $X = Y \oplus \mathbb{R}x_0$ and that $\varphi_0 \in Y^*$ satisfying: $$\varphi_0(y) \leq p(y) \quad \forall y \in Y$$
>Then there exists $\varphi \in X^*$ such that 
>1. $\varphi\mid_Y = \varphi_0$
>2. $\varphi(x) \leq p(x)$  $\forall x \in X$
##### Proof

We need $\varphi(y + \lambda x_0) = \varphi_0(y) + \lambda c$  where $c = \varphi(x_0)$ is chosen such that
$$\varphi_0(y) + \lambda c \:\:\leq\:\: p(y+\lambda x_0) \quad\quad \forall y \in Y,\lambda \in \mathbb{R} \tag{$\star$}$$
Hence we just need to show that $c$ exists.

###### $\lambda > 0$
Replace $y$ with $\lambda y$. Then 
$$\begin{align*}
(\star) &\:\:\iff\:\: \varphi_0(\lambda y) + \lambda c \leq p(\lambda y + \lambda x) \\[4pt]
&\:\:\iff\:\: \lambda(\varphi_0(y)+ c) \leq \lambda p(y+x_0) \\[4pt]
&\:\:\iff\:\: c \leq p(y+x_0) - \varphi_0(y)
\end{align*}$$
###### $\lambda < 0$
$$\begin{align*}
(\star) &\:\:\iff\:\: \varphi_0(\lambda y) + \lambda c \leq p(\lambda y + \lambda x) \\[4pt]
&\:\:\iff\:\: \lambda(\varphi_0(y)+ c) \leq -\lambda p(-y-x_0) \\[4pt]
&\:\:\iff\:\: \varphi_0(y)+ c \geq -p(-y-x_0)\\[4pt]
&\:\:\iff\:\: c \geq -p(-y-x_0) - \varphi_0(y)
\end{align*}$$
###### $\lambda = 0$
Then $(\star)$ is true by the hypothesis.

-> We need to show now that $c \in \mathbb{R}$ with $$-p(-y_1-x_0)-\varphi_0(y_1) \leq c\leq p(y_2+x_0)-\varphi_0(y_2)\quad\quad \forall y_1,y_2\in Y$$
That is $-p(-y_1-x_0)-\varphi_0(y_1)\leq p(y_2+x_0)- \varphi_0(y_2)$
$\implies \varphi_0(y_2) - \varphi_0(y_1)\leq p(y_2+x_0) + p(-y-x_0)$
$\implies \varphi_0(y_2-y_1)\leq p(y_2+x_0)+ p(-y_1-x_0)$. (We need to show this)

But recall that $\varphi_0(y_2-y_1)\leq p(y_2-y_1) = p(y_2+x_0 + (-y-x_0)) \leq p(y_2+x_0) + p(-y_1-x_0)$
as required. 
Thus setting $$\begin{align*}
a &= \sup_{y\in Y} (-p(-y-x_0)- \varphi_0(y))\\[5pt]
b &= \inf_{y \in Y} (p(y+x_0) - \varphi_0(y))
\end{align*}$$
Then $a \leq b$ which we showed before, and choosing any $c \in [a,b]$ will be sufficient. $\square$



- Now to apply this lemma for induction, we need to apply this step possibly uncountably many times
  **Solutions:** Transfinite induction, or [[Zorn's Lemma]]
