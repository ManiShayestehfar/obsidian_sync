>[!lemma]
>Suppose that $\mathbb{F}$ is an algebraically closed [[Field|field]] and that $D,E$ are irreducible [[A-Module]]. Then as vector spaces,
>$$\text{Hom}_A(D,E) \cong \begin{cases} \mathbb{F} & \text{if}\:\: D \cong E \\[4pt]
>0 & \text{otherwise}
\end{cases}$$
Moreover, $\text{End}_A(D) \cong \mathbb{F}$. In particular, $A$ is a Schurian [[F-Algebra]].
##### Proof
Split the proof into two parts: when $D \not\cong E$, and $D \cong E$.

For $D\not\cong E$, define $\varphi:D \to E$, where $\varphi \in \text{Hom}_A(D,E)$. By the 1st isomorphism theorem
$$D / \ker \varphi \cong \text{im }\varphi.$$
But since both $D,E$ are irreducible, meaning no proper submodule of $D$ exists:
- $\ker \varphi = 0$ or $D$
- $\text{im }\varphi = E$ or $0$.
Since $\varphi \neq 0$, we must have that $\ker \varphi =0$, and $\text{im }\varphi = E$. Meaning that $\varphi$ is an isomorphism and $D \cong E$. Therefore, if $D \neq E$, then any homomorphism $\varphi$ must be $0$. i.e. $\text{Hom}_A(D,E) = 0$.

--

For $D \cong E$, $\text{Hom}_A(D,E) \cong \text{End}_A(D)$. We want to show that 
$$\text{End}_A(D) = \{\rho_\lambda\:|\: \lambda \in \mathbb{F}\} \cong \mathbb{F}$$
Since $D$ is an $A$-module (and by extension a [[vector space]]), we can find and fix a basis $\{d_1,...,d_n\}$ for it, and let $\varphi \in \text{End}_A(D)$. Then:
$$\varphi(d_i) = \sum_{j}a_{ij}d_j,\quad\quad a_{ij} \in \mathbb{F}.$$
So $\varphi$ is represented by some matrix $(a_{ij})$. Since $F$ is algebraically closed, the matrix has at least one eigenvalue $\lambda \in \mathbb{F}$. Let $v_\lambda$ be the corresponding eigenvector with $\varphi(v_\lambda) = \lambda v_\lambda$.

Define the map $\rho_\lambda: D \to D$,  $\rho_\lambda(d) = \lambda d$. Since $\rho_\lambda$ is an $A$-module map (because scalar multiplication commutes with $A$-action), then $\rho_\lambda \in \text{End}_A(D)$.

Now define $\psi := \varphi - \rho_v$ where $\psi \in \text{End}_A(D)$. Then
$$\psi(v_\lambda) = \varphi(v_\lambda) - \rho_v(v_\lambda) = \varphi(v_\lambda) - \lambda v_\lambda = 0.$$
Since $v_\lambda \neq 0$, this means that $\ker \psi \neq 0$ and so $\ker \psi = D$. This forces $\psi = 0$ and therefore $\varphi \equiv \rho_v$. 
Therefore, every $A$-module endomorphism $\varphi$ is a scalar multiplication defined by $\rho_\lambda$. i.e.  $\text{End}_A(D) = \{\rho_\lambda \:|\: \lambda \in \mathbb{F}\} \cong \mathbb{F}$.

--

Finally, we need to confirm that this is not just a vector space isomorphism but also an $\mathbb{F}$-algebra isomorphism. Let $\rho_\lambda,\rho_\mu \in \text{End}_A(D)$. Then:
- $\rho_\lambda + \rho_\mu = \rho_{\lambda + \mu}$,
- $\rho_\lambda \circ \rho_\mu = \rho_{\lambda\mu}$
since they both act by scalar multiplication. So the map 
$$\mathbb{F}\to \text{End}_A(D),\quad \lambda \mapsto \rho_\lambda$$ is an isomorphism of $\mathbb{F}$-algebras.     $\square$

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
- So there exists $\lambda \in \mathbb{F}$ such that:	$$\rho_a(d) = ad$$
	i.e. $d$ is an eigenvector for *every* $a \in A$.

Since we showed this for every $a$, then *every* vector in $D$ is an eigenvector of *every* $a \in A$.
So $D$ must be a $1$-dimensional vector space, because otherwise there would be a nontrivial linear combination of eigenvectors with different eigenvalues.   $\square$ 



