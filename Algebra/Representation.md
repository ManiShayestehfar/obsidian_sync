
>[!info] Definition
>A **representation** of an [[Associative Algebra]]  or a **left $A$-module** is a [[vector space]] $V$ equipped with homomorphism $\rho:\: A \to \textrm{End}\: V$.  i.e. a linear map preserving the multiplication and unit.

A **left $A-$module** is a vector space $V$ with *anti*-homomorphism $\rho:A \to \text{End}V$. The two only differ in associativity laws.

A **sub-representation** of a representation $V$ is a subspace $U \subset V$ which is invariant under all operators $\rho(a), \:\:\:a\in A$.  

If $V_{1},V_2$  are two representations of $A$, then the **direct sum** $V_{1} \oplus V_2$ has an obvious structure of a representation of $A$. 


# Irreducibility

A nonzero representation $V$ of $A$ is said to be **irreducible** if its only sub-representations are $0$
and $V$ itself.

It is called **indecomposable** if it cannot be written as a direct sum of two nonzero sub-representations. 

# Regular Representation

> [!info] Definition
> The (left) **regular representation** of $G$ is the $\mathbb{F}$-vector space $\mathbb{F}G$ that has as its basis the elements of $G$ and the $G$-action is given by left multiplication. Thus
> $$\mathbb{F}G = \left\{\sum_{x\in G}\lambda_x x \;|\; \lambda_x \in \mathbb{F} \right\}$$
> and $g\left(\sum_{x\in G}\lambda_x x \right) = \sum_{x \in G} \lambda_x (gx) = \sum_{y = xg \in G} \lambda_{g^{-1}y}y$ 

- Since the elements of $G$ are a basis for $\mathbb{F}G$, then addition and multiplication in $\mathbb{F}G$ are component-wise operations.


>[!tip] Lemma 1
>The vector space $\mathbb{F}G$ is a $G$-module.


