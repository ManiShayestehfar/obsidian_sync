# FG-Module and G-Module

Let $G$ be a *finite* group, and $\mathbb{F}$ a field.

>[!def]
>An **$\mathbb{F}G$-module** or a **representation of $G$**, is an $\mathbb{F}$-[[vector space]] $V$ that comes equipped with a unitary linear $G$-action. i.e. a map $G \times V\to V$ given by $(g,v)\to gv$ such that 
>
>**Unital:** $1_G v = v$  for all $v \in V$
>**Associative:** $(gh)v = g(hv)$  for $g,h\in G$ and $v \in V$
>**Linear:** $(\lambda v + \mu w)g = \lambda vg + \mu wg$  for all $g \in G$, $\lambda, \mu \in \mathbb{F}$, and $v,w\in V$ 

- Strictly, the former definition is a **left $G$-module**. The same applied for a right module where $V \times G \to V$ is given by $(g,v) \to vg$ 
- Fix a basis $\{e_1,...,e_n\}$ of $V$ and for each $g \in G$, define the matrix $\mathbf{g} = (g_{ij})$ by
	$$ge_j = \sum_{i=1}^ng_{ij}\:e_i$$
- A matrix **representation** of $G$ is a group homomorphism $\rho: G \to GL_n(\mathbb{F})$, the group of invertible  $n\times n$ matrices with entries in $\mathbb{F}$.


## Equivalence of Representation and G-Modules

>[!proposition]
>Let $V$ be an $n$-dimensional $G$-module. Then $V$ determines a representation $\rho_V: G\to GL_n(\mathbb{F})$. Conversely, if $\rho:G \to GL_{n}(\mathbb{F})$ is a group homomorphism then $V = \mathbb{F}^n$ becomes a $G$-module by defining the action of $g \in G$ on $V$ to be given by matrix multiplication by $\rho(g)$.
##### Proof
Fix a basis $\{e_1,\ldots,e_n\}$ of $V$ and for each $g \in G$ define the matrix $\mathbf{g}$ as above. We claim that the map $\rho_V : G \to GL_n(\mathbb{F}); g \mapsto \mathbf{g}$ is a representation of $G$.

We have already shown that $\rho_V(gh) = \rho_V(g)\rho_V(h)$.
So it remains to show that $\rho(g) \in GL_n(\mathbb{F})$ for $g \in G$. However, if $g \in G$, then $g^m = 1$ for some $m \geq 1$ since $G$ is a finite group. Therefore,
$$\mathbf{g}^m = \rho_V(g)^m = \rho_V(g^m) = I_n,$$
 where $I_n$ is the $n \times n$ identity matrix. Consequently, $\mathbf{g} = \rho_V(g)$ is an invertible matrix, and so $\rho_V(g) \in GL_n(\mathbb{F})$. Hence, $\rho_V$ is a matrix representation of $G$.

