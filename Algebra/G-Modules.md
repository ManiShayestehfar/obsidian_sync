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
>Let $V$ be an $n$-dimensional $G$-module. Then $V$ determines a representation $\rho_V: G\to GL_n(\mathbb{F})$. Conversely, if $\rho:G \to GL_{n}(\mathbb{F})$ is a group homomorphism the $V = \mathbb{F}^n$ becomes a $G$-module by defining the action of $g \in G$ on $V$ to be given by matrix multiplication by $\rho(g)$.
 
![[Screenshot 2025-03-06 at 12.50.18 pm.png]]
![[Screenshot 2026-02-26 at 11.41.00 am.png]]

**Remark:** $\text{im } \rho_{V}^{E} = A^{-1}\text{im } \rho_{V}^{F}A$  are conjugate subgroups of $GL_n(\mathbb{F})$



## FG-Module Examples

1. $G = GL_n(\mathbb{F}) = \{\text{invertible}\:\: n \times n \:\:\text{matrices made of}\:\: \mathbb{F}\}$ 
The natural representation is 
$$V = \mathbb{F}^n = \left\{\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix}\:\Bigg|\: \lambda_i \in \mathbb{F}\right\} 
$$
If $A = (a_{ij}) \in G$, then $A\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix}$ is given by matrix multiplication

2. $G = S_n = \text{symmetric group of permutation of}\:\:\{1,2,...,n\}$. 
$V = \mathbb{F}^n$ with $S_n$-action
$$a\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix} := \begin{pmatrix}\lambda_{a(1)} \\ \vdots \\ \lambda_{a(n)}\end{pmatrix}$$



## G-Module Homomorphism & Isomorphisms

- Let $V,W$ be $G-$modules.

> [!info] G-Module Homomorphism
> A **$G-$Module Homomorphism** is a linear transf. $\phi : V \to W$ that commutes with the $G-$action. i.e. $\phi(gv) = g\phi(v)$ for all $g\in G$, $v\in V$.

> [!info] G-Module Isomorphism
> A **$G-$Module Isomorphism** is a bijective $G-$module homomorphism, $\phi : V \to W$ that commutes with the $G-$action. i.e. $\phi(gv) = g\phi(v)$ for all $g\in G$, $v\in V$. We write $V\cong W$. 

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
>2. $gw \in W$ for all $w \in W$ and all $g \in G$
>   
>   Every submodule $W$ of a $G-$module is by definition a $G-$module.


> [!lemma]
> ![[Pasted image 20250306222032.png]]
##### Proof for a)
1.  Clearly $\ker\varphi \subset V$ 
2. Let $g \in G$. $\varphi(vg) = g\varphi(v) = g\cdot 0 = 0$ and so $vg \in \ker \varphi$, where the choice of $v$ and $g$ were arbitrary.    $\square$ 
##### Proof for b)
1. $\text{im}\:\phi \subset W$   
2. Let $w = \varphi(v)$ for $v \in V$ and $w \in W$. And $gw = g\varphi(v) = \varphi(gv) \in \text{im}\: W$ for all $g \in G$ and so $gw \in \text{im }W$.     $\square$ 

---
# Irreducible G-modules

>[!def]
>A $G$-module $V$ is **irreducible** if it contains no proper nonzero submodules. i.e its only submodules are $0$ and $V$.
>
>Otherwise, $V$ is **reducible**.
>
>A $G$-module $V$ is **completely reducible**, or **semisimple**, if it is isomorphic to a direct sum of irreducible $G$-modules.

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
>With the natural multiplication defined, $\mathbb{F}G$ is an associative ring with $1_G$ as identity. The natural multiplication comes from a natural multiplication in $G$:
>
>![[Screenshot 2025-03-13 at 11.41.14 am.png]]
#### Proof
![[Screenshot 2025-03-13 at 11.42.54 am.png]]


>[!success] NOTE
>$\mathbb{F}G$  is both an $\mathbb{F}$-[[Vector Space]], and a [[Ring]]

---

# Maximal submodules of $\mathbb{F}G$

>[!Proposition]
>Let $D$ be an irreducible $G$-module. Then there exists a maximal proper $G$-submodule $M$ of $\mathbb{F}G$ such that $D \cong \mathbb{F}G/M$ as $G$-modules.
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
>Let $V$ be an $\mathbb{F}$-vector space. Then $V$ is an $A$-module if and only if there is an algebra homomorphism $\Phi: A \to \text{Mat}_n(\mathbb{F}),\quad a \mapsto \varphi_a$ such that $a \cdot v = \varphi_a(v)$.
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


>[!proposition|2]
>Let $G$ be a finite group and $\mathbb{F}$ a field
>1. Every $G$-module is an $\mathbb{F}G$-module
>2. Every $\mathbb{F}G$-module is a $G$-module
>3. Let $V$ and $W$ be $G$-modules of $\mathbb{F}G$-modules. Then $V \cong W$ as $G$-modules $\iff\: V \cong W$ as $\mathbb{F}G$-modules.

##### Proof 
###### 1. 
By Prop above, $V$ is an $\mathbb{F}G$-module if and only if there is an algebra homomorphism $\mathbb{F}G\to \text{Mat}_n(\mathbb{F})$ with $n = \dim V$.
$\implies$ a group homomorphism $G \to GL_n(\mathbb{F})$, because $1_G = g\cdot g^{-1}$
$\implies I_n = \Phi(1_{\mathbb{F}G}) = \Phi(g\cdot g^{-1}) = \Phi(g)\Phi(g^{-1})$
$\implies \Phi(g) \in GL_n(\mathbb{F})$ 
$\square$

###### 2.
We have $G$-module homomorphism $\varphi(gv) = g\varphi(v)$ since $G$ is a basis of $\mathbb{F}G$.
Then $V \cong W$ as $G$-modules $\iff V\cong W$ as $\mathbb{F}G$-modules. $\square$

>[!Remark]
>If $V,W$ are $G$-modules and $\varphi:V \to W$ is a $G$-module homomorphism, then we can consider $\varphi$ as an $\mathbb{F}G$-module homomorphism.



