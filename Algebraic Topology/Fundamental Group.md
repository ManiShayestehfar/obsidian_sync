
# Definition

>[!def] Fundamental group
>The **fundamental group** $\pi_1(X,x_0)$ of $X$ based at base point $x_0$ is the set of all homotopy classes $[f]$ of loops $f:I \to X$ based at $x_0$.

##### Proof: Group properties

*Well-definedness:* If $f_0\simeq f_1$ , $g_0\simeq g_1$ then $f_0 \circ g_0 = f_1 \circ g_1$. Also composing two paths gives a paths so we have closure.

*Associativity:* 
$$\begin{align*}
([f][g])[h] &= [f \cdot g][h] \\
&= [(f \cdot g) \cdot h] \\
&= [f \cdot (g \cdot h)] \\
&= [f][g \cdot h] \\
&= [f]([g][h])
\end{align*}$$
*Identity:* Let $c_0 : I \to X$ be the constant path at $x_0$. Then
$$\begin{align*}
[c_0][f] &= [c_0 \cdot f] = [f] \\
[f][c_0] &= [f \cdot c_0] = [f]
\end{align*}$$
and so $c_0$ is the identity element. 


## Examples

1. $X = \mathbb{R}^n$, $x_0 \in \mathbb{R}^n$, then $\pi_1(X,x_0) \cong 1$ as every loop in $\mathbb{R}^n$ is straight-line homotopic to the constant path.
2. Same for any convex subset $C \subseteq \mathbb{R}^n$ with $x_0 \in C$
3. $\pi_1(S^1,x_0) \cong \mathbb{Z}$ for all $x \in S^1$
4. $X$ the "figure-8" with $a,b$ loops based at $x_0$, then $\pi_1(X,x_0) = F(a,b)$


# Dependence of Fundamental group on basepoint

$x_0,x_1\in X$. All loops based at $x_0$ lie on the same path-connected component of $X$ as $x_0$. So if $x_0,x_1$ are in different path-connected components, then there is a path $h:I \to X$ from $x_0$ to $x_1$. 
For any loop $f$ based at $x_1$, $h \circ f \circ\bar{h}$ is a loop based at $x_0$.

![[Fundamental Group-1759575687809.png|300]]


>[!proposition] 
>If $x_0,x_1\in X$ are in the same path-connected component of $X$, then $\pi_1(X,x_0) \cong \pi_1(X,x_1)$
##### Proof
$h$ a path from $x_0$ to $x_1$. Define $\beta_h: \pi_1(X,x_0)\to \pi_1(X,x_1)$ by $[f] \mapsto [h \cdot f \cdot \bar{h}]$.

*Well-defined:* If $f_0\simeq f_1$, then $h \cdot f_0 \cdot \bar{h} \simeq h \cdot f_1 \cdot \bar{h}$.
*Homomorphism:* Given loops $f,g$ based at $x_1$, we have 
$$\begin{align*}
\beta_h([f])\beta_h([g]) &= [h \cdot f \cdot\bar{h}][h \cdot g \cdot\bar{h}] \\
&= [h \cdot f \cdot \bar{h} \cdot h \cdot g \cdot \bar{h}] \\
&= [h \cdot f \cdot c_1 \cdot g \cdot \bar{h}] \\
&= [h \cdot f \cdot g \cdot \bar{h}] \\
&= \beta_h([f \cdot g]) \\
&= \beta_h ([f][g])
\end{align*}$$
$\therefore\:\:\beta_h$ is a homomorphism.

*Bijection:* $\beta_{\bar{h}}:\pi_1(X,x_1)\to \pi_1(X,x_0)$ is  the inverse of $\beta_h$ and so $\beta_h$ is bijective.   $\square$


# Simply-Connected

>[!def] Simply-Connected
>For $X$ path-connected, $X$ is **simply-connected** if $X$ is path connected and $\pi_1(X)\cong 1$.



# Fundamental Group of the Circle
$$\pi_1(S^1) \cong \mathbb{Z}$$
For $n \in \mathbb{Z}$, define $w_n: I \to S^1$ by $w_n(s) = (\cos 2\pi ns\:,\:\sin 2\pi ns)$. These are loops in $S^1$ based at $x_0=(1,0)$, wrapping around the circle $n$-times.
Consider $\Phi:\mathbb{Z} \to \pi_1(S^1,x_0)$ given by $\Phi(n) = [w_n]$.

>[!thm]
>$\Phi$ is an isomorphism
##### Proof
Define $p: \mathbb{R} \to S^1$ by $p(s) = (\cos 2\pi s\:,\:\sin 2\pi s)$. Define $\tilde{w}_n: I \to \mathbb{R}$ by $\tilde{w}_n(s)=ns$ where the image of $\tilde{w}_n$ is $[0,n]$ for $n\geq 0$ and $[n,0]$ for $n \leq 0$. Then $p \circ \tilde{w}_n = w_n$.

![[Fundamental Group-1759576652737.png|100]]
Now if $\tilde{f}_n:I\to \mathbb{R}$ is any path from $0$ to $n$ then $\tilde{f}_n \simeq \tilde{w}_n$ by straight-line homotopy. Thus $p \cdot \tilde{f}_n \simeq p \cdot \tilde{w}_n = w_n$. That is, for any path $\tilde{f}_n$ we have $\Phi(n):=[w_n] = [p \cdot \tilde{f}_n]$.

