# Definition

>[!Definition]
>If $W$ is a [[G-Modules|submodule]] of $V$, then we can form a **quotient module** 
$$V/W =\{v+W\:|\:v\in V\}$$
where $v \sim w \iff w-v \in W$ for any $v,w \in V$. 

- We know that $V/W$ is a [[vector space]], but is also a [[G-Modules|G-Module]].


# Submodule Structure

>[!Proposition]
>Suppose $W$ is a submodule of a $G$-module $V$. Then $V/W$ becomes a $G$-module via
>$$g\cdot (v+W)=g\cdot v + W,\qquad g \in G,\: v \in V$$
##### Proof
###### Well-definedness

Suppose $v+W = v'+W$ and $g \in G$. Then $v-v' \in W$. So $g\cdot v-g\cdot v'= g \cdot (v-v') \in W$.
Thus $g \cdot v+W = g\cdot v'+W$.

###### Three Axioms

**Unital:** Take $v \in V$. Then $1_G\cdot (v+W)=1_G \cdot v + W = v + W$

**Associativity:** $v \in V,$ and $g,h \in G$. Then
$$(gh)\cdot (v+W)=(gh)\cdot v + W = g\cdot (h \cdot v)+W = g(h\cdot v+W)= g\cdot(h\cdot(v+W))$$
**Linearity:** Take $v,v'\in V$, $\lambda,\mu \in \mathbb{F}$, and $g \in G$. Then
$$g\cdot(\lambda(v+W)+ \mu(v'+W)) = g\cdot((\lambda v+\mu v') + W) = (\lambda g v + \mu g v') + W = \lambda(g\cdot v + W) + \mu (g \cdot v' + W)$$
hence the action of $G$ on $V/W$ is linear, so $V/W$ is a $G$-module.
$\square$

# First Isomorphism Theorem

>[!Theorem]
>Suppose $\varphi: V\to W$ is a $G$-module homomorphism. Then 
$$V / \ker \varphi \cong \text{im }\varphi$$
as $G$-modules.
##### Proof
We know that $\text{im }\varphi$ and $\ker \varphi$ are both $G$-submodules so the statement makes sense.

Define a map $\Phi: V/\ker \varphi \to \text{im }\varphi$ by $\Phi(v+ \ker \varphi) = \varphi(v)$ for all $v \in V$. 

