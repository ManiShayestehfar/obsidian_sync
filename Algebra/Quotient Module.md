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
##### Proof
###### 2. 
Since $X$ and $Y$ are submodules of $V$, their sum $X+Y=\{x+y\mid x\in X,\ y\in Y\}$ is also a submodule of $V$. Indeed, if $g\in G$ and $x+y\in X+Y$, then $g(x+y)=gx+gy\in X+Y$, since $gx\in X$ and $gy\in Y$.

Define $\Phi:X\to (X+Y)/Y$ by $\Phi(x)=x+Y$. This is the restriction to $X$ of the quotient map $X+Y\to (X+Y)/Y$, so $\Phi$ is a $G$-module homomorphism.

We now show that $\Phi$ is surjective. Let $(x+y)+Y\in (X+Y)/Y$, where $x\in X$ and $y\in Y$. Since $y+Y=Y$, we have $(x+y)+Y=x+Y=\Phi(x)$. Hence $\operatorname{im}\Phi=(X+Y)/Y$.

Next,
$$
\ker\Phi
=
\{x\in X\mid \Phi(x)=Y\}
=
\{x\in X\mid x+Y=Y\}
=
\{x\in X\mid x\in Y\}
=
X\cap Y.
$$

Therefore, by the first isomorphism theorem, $X/\ker\Phi\cong\operatorname{im}\Phi$. Since $\ker\Phi=X\cap Y$ and $\operatorname{im}\Phi=(X+Y)/Y$, we obtain
$$
X/(X\cap Y)\cong (X+Y)/Y.
$$
Equivalently, $(X+Y)/Y\cong X/(X\cap Y)$. $\square$


###### 3.
Define $\Theta:V\to (V/U)/(W/U)$ by $\Theta(v)=(v+U)+W/U$. 
This is well-defined because $U\leq W\leq V$, so $W/U$ is a submodule of $V/U$.

The map $\Theta$ is a $G$-module homomorphism, since for $v_1,v_2\in V$, $\lambda\in F$ and $g\in G$, we have $\Theta(v_1+\lambda v_2)=((v_1+\lambda v_2)+U)+W/U=((v_1+U)+W/U)+\lambda((v_2+U)+W/U)=\Theta(v_1)+\lambda\Theta(v_2)$, and $\Theta(gv)=(gv+U)+W/U=g((v+U)+W/U)=g\Theta(v)$.

The map $\Theta$ is surjective because every element of $(V/U)/(W/U)$ has the form $(v+U)+W/U=\Theta(v)$ for some $v\in V$.

Moreover, $\ker\Theta=\{v\in V\mid (v+U)+W/U=W/U\}=\{v\in V\mid v+U\in W/U\}=\{v\in V\mid v\in W\}=W$.

	Therefore, by the first isomorphism theorem, $V/\ker\Theta\cong\operatorname{im}\Theta$. Since $\ker\Theta=W$ and $\operatorname{im}\Theta=(V/U)/(W/U)$, we obtain $V/W\cong (V/U)/(W/U)$. $\square$

###### 4.
Let $V$ be a $G$-module, and let $U$ be a $G$-submodule of $V$. Let $\pi : V \to V/U$ be the quotient map, defined by $\pi(v) = v + U$.

We claim that there is a one-to-one inclusion-preserving correspondence between the $G$-submodules $W \leq V$ such that $U \subseteq W$, and the $G$-submodules $\mathcal W \leq V/U$.

First, suppose $W \leq V$ is a $G$-submodule with $U \subseteq W$. Then $\pi(W) = W/U$, so $W/U$ is a vector subspace of $V/U$. Moreover, if $g \in G$ and $w + U \in W/U$, then $gw \in W$ because $W$ is a $G$-submodule. Hence $g(w+U) = gw + U \in W/U$, so $W/U$ is a $G$-submodule of $V/U$.


Conversely, suppose $\mathcal W \leq V/U$ is a $G$-submodule. Define $W = \pi^{-1}(\mathcal W) = \{v \in V : \pi(v) \in \mathcal W\}$. Since $\pi$ is linear, $W$ is a vector subspace of $V$. Also, $U \subseteq W$, because if $u \in U$, then $\pi(u) = u + U = 0_{V/U} \in \mathcal W$. Finally, if $g \in G$ and $w \in W$, then $\pi(w) \in \mathcal W$, so $\pi(gw) = g\pi(w) \in \mathcal W$, since $\mathcal W$ is a $G$-submodule. Therefore $gw \in W$, and hence $W$ is a $G$-submodule of $V$ containing $U$.

These constructions are inverse to each other. Indeed, if $W \leq V$ contains $U$, then $\pi^{-1}(W/U) = W$. Also, if $\mathcal W \leq V/U$, then $\pi(\pi^{-1}(\mathcal W)) = \mathcal W$, since $\pi$ is surjective.

Therefore the maps $W \mapsto W/U$ and $\mathcal W \mapsto \pi^{-1}(\mathcal W)$ give a one-to-one correspondence between $G$-submodules of $V$ containing $U$ and $G$-submodules of $V/U$. Moreover, the correspondence is inclusion-preserving, since if $W_1 \subseteq W_2$, then $W_1/U \subseteq W_2/U$, and if $\mathcal W_1 \subseteq \mathcal W_2$, then $\pi^{-1}(\mathcal W_1) \subseteq \pi^{-1}(\mathcal W_2)$. $\square$

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