*Showing $\Phi$ is a homomorphism:* Need $\Phi(m+n) = \Phi(m) + \Phi(n)$. i.e. $[w_{m+n}]=[w_m][w_n]$.
Let $\tau_m: \mathbb{R} \to \mathbb{R}$ be translation by $m$, i.e. $\tau_m(x) = x+m$. Then $\tilde{w}_m \cdot(\tau_m \circ \tilde{w}_n) \simeq \tilde{w}_{m+n}$ is a path from $0$ to $m+n$ in $\mathbb{R}$. Hence,
$$\begin{align*}
\Phi(m+n) 
&= [\, \rho \circ \tilde{\omega}_{m+n} \,] \\
&= [\, \rho \circ (\tilde{\omega}_m \cdot (\tau_m \circ \tilde{\omega}_n)) \,] \\
&= [\, (\rho \circ \tilde{\omega}_m) \cdot (\rho \circ \tau_m \circ \tilde{\omega}_n) \,] \\
&= [\, (\rho \circ \tilde{\omega}_m) \cdot (\rho \circ \tilde{\omega}_n) \,] 
\quad \text{since } \rho \circ \tau_m = \rho \\
&= [\, \rho \circ \tilde{\omega}_m \,] [\, \rho \circ \tilde{\omega}_n \,] \\
&= \Phi(m)\,\Phi(n)
\end{align*}
$$
and so $\Phi$ is a homomorphism.

*Isomorphism:* 
1. For each path $f:I \to S^1$ starting at $x_0 \in S^1$, and each $\tilde{x}_0\in p^{-1}(x_0)$, there is a unique **lift** $\tilde{f}:I \to \mathbb{R}$ starting at $\tilde{x}_0$ such that TFDC:
	![[Fundamental Group-1759579106302.png|200]]

2. For each homotopy $f_t:I\to X$ of paths starting at $x_0$ and each $\tilde{x}_0\in p^{-1}(x_0)$, there is a *unique* lifted homotopy $f_t:I\to \mathbb{R}$ of paths starting at $\tilde{x_0}$.


- *Surjectivity:* Recall $x_0 = (1,0)$. Let $[f]\in \pi_1(S^1,x_0)$. By existence in part (1), there exists a lift $\tilde{f}$ of $f$ starting at at $0$. Now $p \circ\tilde{f} = f$ and $p^{-1}(x_0) = p^{-1}(f(1)) = \mathbb{Z}$. 
	So $\tilde{f}(1) = \mathbb{Z}$. Letting $n := \tilde{f(1)}$, we get $\Phi(n) = [p \cdot \tilde{f}] = [f]$ and so $\Phi$ is surjective.

- *Injectivity:* Suppose $\Phi(m)=\Phi(n)$ so $[w_m]=[w_n]$, so $w_m \simeq w_n$, say via $f_t$. 
	By existence part of (b), there exists a lifted homotopy $\tilde{f}_t$ of paths starting at $0$. Uniqueness part of (a) implies $\tilde{f}_0 = \tilde{w}_m$, $\tilde{f}_1 = \tilde{w}_n$. So $m=n$ and so $\Phi$ is injective.   $\square$ 


# Brouwer fixed-point theorem

>[!thm]
>Every continuous map $f:D^2\to D^2$ has a fixed point. i.e. $\exists x \in D^2$ such that $f(x)=x$.
##### Proof
Suppose $f(x)\neq x$ for all $x \in D^2$.
Define $r:D^2 \to S^1=\partial D^2$ by intersecting the ray from $f(x)$ to $x$ with the boundary. Then $r$ is continuous, and if $x \in S^1$, then $r(x)=x$. So $r$ is a retraction of $D^2$ onto $S^1$.

![[Fundamental Group-1759585675849.png|200]]

Let $[f_0]$ be a non-trivial element of $\pi_1(S^1,x_0)$, then $f:I \to S^1$ is a loop at $x_0$. Let $c_0$ be the constant map, so $[c_0]$ is the identity of $\pi_1(S^1,x_0)$.

Thinking of $f_0,c_0$ as maps $I \to D^2$, we have $f_0 \simeq c_0$ in $D^2$ by a straight-line homotopy $f_t(x) = (1-t)f_0(s)+tx_0$. Then $r \circ f_t$ is a homotopy in $S^1$ from $r \circ f_0 = f_0$ to $r \circ c_0 = c_0$. Hence $[f_0] = [c_0]$ in $\pi_1(S^1,x_0)$, which is a contradiction since we assumed that $[f_0]$ is non-trivial. $\therefore$ $f$ has a fixed point.  $\square$


# Product of fundamental groups

>[!proposition] 
>If $X,Y$ are path-connected, then $\pi_1(X\times Y) \cong \pi_1(X) \times \pi_1(Y)$
##### Proof
$f:I \to X\times Y$ is continuous as $f(s) = (f_X(s), f_Y(s))$. Then the isomorphism is given by $[f] \mapsto ([f_X], [f_Y])$.

## Example

1. Torus $T^2 \cong S^1 \times S^1$ so $\pi_1(T^2) = \mathbb{Z} \times \mathbb{Z} = \mathbb{Z}^2$


# Application to CW

>[!proposition]
>For every group $G$, there is a two-dimensional cell complex $X$ with $\pi_1 (X) \cong G$.
##### Sketch of proof

Choose presentation $G = \langle S_\alpha \:|\: r_\beta\rangle$. Then construct $X$ with 
- one vertex $v$
- for each $S_\alpha$, a loop at $v$
- for each $r_\beta= S_{\alpha_1}^{\xi_1}S_{\alpha_2}^{\xi_2}...S_{\alpha_n}^{\xi_n}$ ($\xi_i = \pm 1$) attach a $2$-cell $e_\beta$ by sending $\partial e_\beta = S^1$ to the loop at $v$ given by $S_{\alpha_1}^{\xi_1}S_{\alpha_2}^{\xi_2}...S_{\alpha_n}^{\xi_n}$

## Example

![[Fundamental Group-1759722995154.png|650]]


