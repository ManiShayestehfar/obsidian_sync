
# Definition

>[!def] Fundamental group
>The **fundamental group** $\pi_1(X,x_0)$ of $X$ based at base point $x_0$ is the set of all homotopy classes $[f]$ of loops $f:I \to X$ based at $x_0$.

##### Proof: Group properties

*Well-definedness:* If $f_0\simeq f_1$ , $g_0\simeq g_1$ then $f_0 \circ g_0 = f_1 \circ g_1$. Also composing two paths gives a paths so we have closure.

*Associativity:* 
$$\begin{align*}
([f][g])[h] &= [f \circ g][h] \\
&= [(f \circ g) \circ h] \\
&= [f \circ (g \circ h)] \\
&= [f][g \circ h] \\
&= [f]([g][h])
\end{align*}$$
*Identity:* Let $c_0 : I \to X$ be the constant path at $x_0$. Then
$$\begin{align*}
[c_0][f] &= [c_0 \circ f] = [f] \\
[f][c_0] &= [f \circ c_0] = [f]
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
$h$ a path from $x_0$ to $x_1$. Define $\beta_h: \pi_1(X,x_0)\to \pi_1(X,x_1)$ by $[f] \mapsto [h \circ f \circ\bar{h}]$.

*Well-defined:* If $f_0\simeq f_1$, then $h \circ f_0 \circ\bar{h} \simeq h \circ f_1 \circ\bar{h}$.
*Homomorphism:* Given loops $f,g$ based at $x_1$, we have 
$$\begin{align*}
\beta_h([f])\beta_h([g]) &= [h \circ f \circ\bar{h}][h \circ g \circ\bar{h}] \\
&= [h \circ f \circ\bar{h} \circ h \circ g \circ\bar{h}] \\
&= [h \circ f \circ c_1 \circ g \circ\bar{h}] \\
&= [h \circ f \circ g \circ \bar{h}] \\
&= \beta_h([f \circ g]) \\
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
Now if $\tilde{f}_n:I\to \mathbb{R}$ is any path from $0$ to $n$ then $\tilde{f}_n \simeq \tilde{w}_n$ by straight-line homotopy. Thus $p \circ \tilde{f}_n \simeq p \circ \tilde{w}_n = w_n$. That is, for any path $\tilde{f}_n$ we have $\Phi(n):=[w_n] = [p \circ\tilde{f}_n]$.

*Showing $\Phi$ is a homomorphism:* Need $\Phi(m+n) = \Phi(m) + \Phi(n)$. i.e. $[w_{m+n}]=[w_m][w_n]$.
Let $\tau_m: \mathbb{R} \to \mathbb{R}$ be translation by $m$, i.e. $\tau_m(x) = x+m$. Then $\tilde{w}_m \circ(\tau_m \circ \tilde{w}_n) \simeq \tilde{w}_{m+n}$ is a path from $0$ to $m+n$ in $\mathbb{R}$. Hence,
$$\begin{align*}
\Phi(m+n) 
&= [\, \rho \circ \tilde{\omega}_{m+n} \,] \\
&= [\, \rho \circ (\tilde{\omega}_m \cdot (\tau_m \circ \tilde{\omega}_n)) \,] \\
&= [\, (\rho \circ \tilde{\omega}_m) \cdot (\rho \circ \tau_m \circ \tilde{\omega}_n) \,] \\
&= [\, (\rho \circ \tilde{\omega}_m) \cdot (\rho \circ \tilde{\omega}_n) \,] 
\quad \text{since } \rho \circ \Sigma_m = \rho \\
&= [\, \rho \circ \tilde{\omega}_m \,] [\, \rho \circ \tilde{\omega}_n \,] \\
&= \Phi(m)\,\Phi(n)
\end{align*}

\[
\therefore \quad \Phi \text{ is a homomorphism.}
\]
$$