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
>Let $X$ be a vector space over $\mathbb{\R}$. Let $p:X \to \mathbb{R}$ be a sublinear function.