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