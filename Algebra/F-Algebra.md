>[!def]
>A (unital) **$\mathbb{F}$-Algebra** is a [[ring]] $R$ with identity element $1_R$ which is also a $\mathbb{F}$-vector space w.r.t addition in $R$.
>
>--> An $\mathbb{F}$-algebra is a ring with its *coefficients* in $\mathbb{F}$. 
>
>A **finite dimensional $\mathbb{F}$-algebra** is an $\mathbb{F}$-algebra that is finite dimensional as an $\mathbb{F}$-vector space.

## Examples

- $\mathbb{F}G$ is an $\mathbb{F}$-algebra
- So is $\text{Mat}_n(\mathbb{F})$

# $\mathbb{F}$-Algebra Homomorphism

>[!def]
>An $\mathbb{F}$-Algebra **homomorphism** is a [[Vector Space]] homomorphism $\varphi: A \to B$ that is also a ring homomorphism.

- Two algebras are **isomorphic** if there is a bijective algebra homomorphism between them


# Irreducibility

- An $\mathbb{F}$-algebra $A$ is **semisimple** if the [[Representation|regular representation]] of $A$, which is the algebra $A$ considered as an $A$-module, is semisimple.


# Schurian $\mathbb{F}$-Algebra

>[!def] 
>An $\mathbb{F}$-Algebra, $A$, is **Schurian** if $\text{End}_A(D) \cong F$, for all simple $A$-modules $D$. 


# Opposite Algebra

>[!def] 
>Let $B$ be an $\mathbb{F}$-algebra. The **opposite algebra** of $B$ is the $\mathbb{F}$-algebra $B^{op}$ that is equal to $B$ as an $\mathbb{F}$-vector space but with multiplication $a\cdot b = ab$ where the multiplication on the left-hand is in $B^{op}$ and multiplication on the right-hand side is in $B$.

## Some Properties

>[!lemma] 
>Let $A$ be an $\mathbb{F}$-algebra. Then $A \cong \text{End}_A(A)^{op}$.
>Also if we consider $A$ as a *right* $A$-module then the statement becomes $A \cong \text{End}_A(A)$.

![[F-Algebra-1753017145112.png]]

>[!lemma]
>Suppose $V \cong U_1 \oplus U_2 \oplus \cdots \oplus U_r$ for some $A$-modules $U_1,...,U_r$. Then
>$$\text{End}_A(V) = \{(\varphi_{il})\:|\: \varphi_{il} \in \text{Hom}_A(U_i, U_l)\:\:\text{for}\:\: 1\leq i,l\leq r\}$$
>


# Artin-Wedderburn Decomposition

>[!thm]
>Let $\mathbb{F}$ be a field and suppose that $A$ is a semisimple Schurian $\mathbb{F}$-algebra. Let $d_1,...,d_t$ be the dimensions of the irreducible $A$-modules, counted up to isomorphism. Then 
>$$A \cong \text{Mat}_{d_1}(\mathbb{F}) \oplus \cdots \oplus \text{Mat}_{d_t}(\mathbb{F})$$ 

