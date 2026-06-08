> [!lemma] Schur's Lemma  
> Suppose that $\mathbb{F}$ is an algebraically closed [[Field|field]], and let $D$ and $E$ be irreducible [[A-Module|$A$-modules]]. Then, as vector spaces,  
> $$  
> \operatorname{Hom}_A(D,E) \cong  
> \begin{cases}  
> \mathbb{F}, & \text{if } D \cong E, \\[4pt]  
> 0, & \text{otherwise}.  
> \end{cases}  
> $$  
> Moreover, $\operatorname{End}_A(D) \cong \mathbb{F}$. More generally, if $\mathbb{F}$ is not algebraically closed, then $\operatorname{End}_A(D)$ is a division algebra over $\mathbb{F}$.
##### Proof
###### Part 1: The case $D \not\cong E$

Let $\varphi \in \operatorname{Hom}_A(D,E)$. Since $\varphi$ is an $A$-module homomorphism, $\ker \varphi$ is a submodule of $D$, and $\operatorname{im} \varphi$ is a submodule of $E$.

Because $D$ and $E$ are irreducible, their only submodules are the trivial submodule and the whole module. Hence $\ker \varphi$ is either $0$ or $D$, and $\operatorname{im} \varphi$ is either $0$ or $E$.

Suppose, for contradiction, that $\varphi \neq 0$. Then $\ker \varphi \neq D$, so $\ker \varphi = 0$. Similarly, $\operatorname{im} \varphi \neq 0$, so $\operatorname{im} \varphi = E$. Therefore $\varphi$ is both injective and surjective, and hence $\varphi$ is an $A$-module isomorphism $D \cong E$.

This contradicts the assumption that $D \not\cong E$. Therefore every $A$-module homomorphism $\varphi : D \to E$ must be zero, and so $\operatorname{Hom}_A(D,E)=0$.

###### Part 2: The case $D \cong E$

If $D \cong E$, then $\operatorname{Hom}_A(D,E) \cong \operatorname{End}_A(D)$ as vector spaces. Hence it remains to show that $\operatorname{End}_A(D) \cong \mathbb{F}$.

*Eigenvalue argument:*
Let $\varphi \in \operatorname{End}_A(D)$. Since $D$ is a finite-dimensional vector space over $\mathbb{F}$, and since $\mathbb{F}$ is algebraically closed, the linear map $\varphi : D \to D$ has an eigenvalue $\lambda \in \mathbb{F}$. Choose a corresponding non-zero eigenvector $v \in D$, so that $\varphi(v)=\lambda v$.

*Eigenvalue map construction:*
Define $\rho_\lambda : D \to D$ by $\rho_\lambda(d)=\lambda d$ for all $d \in D$. This is an $A$-module homomorphism because scalar multiplication commutes with the $A$-action. Thus $\rho_\lambda \in \operatorname{End}_A(D)$.

*Equivalence of the two maps:*
Now consider $\psi := \varphi - \rho_\lambda$. Since both $\varphi$ and $\rho_\lambda$ are $A$-module endomorphisms of $D$, we have $\psi \in \operatorname{End}_A(D)$. Moreover,  
$$  
\psi(v) =\varphi(v)-\rho_\lambda(v)= \lambda v-\lambda v =0
$$

Since $v \neq 0$, it follows that $\ker \psi \neq 0$. But $\ker \psi$ is a submodule of $D$, and $D$ is irreducible. Hence $\ker \psi = D$. Therefore $\psi = 0$, so $\varphi = \rho_\lambda$.

Thus every $A$-module endomorphism of $D$ is scalar multiplication by some $\lambda \in \mathbb{F}$. Therefore  
$$  
\operatorname{End}_A(D) = \{{\rho_\lambda : \lambda \in \mathbb{F}}\} \cong \mathbb{F}.  
$$
*Isomorphism of F-algebras:*
Finally, the map $\mathbb{F} \to \operatorname{End}_A(D)$ given by $\lambda \mapsto \rho_\lambda$ is an $\mathbb{F}$-algebra isomorphism. Indeed, for $\lambda,\mu \in \mathbb{F}$, we have $\rho_\lambda+\rho_\mu=\rho_{\lambda+\mu}$, $\rho_\lambda \circ \rho_\mu=\rho_{\lambda\mu}$, and $\rho_1=\operatorname{id}_D$.

Hence $\operatorname{End}_A(D) \cong \mathbb{F}$ as $\mathbb{F}$-algebras. Consequently, if $D \cong E$, then $\operatorname{Hom}_A(D,E) \cong \mathbb{F}$ as vector spaces.

Hence
$$  
\operatorname{Hom}_A(D,E) \cong  
\begin{cases}  
\mathbb{F}, & \text{if } D \cong E, \\[4pt]  
0, & \text{otherwise}.  
\end{cases}  
$$

$\square$



# Some Properties

>[!corollary]
>Suppose $A$ is a commutative Schurian $\mathbb{F}$-algebra. Then every irreducible $A$-module is one dimensional.
##### Proof
Suppose $D$ is an irreducible $A$-module. For each $a \in A$ we define a map $\rho_a: D\to D$ such that $\rho_a(d) = ad$ for all $d \in D$.
In order for $\rho_a$ to be an $A$-module homomorphism, it must satisfy
$$\rho_a(bd) = b\rho_a(d),\quad \quad \forall\: b \in A, d \in D$$
This is shown using associativity and commutativity of $A$:
$$\rho_a(bd) = a(bd) = (ab)d = (ba)d = b(ad) = b \rho_a(d).$$
Hence, $\rho_a$ is an $A$-module homomorphism. 

Since $D$ is irreducible and $A$ is Schurian, then by Schur's Lemma: $\text{End}_A(D) \cong \mathbb{F}$. i.e.
- Every $A$-module endomorphism $\rho_a$ is just scalar multiplication
- So there exists $a \in \mathbb{F}$ such that:	$$\rho_a(d) = ad$$
	i.e. $d$ is an eigenvector for *every* $a \in A$.

Since we showed this for every $a$, then *every* vector in $D$ is an eigenvector of *every* $a \in A$.
So $D$ must be a $1$-dimensional vector space, because otherwise there would be a nontrivial linear combination of eigenvectors with different eigenvalues.   $\square$ 



