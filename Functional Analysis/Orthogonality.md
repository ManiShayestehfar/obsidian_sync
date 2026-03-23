
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

## Existence and Uniqueness of Projector

>[!Theorem]
>Let $(\mathcal{H}, \langle-,-\rangle)$ be a Hilbert space, and let $M\subseteq X$ (closed + convex).
>Let $x \in \mathcal{H}$. Then $\exists ! \:P_Mx \in M$ such that $$\|x - P_Mx\| = \text{dist}(x,M) = \inf_{m \in M} \|x-m\|$$
##### Proof
Let $d = \text{dist}(x,M)$.
For $k\geq 1$, choose $m_k \in M$ with $d^2 \leq \|x-m_k\|^2 \leq d^2 + \frac{1}{k}$.
For $k,l \geq 1$, we have$$\begin{align*}
\|m_k - m_l\|^2 &= \|(m_k-x)- (m_l-x)\|^2 \\[3pt]
\overset{P.I}{=} 2\|m\|
\end{align*}$$

### Non-example
![[Screenshot 2026-03-23 at 2.15.23 pm.png|300]]
$(\mathbb{R}^2, \|\cdot\|_1)$ (not a Hilbert space).
$M = \{(t,1-t)\:|\: t \in [0,1]\}$ (convex + closed). 
Let $x = (0,0)$. Then $$\|x-m\|_1 = \|(t,1-t)\|_1 = |t|+|1-t|= 1\qquad \forall m \in M$$
but every point on $M$ attains this distance and so $P_M$ is not unique.

