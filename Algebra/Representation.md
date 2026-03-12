
>[!def]
>A **representation** of an [[Associative Algebra]]  or a **left $A$-module** is a [[vector space]] $V$ equipped with homomorphism $\rho:\: A \to \textrm{End}\: V$.  i.e. a linear map preserving the multiplication and unit.

A **left $A-$module** is a vector space $V$ with *anti*-homomorphism $\rho:A \to \text{End}V$. The two only differ in associativity laws.

A **sub-representation** of a representation $V$ is a subspace $U \subset V$ which is invariant under all operators $\rho(a), \:\:\:a\in A$.  

If $V_{1},V_2$  are two representations of $A$, then the **direct sum** $V_{1} \oplus V_2$ has an obvious structure of a representation of $A$. 


# Irreducibility

A nonzero representation $V$ of $A$ is said to be **irreducible** if its only sub-representations are $0$
and $V$ itself.

It is called **indecomposable** if it cannot be written as a direct sum of two nonzero sub-representations. 

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
