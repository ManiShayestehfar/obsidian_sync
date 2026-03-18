>[!def]
>An **Associative algebra** or **Algebra $A$** over a field $k$ is a vector space $A$ over $k$ equipped with a multiplication operator  $x,y \to xy$ for $x,y \in A$ with properties:
>
>1. **Associativity:**   $x(yz) = (xy)z$   for $x,y,z \in A$ 
>2. **Bilinearity:**   for $x,x',y,y' \in A$  and  $\alpha \in k$
>
	>- $(x+x')y = xy + x'y$ 
	>- $x(y+y') = xy + xy'$
	>- $(\alpha x)y = x(\alpha y) = \alpha(xy)$
>
There is always a unit such that $1 \cdot x = x \cdot 1 = x$  for all $x \in A$

>[!Unit]
>A **unit** in an associative algebra $A$ is an element $1 \in A$ such that $1a = a1 = a$
>
>-> The unit is unique
>
>**Proof**
>Let $1,1'$ be units, then $1 = 11' = 1'$.


> [!Homomorphism of an Algebras]
> $f:A\to B$ is a linear map such that $f(xy) = f(x)f(y)$ for all $x,y \in A$ and $f(1)= 1$.

>[!tip] Every Associative Algebra is an [[R-Module]] with the added feature of having **bilinear and associative multiplication**.

## Examples

-  $\textrm{End}\:V$ is an associative algebra of linear operators from a vector space $V$ to itself.


# Representations of an Associative Algebra

>[!def]
>A **representation** of an [[Associative Algebra]]  or a **left $A$-module** is a [[vector space]] $V$ equipped with homomorphism $\rho:\: A \to \textrm{End}\: V$.  i.e. a linear map preserving the multiplication and unit.

A **left $A-$module** is a vector space $V$ with *anti*-homomorphism $\rho:A \to \text{End}V$. The two only differ in associativity laws.

A **sub-representation** of a representation $V$ is a subspace $U \subset V$ which is invariant under all operators $\rho(a), \:\:\:a\in A$.  

If $V_{1},V_2$  are two representations of $A$, then the **direct sum** $V_{1} \oplus V_2$ has an obvious structure of a representation of $A$. 


# Irreducibility

A nonzero representation $V$ of $A$ is said to be **irreducible** if its only sub-representations are $0$
and $V$ itself.

It is called **indecomposable** if it cannot be written as a direct sum of two nonzero sub-representations. 
