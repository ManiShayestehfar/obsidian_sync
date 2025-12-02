
>[!lemma]
>Suppose $V \cong U_1 \oplus U_2 \oplus \cdots \oplus U_r$ for some $A$-modules $U_1,...,U_r$. Then
>$$\text{End}_A(V) = \{(\varphi_{il})\:|\: \varphi_{il} \in \text{Hom}_A(U_i, U_l)\:\:\text{for}\:\: 1\leq i,l\leq r\}$$
>


# Artin-Wedderburn Decomposition

>[!Theorem]
>- $\mathbb{F}$ is a field,
>- $A$ is a *semisimple Schurian* $\mathbb{F}$-algebra. 
>- $d_1,...,d_t$ be the dimensions of the irreducible $A$-modules, counted up to isomorphism.
>Then $$A \cong \text{Mat}_{d_1}(\mathbb{F}) \oplus \cdots \oplus \text{Mat}_{d_t}(\mathbb{F})$$ 
##### Proof
[ENTER PROOF]


>[!corollary] 
>Suppose $\mathbb{F}G$ is Schurian, where $\mathbb{F}$ is a field of characteristic $p$ such that $p \nmid |G|$. Let $d_1,d_2,...,d_t$ be the dimensions of the irreducible $\mathbb{F}G$-modules, counted up to isomorphism. Then $|G|= d_1^2+\cdots +d_t^2$.
##### Proof

By [[Maschke's Theorem]] $\mathbb{F}G$ is a semisimple $\mathbb{F}$-algebra. Hence, this follows by taking dimensions on both sides of the Artin-Wedderburn decomposition of $\mathbb{F}G$. 


>[!proposition]
>If $A$ is a semisimple $\mathbb{F}$-algebra, and $V$ is an $A$-module, then $V$ is a semisimple $A$-module. 
##### Proof

We know $A = D_1 \oplus D_2 \oplus \cdots \oplus D_r$ as a direct some of irreducible submodules. Then
$$V = AV = \{av \:|\: a \in A, v \in V\} = D_1V + \cdots D_rV$$
Pick a basis $\{e_1,..,e_n\}$ for $V$, and let $1 \leq a \leq n$ and $1 \leq i \leq r$.
Then $D_i e_a = \{de_a \:|\: d \in D_i\}$ is a submodule of $V$ as it is a vector subspace of $V$ closed under left multiplication by $A$. 
If $D_ie_a\neq 0$, then $D_i \cong D_ie_a$ by Schur's lemma as there is an nonzero $A$-homomorphism from $d \mapsto de_a$. Thus $V = D_1 + D_2 + \cdots D_r$.

This is *a priori* not a direct sum, but If $D,D'$ are irreducible submodules of $V$, then either $D = D'$ or $D \cap D' = 0$. Therefore we can indeed write $V = D_1 \oplus D_2 \oplus \cdots \oplus D_r$. $\square$

**Remark:** the proof relies on the fact that we can view $A$ as both an algebra and an $A$-modules.



 
