# Definition

>[!Definition]
>Let $X$ be Banach over $\mathbb{C}$.
>Then **general linear group** of $X$ is 
>$$\text{GL}(X) = \{T \in \mathcal{L}(X,X) \:|\: T \text{ is invertible }\}$$

- Since $X$ is Banach, the [[Open Mapping Theorem|Bounded Inverse Theorem]] tells us that $\text{GL}(X)$ is a group under composition of continuous linear maps

# Propositions

>[!Exercise]
>If $\|I - T\|< 1$, then $T$ is invertible with inverse 
>$$T^{-1}= \sum_{k=0}^\infty(I-T)^k$$
>In particular $B(I,1)$ consists of invertible elements.


>[!Proposition]
>Let $X$ be Banach over $\mathbb{C}$. Then 
>1. $\text{GL}(X)$ is an open subset of $\mathcal{L}(X,X)$
>2. The map $\text{GL}(X) \to \text{GL}(X)$ given by $T \mapsto T^{-1}$ is continuous
##### Proof
###### 1.
Let $T_0 \in \text{GL}(X)$. 
We claim that $B\left(T_0, \frac{1}{\|T_0^{-1}\|}\right)\subseteq GL(X)$.
If $\|T_0-T\| < \frac{1}{\|T_0^{-1}\|}$, then
$$\|I - T_0^{-1}T\| = \|T_0^{-1}(T_0-T)\| \leq \|T_0^{-1}\|\|T_0-T\| < 1$$
so $T_0^{-1}T$ is invertible by the exercise above.
So $T$ is invertible (as $GL(X)$ is a group).

###### 2.
$$\|T^{-1}-T_0^{-1}\| = \|T_0^{-1}(T_0-T)T^{-1}\| \leq \|T_0^{-1}\|\|T_0-T\|\|T^{-1}\| \tag{$\ast$}$$
If $\|T-T_0\|\leq \frac{1}{2\|T_0^{-1}\|}$ then 
$$\|I - TT_0^{-1}\| = \|(T_0-T)T_0^{-1}\|\leq \|T_0-T\|\|T_0^{-1}\|\leq\frac{1}{2}<1.$$
So 
$$\begin{align*}
\|T_0T^{-1}\| &= \|(TT_0^{-1})^{-1}\| \\
&= \left\| \sum_{k=0}^\infty (I-TT_0^{-1})\right\| \tag{by exercise}\\
&\leq \sum_{k=0}^\infty \|I - TT_0^{-1}\|^k \\
&\leq \sum_{k=0}^\infty \frac{1}{2^k} = 2
\end{align*}$$
So $\|T^{-1}\|= \|T_0^{-1}(T_0T^{-1})\|\leq 2 \|T_0^{-1}\|$.
Thus $(\ast)$ gives
$$\|T^{-1}-T_0^{-1}\|\leq \|T_0^{-1}\|\|T-T_0\|\:2\|T_0^{-1}\| = 2\|T_0^{-1}\|^2\|T-T_0\|$$
whenever $\|T_0-T\|\leq \frac{1}{2\|T_0^{-1}\|}$.
So $T\to T^{-1}$ is continuous.  $\square$

