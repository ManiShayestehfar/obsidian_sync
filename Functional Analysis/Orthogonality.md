
# Definition

>[!Definition] Orthogonality
>$X$ a vector space with $\langle-,-\rangle$. Say $x,y$ are orthogonal, i.e. $x \perp y$ if $\langle x,y \rangle= 0$.

## Pythagoras' Theorem

>[!Proposition] Pythagoras
>If $x_1,...,x_n$ are mutually orthogonal. i.e. $\langle x_i, x_j \rangle= 0$ for $i \neq j$. Then $$\|x_1+\cdots + x_n\|^2 = \|x_1\|^2 + \cdots \|x_n\|^2$$


# Convex

>[!Definition]
>A subset $M$ of a vector space over $\mathbb{K}$ is **convex** if: $$x,y \in M \implies (1-t)x+ty \in M\qquad t \in [0,1]$$


# Orthogonal Projectors

>[!Definition]
>$P_Mx$ is called the **projection** of $x$ onto $M$

>[!Theorem]
>Let $(\mathcal{H}, \langle-,-\rangle)$ be a Hilbert space, and let $M$