###### Well-definedness
Take $v+\ker \varphi = v' + \ker \varphi$. Then $v-v' \in \ker \varphi$. i.e. $0=\varphi(v-v')=\varphi(v)-\varphi(v')$ so $\varphi(v)=\varphi(v')$.
Consequently, $\Phi(v + \ker \varphi) = \varphi(v) = \varphi(v') = \Phi(v'+\ker \varphi)$.

###### G-module homomorphism
$\Phi$ is a $G$-module homomorphism because it is linear by definition. So 
$$\Phi(g\cdot(v+\ker\varphi)) = \Phi(g\cdot v+ \ker \varphi)= \varphi(g\cdot v)=g \cdot \varphi(v) = g \cdot \Phi(v + \ker \varphi).$$
###### Isomorphism
$\Phi$ is surjective by definition because if $w \in \text{im }\varphi$, then there exists $v \in V$ such that $w = \varphi(v) = \Phi(v+\ker \varphi)$ so $w \in \text{im }\Phi$.
Therefore $\Phi$ is *surjective*.

If $\Phi(v + \ker \varphi)= 0$, then $\varphi(v)=0$. So $v \in \ker \varphi$ and thus $v + \ker \varphi = 0+ \ker \varphi$.
Hence $\ker \Phi = \{0 + \ker \varphi\}$, which is the zero vector in $V/\ker \varphi$.
Therefore $\Phi$ is *injective*.

# Other Isomorphism Theorems

>[!Theorem]
Let $V$ be a $G$-module.
>2. Suppose $X$ and $Y$ are submodules of $V$ $\implies (X+Y)/Y \:\cong\: X/(X\cap Y)$ 
>3. Suppose $U \leq W \leq V$ are submodules of $V$ $\implies V/W \:\cong\: (V/U)/(W/U)$
>4. Suppose $W$ is a submodule of $V$. Then there is a 1-to-1 inclusion preserving correspondence between submodules of $V$ that contain $W$ and the submodules of $V/W$
##### Proof Sketch
###### 2. 
*Recap:* If $X$ and $Y$ are subspaces of $V$, then $X+Y = \{x + y \:|\: x \in X, y \in Y\}\subseteq V$. 
If we take $x \in X$ and $y \in Y$, then $g(x+y) = gx+gy \in X+Y$ so $X+Y$ is a $G$-submodule of $V$.

Define $\Psi:Y\to (X+Y)/X$  by $\Psi(y) = y+X \in (X+Y)/X$.
$\Psi$ is a $G$-module homomorphism because it is both linear and an intertwiner.

By the first isomorphism theorem, $Y/\ker \Psi \cong \text{im }\Psi = (X+Y)/X$ and $\ker \Psi = \{y \in Y \:|\: y + X = 0_{(X+Y)/Y}\} = X \cap Y$ since $y + X = 0 + X \iff y \in X$. $\square$

###### 3.
Define $\Theta: V \to (V/U)/(Y/U)$ by $\Theta(v)= (v+U) + W/U$ which we can check to be well-defined.
$\Theta$ is a $G$-module homomorphism because it is both linear and an intertwiner.

By first isomorphism theorem, $V/\ker \Theta \cong \text{im }\Theta = (V/X)/(Y/X)$ and $\ker \theta = \{v \in V \:|\: v \in Y\} = V \cap Y = Y$. 
Therefore $V/Y \cong (V/X)/(Y/X)$. $\square$

###### 4.
We have a natural map $\pi: V \to V/U$ given by $\pi(v) = v+ U$. 
$\text{im }\pi = V/U$ and $\ker \pi = U$. 
If $W$ is a $G$-submodule of $V$ that contains $U$, then $W/U = \pi(W)$ is a $G$-submodule of $V/U$.

Conversely if $\mathcal{W}$ is a $G$-submodule of $V/U$ then $W = \pi^{-1}(\mathcal{W}) = \{v \in V \:| \pi (v) \in \mathcal{W}\}$ 
is a vector subspace of $V$ (since $\pi$ is linear).
$U \subseteq W$ because if $u \in U$, then $\pi(u) = u + U = 0_{V/U} \in \mathcal{W}$.
Moreover, $W$ is a $G$-submodule because if $g \in G$ and $w \in W$, then $\pi(gw) = g\pi(w) \in \mathcal{W}$ since $\mathcal{W}$ is a $G$-module. 
$\implies gw \in W \implies W$ is a $G$-submodule of $V$ containing $U$. $\square$



# Dimension of $V/U$

Let $\{u_1,...,u_m\}$ be a basis of $U$. By the basis extension theorem, $V$ has a basis of the form $\{u_1,...,u_m,v_{m+1},...,v_n\}$ 

>[!Claim] 
>$V/U$ has basis $\{v_{m+1}+ U,...,v_n + U\}$. 
>So $\dim V/U = \dim V - \dim U = n-m$
##### Proof
$$\begin{align*}
V/U = \langle v+ U \:|\: v \in V\rangle &= \left\langle \sum_{i=1}^m\lambda_iu_i + \sum_{i=m+1}^n \mu_iv_i \: + U\right \rangle \\
&= \left \langle \sum_{i=m+1}^n \mu_iv_i \: + U \:|\: \mu_i \in \mathbb{F}\right \rangle\\
\end{align*}$$
So $\{v_{m+1}+U,...,v_n+U\}$ spans $V/U$. Still need to show it is linearly independent.
If $0 = \sum_{i=m+1}^n \mu_i(v_i + U) = \sum_{i=m+1}^n(\mu_iv_i)+ U$,
then $\sum \mu_i v_i \in U \implies \mu_i = 0$. Hence the set is a basis for $V/U$.  $\square$


