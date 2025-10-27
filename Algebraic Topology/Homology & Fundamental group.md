Recall that $H_0(X) \cong \mathbb{Z}^{\#\text{ of path-components of }X}$.

For $f:I \to X$, we can view it as 
1. a singular 1-simplex
2. path in $X$
If $f$ is a loop, $f(0) = f(1)\implies \partial f = f(1)-f(0) = 0\implies f \in \ker \partial$ is a cycle

>[!def] Commutator
>For a group $G$, the **commutator** of a  group, denoted $[G,G]$ is a subgroup $$[G,G]:= \{g^{-1}h^{-1}gh\:\:\:\: \forall g \in G. h \in G\}$$

>[!Theorem]
>$[G,G]$ is the smallest normal subgroup $H$ of $G$ such that $G/H$ is abelian.

>[!def] Abelianisation of $G$
>The **abelianisation of $G$**, denoted $G^{ab}$ is $G/[G,G]$ 

>[!Theorem] 
>Any homomorphism $\phi:G \to H$ with $H$ abelian can be factored through $\phi': G^{ab}\to H$.


>[!Theorem] H Theorem 2.A.1
>a. 