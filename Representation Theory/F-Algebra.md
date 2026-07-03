# Definitions

> [!def] Unital $\mathbb{F}$-Algebra
> Let $\mathbb{F}$ be a field. A **unital $\mathbb{F}$-algebra** is a tuple $(A, +, \cdot, \star)$ where:
> 
> - $(A, +, \cdot)$ is a **unital ring** with additive identity $0_A$ and multiplicative identity $1_A$, and
> - $(A, +, \star)$ is an **$\mathbb{F}$-vector space** with respect to the same addition $+$,
> 
> such that the scalar multiplication $\star : \mathbb{F} \times A \to A$ is **compatible** with the ring multiplication in the sense that:
> $$\lambda \star (a \cdot b) = (\lambda \star a) \cdot b = a \cdot (\lambda \star b) \qquad \forall\, \lambda \in \mathbb{F},\ \forall\, a, b \in A.$$

> [!def] Equivalent Formulation
> Equivalently, $A$ is a unital $\mathbb{F}$-algebra if and only if there exists a **unital ring homomorphism**
> $$\varphi : \mathbb{F} \longrightarrow Z(A),$$
> where $Z(A) := \{ z \in A : za = az\ \forall\, a \in A \}$ is the **centre** of $A$, such that scalar multiplication is recovered by:
> $$\lambda \star a := \varphi(\lambda) \cdot a \qquad \forall\, \lambda \in \mathbb{F},\ \forall\, a \in A.$$

> [!def] Finite-Dimensional $\mathbb{F}$-Algebra
> A unital $\mathbb{F}$-algebra $A$ is **finite-dimensional** if $A$, regarded as an $\mathbb{F}$-vector space, satisfies:
> $$\dim_{\mathbb{F}}(A) < \infty.$$
> That is, there exists a finite basis $\{e_1, \ldots, e_n\} \subset A$ such that every $a \in A$ has a unique representation
> $$a = \sum_{i=1}^{n} \alpha_i\, e_i, \qquad \alpha_i \in \mathbb{F}.$$
> The integer $n = \dim_{\mathbb{F}}(A)$ is called the **dimension** of the algebra.

## Examples

- $\mathbb{F}G$ is an $\mathbb{F}$-algebra.
	  For $\lambda \in \mathbb{F}$ and $a = \sum_{g \in G} \lambda_g g \in \mathbb{F}G$, then  $\lambda a = \sum_{g \in G}\lambda \cdot \lambda_g g$ 
- $\text{Mat}_n(\mathbb{F})$ is an $\mathbb{F}$-algebra
	  $M,N \in \text{Mat}_n(\mathbb{F})$ where $M+N$ and $\lambda N$ is natural and $MN$ is matrix mult.
- $\text{End}_\mathbb{F}(V)$is also similar to above except here you just fix a basis.
- $\mathbb{C}$ is a $\mathbb{C}$-algebra where $\mathbb{C} = \mathbb{R} \oplus \mathbb{R}i$ as $\mathbb{R}$-algebras.
- If $A_1,A_2,...,A_n$ are $\mathbb{F}$-algebras (with ones), then $A = A_1 \oplus ... \oplus A_n$ is an $\mathbb{F}$-algebra. You can check that all necessary criteria hold

# $\mathbb{F}$-Algebra Homomorphism

>[!defintion]
>An $\mathbb{F}$-Algebra **homomorphism** is a [[Vector Space]] homomorphism $\varphi: A \to B$ that is also a ring homomorphism.

- Two algebras are **isomorphic** if there is a bijective algebra homomorphism between them


# Irreducibility

>[!Definition]
>- An $\mathbb{F}$-algebra $A$ is **semisimple** if the [[Representation|regular representation]] of $A$, which is the algebra $A$ considered as an $A$-module, is semisimple.
> 	 - Equivalently, $A$ is **semisimple** if $\text{Rad }A=0$
> - An $\mathbb{F}$-algebra $A$ is **completely reducible** if it is a direct sum of irreducible $A$-modules

# Schurian $\mathbb{F}$-Algebra