If $\{f_1,\ldots,f_n\}$ is another basis of $V$, then there is an invertible matrix $A = (a_{jk}) \in GL_n(\mathbb{F})$ such that $f_k = \sum_{j=1}^n a_{jk}e_j$. Let $B = A^{-1} = (b'_{ij})$, so that $e_j = \sum_{i=1}^n b'_{ij}f_i$. Then
$$\begin{aligned}
gf_k
&= g\left(\sum_{j=1}^n a_{jk}e_j\right) \\
&= \sum_{j=1}^n a_{jk}ge_j \\
&= \sum_{j=1}^n a_{jk}\left(\sum_{i=1}^n g_{ij}e_i\right) \\
&= \sum_{j=1}^n a_{jk}\left(\sum_{i=1}^n g_{ij}\left(\sum_{l=1}^n b'_{li}f_l\right)\right) \\
&= \sum_{l=1}^n\left(\sum_{i=1}^n\sum_{j=1}^n b'_{li}g_{ij}a_{jk}\right)f_l \\
&= \sum_{l=1}^n (A^{-1}\mathbf{g}A)_{lk}f_l.
\end{aligned}$$
Therefore, with respect to the basis $\{f_1,\ldots,f_n\}$, $g$ acts on $V$ via the matrix $A^{-1}\mathbf{g}A$. Hence, the matrix representation corresponding to the basis $\{f_1,\ldots,f_n\}$ is $\mathbf{g} \mapsto A^{-1}\mathbf{g}A$, where $A$ is the transition matrix from that $e$-basis to the $f$-basis. $\square$

**Remark:** $\text{im } \rho_{V}^{E} = A^{-1}\text{im } \rho_{V}^{F}A$  are conjugate subgroups of $GL_n(\mathbb{F})$



## FG-Module Examples

1. $G = GL_n(\mathbb{F}) = \{\text{invertible}\:\: n \times n \:\:\text{matrices made of}\:\: \mathbb{F}\}$ 
The natural representation is 
$$V = \mathbb{F}^n = \left\{\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix}\:\Bigg|\: \lambda_i \in \mathbb{F}\right\} 
$$
If $A = (a_{ij}) \in G$, then $A\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix}$ is given by matrix multiplication

2. $G = S_n$.  $V = \mathbb{F}^n$ with $S_n$-action
$$a\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix} := \begin{pmatrix}\lambda_{a(1)} \\ \vdots \\ \lambda_{a(n)}\end{pmatrix}$$


## G-Module Homomorphism & Isomorphisms

- Let $V,W$ be $G-$modules.

> [!info] G-Module Homomorphism
> A **$G-$Module Homomorphism** is a linear transf. $\phi : V \to W$ that commutes with the $G-$action. i.e. $\phi(g\cdot v) = g\cdot \phi(v)$ for all $g\in G$, $v\in V$.

> [!info] G-Module Isomorphism
> A **$G-$Module Isomorphism** is a bijective $G-$module homomorphism, $\phi : V \to W$ that commutes with the $G-$action. i.e. $\phi(g\cdot v) = g\cdot \phi(v)$ for all $g\in G$, $v\in V$. We write $V\cong W$. 

---

# Submodules

- Let $V,W$ be $G-$modules, and let
$$\begin{align*}
\text{Hom}_G(V,W)&=\{\phi:V\to W\:|\:\phi\:\text{a G-module homomorphism}\} \\[6pt]
\text{End}_G(V) = \text{Hom}_G(V,V) &= \{\phi:V\to V\:|\:\phi\:\text{a G-module endomorphism}\} 
\end{align*}$$
- **NOTE:** $\text{End}_G(V)$ is a [[Ring|ring]], multiplication given by composition of maps.

>[!def]
>If $V$ is an $\mathbb{F}$-vector space then a subset $W$ of $V$ is a **submodule** of $G$ if 
>
>1. $W$ is a subspace of $V$
>2. $g\cdot w \in W$ for all $w \in W$ and all $g \in G$
>   
>   Every submodule $W$ of a $G-$module is by definition a $G-$module.

>[!Lemma]
>Suppose $\varphi:V \to W$ is a $G$-module homomorphism. Then
>1. $\ker \varphi = \{v \in V \:|\: \varphi(v)=0\}$ is a $G$-submodule of $V$
>2. $\text{im }\varphi = \{\varphi(v) \:|\: v \in V\}$ is a $G$-submodule of $W$
##### Proof
###### 1.
1.  Clearly $\ker\varphi \subset V$ 
2. Let $g \in G$. $\varphi(vg) = g\varphi(v) = g\cdot 0 = 0$ and so $vg \in \ker \varphi$, where the choice of $v$ and $g$ were arbitrary.    $\square$ 
###### 2.
1. $\text{im}\:\phi \subset W$   
2. Let $w = \varphi(v)$ for $v \in V$ and $w \in W$. And $gw = g\varphi(v) = \varphi(gv) \in \text{im}\: W$ for all $g \in G$ and so $gw \in \text{im }W$.     $\square$ 

---
# Irreducible G-modules

>[!def]
>- A $G$-module $V$ is **irreducible** if it contains no proper nonzero submodules. i.e its only submodules are $0$ and $V$. Otherwise, $V$ is **reducible**.
>- A $G$-module $V$ is **completely reducible**, or **semisimple**, if it is isomorphic to a direct sum of irreducible $G$-modules.

## Dimension of Irreducible FG-Modules

>[!corollary] 
>Suppose $\mathbb{F}G$ is Schurian, where $\mathbb{F}$ is a field of characteristic $p$ such that $p \nmid |G|$. Let $d_1,d_2,...,d_t$ be the dimensions of the irreducible $\mathbb{F}G$-modules, counted up to isomorphism. Then $|G|= d_1^2+\cdots +d_t^2$.
##### Proof

By [[Maschke's Theorem]] $\mathbb{F}G$ is a semisimple $\mathbb{F}$-algebra. Hence, this follows by taking dimensions on both sides of the Artin-Wedderburn decomposition of $\mathbb{F}G$. 

---
# Regular Representation

> [!def]
> The (left) **regular representation** of $G$ is the $\mathbb{F}$-vector space $\mathbb{F}G$ that has as its basis the elements of $G$ and the $G$-action is given by left multiplication. Thus
> $$\mathbb{F}G = \left\{\sum_{x\in G}\lambda_x x \;|\; \lambda_x \in \mathbb{F} \right\}$$
> and $g\left(\sum_{x\in G}\lambda_x x \right) = \sum_{x \in G} \lambda_x (gx) = \sum_{y = xg \in G} \lambda_{g^{-1}y}y$ 

- Since the elements of $G$ are a basis for $\mathbb{F}G$, then addition and multiplication in $\mathbb{F}G$ are component-wise operations.
- $\text{dim} \mathbb{F}G = |G|$
 
>[!lemma]
>The vector space $\mathbb{F}G$ is a $G$-module.
#### Proof
- $\mathbb{F}G$ is a a $\mathbb{F}$-vector space by definition $\checkmark$  
- Action of $G$ on $\mathbb{F}G$ is linear with $1_G$ as identify $\checkmark$ 
- Need to check associativity on basis $\{x | x \in G\}$ of $\mathbb{F}G$:
$$(gh)x = g(hx)$$
for all $g,h,x \in G$ and therefore associativity is given. $\square$

>[!proposition]
> With the natural multiplication defined, $FG$ is an associative ring with $1_G$ as identity.
> The natural multiplication comes from a natural multiplication in $G$:
> $$
> \left(\sum_{x\in G}\lambda_x x\right)
> \left(\sum_{y\in G}\mu_y y\right)
> =
> \sum_{z\in G}
> \left(
> \sum_{\substack{x,y\in G\\ z=xy}}
> \lambda_x\mu_y
> \right)z,
> $$
> for $\lambda_x,\mu_y\in F$. Equivalently,
> $$
> \left(\sum_{x\in G}\lambda_x x\right)
> \left(\sum_{y\in G}\mu_y y\right)
> =
> \sum_{z\in G}
> \left(
> \sum_{g\in G}
> \lambda_{zg}\mu_{g^{-1}}
> \right)z
> =
> \sum_{z\in G}
> \left(
> \sum_{g\in G}
> \lambda_g\mu_{g^{-1}z}
> \right)z.
> $$
##### Proof
By the last Lemma, $FG$ is a vector space. In particular, it is an abelian group under addition. Looking at the formula above for multiplication in $FG$ we have  
$$  
\left(\sum_{x\in G}\lambda_x x\right)  
\left(\sum_{y\in G}\mu_y y\right)  
=  
\sum_{x\in G}  
\lambda_x x  
\left(\sum_{y\in G}\mu_y y\right)  
=  
\sum_{y\in G}  
\mu_y  
\left(\sum_{x\in G}\lambda_x x\right)y.  
$$
So, multiplication in $FG$ is bilinear—that is, linear in both the $x$'s and the $y$'s. Hence, it suffices to check that the associative and distributive laws hold on the basis of $FG$ given by the group elements. The multiplication in $G$ is associative so $x(yz)=(xy)z$, for all $x,y,z\in G$, showing that multiplication in $FG$ is also associative. For the distributive laws by linearity we need only check that $(a+b)x=ax+bx$ and $x(a+b)=xa+xb$ for $x\in G$ and $a,b\in FG$, however, this follows from the multiplication formulas given above. Finally, it is clear that $1_G$ is an identity element for $FG$, so we're done. $\square$



> [!Proposition]
> If multiplication is defined by
>
> $$\left(\sum_{x \in G} \lambda_x x\right)\left(\sum_{y \in G} \mu_y y\right)
> =
> \sum_{z \in G}\left(\sum_{\substack{x,y \in G \\ z = xy}} \lambda_x \mu_y\right)z,$$
>
> for $\lambda_x,\mu_y \in \mathbb{F}$, then $\mathbb{F}G$ is an associative ring with $1_G$ as identity. The natural multiplication comes from a natural multiplication in $G$.
>
> Equivalently,
>
> $$\left(\sum_{x \in G} \lambda_x x\right)\left(\sum_{y \in G} \mu_y y\right)
> =
> \sum_{z \in G}\left(\sum_{g \in G} \lambda_{zg^{-1}}\mu_g\right)z
> =
> \sum_{z \in G}\left(\sum_{g \in G} \lambda_g\mu_{g^{-1}z}\right)z.$$
##### Proof
By the last lemma, $\mathbb{F}G$ is a vector space. In particular, it is an abelian group under addition. Looking at the formula above for multiplication in $\mathbb{F}G$, we have
$$\left(\sum_{x \in G} \lambda_x x\right)\left(\sum_{y \in G} \mu_y y\right)
=
\sum_{x \in G} \lambda_x x\left(\sum_{y \in G} \mu_y y\right)
=
\sum_{y \in G} \mu_y\left(\sum_{x \in G} \lambda_x x\right)y.$$

So, multiplication in $\mathbb{F}G$ is bilinear. That is, linear in both the $x$’s and the $y$’s. Hence, it suffices to check that the associative and distributive laws hold on the basis of $\mathbb{F}G$ given by the group elements.

The multiplication in $G$ is associative, so $x(yz) = (xy)z$ for all $x,y,z \in G$, showing that multiplication in $\mathbb{F}G$ is also associative.

For the distributive laws, by linearity we need only check that $(a+b)x = ax + bx$ and $x(a+b) = xa + xb$ for $x \in G$ and $a,b \in \mathbb{F}G$; however, this follows from the multiplication formulas given above.

Finally, it is clear that $1_G$ is an identity element for $\mathbb{F}G$, so we are done. $\square$

>[!success] NOTE
>$\mathbb{F}G$  is both an $\mathbb{F}$-[[Vector Space]], and a [[Ring]]

---

# Maximal submodules of $\mathbb{F}G$

>[!Proposition]
>Let $D$ be an irreducible $\mathbb{F}G$-module. Then there exists a maximal proper $G$-submodule $M$ of $\mathbb{F}G$ such that $D \cong \mathbb{F}G/M$ as $G$-modules.
##### Proof
Let $0 \neq d \in D$. Define the map $\varphi_d: \mathbb{F}G \to D,$ by $$\sum_{g \in G} \lambda_g g \mapsto \sum_{g \in G} \lambda_g g\cdot d \in D$$
>[!Claim]
>$\varphi_d$ is a $G$-module homomorphism.
###### Proof
- $\varphi_d$ is linear because $G$ acts linearly on $D$
- If $x \in G$, then $\varphi_d(xg) = \varphi_d(xg\cdot 1_G) = (xg)d = x(gd) = x \varphi_d(g)$ hence associative
Hence $\varphi_d$ is a $G$-module homomorphism. $\square$

By First Isomorphism Theorem, $\mathbb{F}G/\ker \varphi_d \cong \text{im }\varphi_d$.
$\text{im }\varphi_d$ is either $0$ or $D$ since $D$ is irreducible. Clearly $\text{im }\varphi_D \neq 0$ since $d = \varphi_d(1_G)$ exists and so the image is non-zero.

Set $M = \ker \varphi_d \implies \mathbb{F}G / M \cong D$. 
By the fourth Isomorphism theorem (correspondence theorem), $G$-submodules of $\mathbb{F}G$ such that $M \subseteq W \subseteq \mathbb{F}G$ is in one-to-one correspondence with $G$-submodules of $\text{im }\varphi_d = D$ which are ${0,D}$.

Since $D$ is irreducible, then it must be in correspondence with $\mathbb{F}G/M$ which is irreducible. Hence $M$ is proper maximal.


## Another Proposition

>[!Proposition]
>Suppose $V$ is an $n$-dimensional $G$-module. Then $$\mathbb{F}G^{\oplus n}/M \cong V$$
>for some $M \subseteq \mathbb{F}G^{\oplus n}$
##### Proof
Let $\{v_1,...,v_n\}$ be a basis of $V$. Define a map $\psi: \mathbb{F}G \oplus ... \oplus \mathbb{F}G \to V$ by $(x_1,...,x_n) \mapsto \sum_{i=1}^n x_iv_i$ 
It follows from the pervious proof that $\psi$ is indeed a $G$-module homomorphism.

---

# FG-Modules vs G-Modules

>[!Proposition] 
>Let $V$ be an $\mathbb{F}$-vector space. Then $V$ is an $A$-module if and only if there is an algebra homomorphism $\Phi: A \to \text{End}_\mathbb{F}(V),\quad a \mapsto \varphi_a$ such that $a \cdot v = \varphi_a(v)$.
##### Proof
###### ($\Rightarrow$) 
Let $v_1,...,v_n$ be basis for $V$. If $V$ is an $A$-module and $a \in A$ we can define a matrix $a \in \text{Mat}_n(\mathbb{F})$ by $$av_j = \sum_{i=1}^n a_{ij}v_i$$
Define $\Phi: A \to \text{Mat}_n(\mathbb{F})$ by $\Phi(a) = (a_{ij}) = \varphi_a$.
Then $\Phi$ is linear because $A$ acts linearly on $V$ and $\Phi(ab) = \Phi(a)\Phi(b)$ since $(ab)v = a(bv)$.
By assumption $1_Av_j = v_j$ and so $\Phi(1_A) = 1_{\text{Mat}_n(\mathbb{F})}$.

###### ($\Leftarrow$)
Conversely, given an algebra map $\Phi: A \to \text{Mat}_n(\mathbb{F})$, we can define an $A$-action $A\times V \to V$ by $a\cdot v = \Phi(a)v$, where if $\Phi(a)= (a_{ij})$ then this means that $a\cdot v_j = \sum_{i=1}^n a_{ij}v_i$.

Bilinearity comes from the fact that the $A$-action is linear in $A$ because $\Phi$ is an algebra map so $\Phi(\lambda a + \mu b) = \lambda\Phi(a) + \mu \Phi(b)$ and it is linear on $V$ because matrix multiplication is linear.

Unitality comes from that fact that $\Phi(1_A) = 1_\text{Mat}\implies 1_A\cdot v = 1_{\text{Mat}}$ for all $v \in V$.

Associativity: $\Phi(ab) = \Phi(a)\Phi(b)\implies (ab)\cdot v = a\cdot (bv)$
$\square$


>[!proposition]  
>Let $G$ be a finite group and $\mathbb{F}$ a field
>1. Every $G$-module is an $\mathbb{F}G$-module
>2. Every $\mathbb{F}G$-module is a $G$-module
>3. Let $V$ and $W$ be $G$-modules of $\mathbb{F}G$-modules. Then $V \cong W$ as $G$-modules $\iff\: V \cong W$ as $\mathbb{F}G$-modules.

##### Proof 
###### 1. 
Let $V$ be a $G$-module. By the proposition above, $V$ is an $\mathbb{F}G$-module if and only if there is an algebra homomorphism $\Phi: \mathbb{F}G\to \text{End}_n(\mathbb{F})$.
Define $\Phi\left(\sum_{g \in G}\lambda_gg\right) = \sum_{g \in G} \lambda_g \rho(g)$  where $\rho:G \to GL(V)$ given by $\rho(g)(v)=g\cdot v$ is a group homomorphism and has a matrix action form.
 
- $\Phi$ is linear by definition 
- Let $x = \sum_{g \in G} \lambda_g g$ and $y = \sum_{h \in G} \mu_hh$, then 
  $$\Phi(xy) = \sum_{g,h \in G} \lambda_g\mu_h \rho(gh) = \sum_{g,h \in G} \lambda_g\mu_h \rho(g)\rho(h) = \left(\sum_{g\in G} \lambda_g \rho(g)\right)\left(\sum_{h \in G} \mu_h \rho(h)\right) = \Phi(x)\Phi(y).$$
- Also $\Phi(1_{\mathbb{F}G}) = \Phi(e)=\rho(e)=\text{id}_V$
Thus $\Phi$ is an $\mathbb{F}$-algebra homomorphism. By Proposition 13, this makes $V$ an $\mathbb{F}G$-module.

###### 2.
Let $V$ be an $\mathbb{F}G$-module. By Proposition 13, this is equivalent to an algebra homomorphism $\Phi:\mathbb{F}G \to \text{End}_\mathbb{F}(V)$ such that $x \cdot v = \Phi(x)(b)$.

We want to define a $G$-action on $V$.
Since every $g \in G$ is an element of $\mathbb{F}G$, then define $g \cdot v := \Phi(g)(v)$.
-  $e \cdot v = \Phi(e)(v) = \text{id}_V(v)=v$ since $e = 1_{\mathbb{F}G}$ and $\Phi$ is unital
- $(gh)\cdot v = \Phi(gh)(v)=\Phi(g)\Phi(h)(v) = \Phi(g)(h\cdot v)=g\cdot(h \cdot v)$ because $\Phi$ is an algebra homomorphism.
Hence the action defines a $G$-module structure on $V$.

###### 3. $(\Rightarrow)$
Suppose $V \cong W$ as $G$-modules.
Then there exists an $\mathbb{F}$-linear bijection: $T:V \to W$ such that $T(g\cdot v)=g\cdot T(v)$.
We need to show $T$ is an $\mathbb{F}G$-module isomorphism.

Take $x = \sum_{g \in G}\lambda_gg \in \mathbb{F}G$.
Then $T(x\cdot v)=T\left(\sum_{g \in G} \lambda_gg \cdot v\right) = \sum_{g \in G} \lambda_g T(g \cdot v)$ since $T$ is $\mathbb{F}$-linear.
Since $T$ is a $G$-module homomorphism, then $T(g\cdot v)g \cdot T(v)$. Hence $T(x\cdot v) = x \cdot T(v)$.
So $T$ respects the $\mathbb{F}G$-action, hence it is an $\mathbb{F}g$-module isomorphism.

###### 3. $(\Leftarrow)$
Suppose $V \cong W$ as $\mathbb{F}G$-modules.
Then there exists an $\mathbb{F}$-linear bijection: $T:V \to W$ such that $T(x\cdot v)=x \cdot T(v)$ this time with $x \in \mathbb{F}G$ instead.
In particular every $g \in G$ is an element of $\mathbb{F}G$. So taking $x=g$ retrieves the $G$-modules action 
$T(g\cdot v)=g \cdot T(v)$.
$\square$

