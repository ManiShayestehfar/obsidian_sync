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