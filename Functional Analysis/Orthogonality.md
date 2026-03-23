
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
&\overset{P.I}{=} 2\|m_k-x\|^2 + 2\|m_l - x\|^2 - \|m_k-x+m_l-x\|^2 \\[3pt]
&= 2\|m_k-x\|^2 + 2\|m_l - x\|^2 - 4 \left\|\frac{m_k+m_l}{2}-x\right\|
\end{align*}$$
Since $\frac{m_k + m_l}{2}\in M$ (by convexity), we have $$\begin{align*}
\|m_k - m_l\|^2 &\leq 2\|m_k-x\|^2 + 2\|m_l - 4d^2\\[3pt]
&\leq 2\left(d^2 + \frac{1}{k}\right) + 2\left(d^2 + \frac{1}{l}\right)  - 4 d^2 \\[3pt]
&= 2 \left(\frac{1}{k} + \frac{1}{l}\right)
\end{align*}$$
Thus, $(m_k)_{k\geq 1}$ is Cauchy. So $(m_k)$ converges in $\mathcal{H}$ (as it is complete).
Define $\|x- P_Mx\| = \lim_{k \to \infty} \|x - m_k\|= d$.
If $m \in M$ satisfies $\|x-m\|=d$, then 
$$\begin{align*}
\|P_Mx - m\|^2 &= \|(P_Mx -x) - (m-x)\|^2 \\[3pt]
&\overset{P.I}{=} 2\|P_Mx - x\|^2 + 2\|m - x\|^2 - \|P_Mx -x + m-x\|^2 \\[3pt]
&= 2d^2 + 2d^2 - 4 \left\|\underbrace{\frac{P_Mx + m}{2}}_{\in M} - x\right\| \\[3pt]
&\leq 2d^2 +2d^2 - 4d^2 = 0
\end{align*}$$
Therefore, $P_Mx = m$ and we have uniqueness. $\square$.

### Non-example
![[Screenshot 2026-03-23 at 2.15.23 pm.png|300]]
$(\mathbb{R}^2, \|\cdot\|_1)$ (not a Hilbert space).
$M = \{(t,1-t)\:|\: t \in [0,1]\}$ (convex + closed). 
Let $x = (0,0)$. Then $$\|x-m\|_1 = \|(t,1-t)\|_1 = |t|+|1-t|= 1\qquad \forall m \in M$$
but every point on $M$ attains this distance and so $P_M$ is not unique.


## Orthogonal Complement

>[!Definition]
>Let $M \subset \mathcal{H}$, then the **orthogonal complement** of $M$ is $$M^{\perp} = \{x \in \mathcal{H} \:|\: \langle x,m \rangle = 0\quad \forall m \in M\}$$

- $M^\perp \subseteq \mathcal{H}$ is closed


## Orthogonal Decomposition

>[!Theorem]
>Let $M \subseteq \mathcal{H}$ be a *closed* subspace of a Hilbert space $\mathcal{H}$. Then $$\mathcal{H}= M \oplus M^{\perp}$$
##### Proof

- It is easy to check that $\mathcal{M}^\perp$ is a subspace
- We are required to prove that each $x \in \mathcal{H}$ can be written in exactly one way as $x = m + m'$.

###### Uniqueness
If $x = m_1 + m_1'=m_2 + m_2'$, then $M \ni m_1-m_2 = (x-m_1^\perp) - (x-m_2^\perp) = m_2^\perp - m_1^\perp \in M^\perp$ .
So $\|m_1-m_2\|^2 = \langle \underbrace{m_1-m_2}_{\in M}, \underbrace{m_1-m_2}_{\in M'} \rangle = 0$ and so $m_1=m_2$ and $m_1^\perp = m_2^\perp$.

###### Existence
$$x = \underbrace{P_Mx}_{\in M} + (\underbrace{x- P_Mx}_{\in M^\perp})$$

![[Screenshot 2026-03-23 at 4.04.59 pm.png|200]]
So we only need to prove that $x - P_Mx \in M^\perp$.

Let $m \in M$. Need to show $\langle x-P_Mx,m \rangle=0$.
If $m =0$ we are done. So assume $m \neq 0$. By rescaling assume $\|m\|=1$.
$$\begin{align*}
x-P_Mx &= x - (\overbrace{P_Mx + \langle x- P_Mx,m\rangle}^{m_1:=}m ) + \langle x- P_Mx,m\rangle m \\[3pt]
&= x-m_1 + \langle x-P_M x\rangle m 
\end{align*}$$
Consider 
$$\begin{align*}
\langle x-m_1, m \rangle &= \langle x,m \rangle - \langle P_Mx + \langle x- P_Mx,m\rangle m,m \rangle \\[3pt]
&= \langle x,m \rangle - \langle P_M x,m \rangle - \langle x - P_M x,m \rangle \underbrace{\langle m,m \rangle}_{=1} \\[3pt]
&= \langle x,m \rangle - \langle P_M x,m \rangle - \langle x,m \rangle + \langle P_m x, m \rangle \\
&= 0
\end{align*}$$
Hence $x-m_1 \perp m$.
By Pythagoras, $$\begin{align*}
\|x-P_M x\|^2 &= \|x-m_1\|^2 + \| \langle x-P_Mx,m \rangle m\|^2 \\[4pt]
&\geq \|x - P_Mx\|^2 + |\langle x-P_Mx,m \rangle |^2
\end{align*}
$$
where we get the last line by considering that:
- $\| \langle x-P_Mx,m \rangle m\|^2 =  |\langle x-P_Mx,m \rangle |^2 \|m\|^2 = |\langle x-P_Mx,m \rangle |^2$,
- $\|x-m_1\|^2 = \|x - P_Mx\|^2 + |\langle x-P_Mx,m \rangle |^2 \|m\|^2 \geq \|x - P_Mx\|^2$ 

Hence $\langle x-P_Mx,m \rangle = 0$ as required. $\square$