>[!def] 
>An $\mathbb{F}$-Algebra, $A$, is **Schurian** if $\text{End}_A(D) \cong \mathbb{F}$, for all simple $A$-modules $D$. 

## Examples

1. If $\mathbb{F}$ is algebraically closed, then by Schur's lemma, $\text{End}_A(D) \cong \mathbb{F}$ for $D$ irreducible $A$-modules. This means that every irreducible $A$-module is Schurian, which implies $A$ is Schurian
2. $\mathbb{F}G$ is Schurian if $\mathbb{F}$ is algebraically closed
3. For $C_4 =\langle x | x^4=1\rangle$ acting on $V = \mathbb{R}^2$ via $x \mapsto \left[\begin{smallmatrix}0 & 1 \\ -1 & 0\end{smallmatrix}\right]$. $\text{End}_{\mathbb{R}G}(V) \cong \mathbb{C}$ (shown in Tutorial 3) and $V$ is irreducible. Hence $V$ is NOT Schurian
4. For $G=S_n$ and $\mathbb{F}$ any field, then $\mathbb{F}S_n$ is Schurian (not obvious)
5. If $p = \text{char } \mathbb{F}$ and $p=0$ or $p \nmid |G|$, then $\mathbb{F}G$ is completely reducible by [[Maschke's Theorem]].

# Opposite Algebra

>[!definition] 
>Let $B$ be an $\mathbb{F}$-algebra. The **opposite algebra** of $B$ is the $\mathbb{F}$-algebra $B^{op}$ that is equal to $B$ as an $\mathbb{F}$-vector space but with multiplication $a\cdot b = ba$ where the multiplication on the left-hand is in $B^{op}$ and multiplication on the right-hand side is in $B$.


## Some Properties

>[!lemma] 
>Let $A$ be an $\mathbb{F}$-algebra. Then $A \cong \text{End}_A(A)^{op}$.
>Also if we consider $A$ as a *right* $A$-module then the statement becomes $A \cong \text{End}_A(A)$.
##### Proof
Notice that if $\varphi \in \text{End}_A(A)^{op}$, then $\varphi(a) = \varphi(a \cdot 1_A) = a \varphi(1_A)$, for $a \in A$. 
So $\varphi$ is uniquely determined by $\varphi(1_A)$.

Define a map $\Theta: \text{End}_A(A)^{op}\to A$ by $\Theta(\varphi) = \varphi(1_A)$. 
$\Theta$ is $\mathbb{F}$-linear because 
$$\Theta(r\varphi+s \psi) = (r\varphi + s \psi)(1_A) = r\varphi(1_A)+s \psi(1_A) = r\Theta(\varphi) + s\Theta(\psi)$$
for all $r,s \in \mathbb{F}$ and $\varphi,\psi \in \text{End}_A(A)$. 

$\Theta$ is also a ring homomorphism because
$$\Theta(\varphi\psi) = (\varphi\psi)(1_A) = \varphi(\psi(1_A)) = \varphi(\psi(1_A)\cdot 1_A)= \psi(1_A)\varphi(1_A) = \Theta(\psi)\Theta(\varphi),$$
where the third equality comes from the fact that $\varphi$ is an $A$-module homomorphism (so $\varphi(ab)=a \varphi(b)$ for $a,b \in A$).

*Injectivity:* $\Theta(\varphi)=0 \iff \varphi(1_A)=0$. Hence if $a \in A$, then $\varphi(a)=\varphi(a\cdot 1_A) = a \varphi(1_A)=0$ so $\varphi$ is identically zero. Thus $\Theta$ is injective.

*Surjectivity:* Fix $a \in A$ and define a map $\rho_a: A \to A$ by $\rho_a(x) = xa$ for $x \in A$.
Then $\rho_a$ is $\mathbb{F}$-linear since multiplication in $A$ is linear. 
$\rho_a(xy)=(xy)a=x(ya) = x\rho_a(y)$ for $x,y \in A$.
Hence $\rho_a \in \text{End}_A(A)^{op}$.
By definition $\Theta(\rho_a)=a$, so $\Theta$ is surjective.
$\square$

