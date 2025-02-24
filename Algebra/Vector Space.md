
>[!info] Definition
>A **vector space** is a set $V$ together with two operations—**vector addition** and **scalar multiplication**—that satisfy the following axioms. 

Let $F$ be a field. Then $V$ is a vector space over $F$ if the following conditions hold for all vectors $\mathbf{u}, \mathbf{v}, \mathbf{w}$ in $V$ and all scalars $a, b$ in $F$:

1. **Closure under Addition:**  $\mathbf{u} + \mathbf{v} \in V.$
2. **Commutativity of Addition:**  $\mathbf{u} + \mathbf{v} = \mathbf{v} + \mathbf{u}.$
3. **Associativity of Addition:**  $(\mathbf{u} + \mathbf{v}) + \mathbf{w} = \mathbf{u} + (\mathbf{v} + \mathbf{w}).$
4. **Existence of an Additive Identity:**  There exists a zero vector $\mathbf{0}$ in $V$ such that  $\mathbf{u} + \mathbf{0} = \mathbf{u}.$
5. **Existence of Additive Inverses:**  For every $\mathbf{u}$ in $V$, there exists a vector $-\mathbf{u}$ in $V$ such that  $\mathbf{u} + (-\mathbf{u}) = \mathbf{0}.$
6. **Closure under Scalar Multiplication:**  $a\mathbf{u} \in V.$
7. **Compatibility of Scalar Multiplication with Field Multiplication:** $a(b\mathbf{u}) = (ab)\mathbf{u}.$ 
8. **Identity Element of Scalar Multiplication:**  $1\mathbf{u} = \mathbf{u},$  where $1$ is the multiplicative identity in $F$.
9. **Distributivity of Scalar Multiplication over Vector Addition:**  $a(\mathbf{u} + \mathbf{v}) = a\mathbf{u} + a\mathbf{v}.$
10. **Distributivity of Scalar Multiplication over Field Addition:** $(a + b)\mathbf{u} = a\mathbf{u} + b\mathbf{u}.$ 


## F-Vector Space Homomorphism

Let $\mathbb{F}$ be a field. Let $V$ and $W$ be  $\mathbb{F}$-vector spaces. Then a **$\mathbb{F}$-vector space homomorphism** is a map $\varphi: V \to W$  is a homomorphism of abelian groups that commutes with the $\mathbb{F}$-[[R-Module|action]]. That is,
- $\varphi(v + v') = \varphi(v) + \varphi(v')$, 
- $\varphi(\lambda v) = \lambda \varphi(v)$        for all $\lambda \in \mathbb{F}$ and $v,v'\in V$.


>[!theorem 1.1 (The Isomorphism Theorems)]  
>
