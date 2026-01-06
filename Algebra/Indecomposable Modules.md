# Decomposable vs Indecomposable

>[!def]
>An [[A-Module|$A$-module]] $V$ is
>- **decomposable:** there exists $U \subset V$  such that $V = U \oplus W$
>- **indecomposable:** not decomposable


# Fitting's Lemma

>[!lemma] Fitting's Lemma
>Suppose $V$ is an $A$-module and $\varphi: V \to V$ is a module homomorphism. Then $$V = \ker \varphi^n \oplus \text{im }\varphi^n$$ 
>for some $n > 0$.
##### Proof
Note that $\ker \varphi \subseteq \ker \varphi^2 \subseteq \cdots \subseteq V$. Hence since $V$ is a finite dimensional module, then there exists $n>0$ such that $\ker \varphi^n=\ker \varphi^{n+1}=\cdots$ (we could also use a Noetherianity argument). 
Consider $\varphi^n$ as a homomorphism from $\text{im }\varphi^n \to \text{im }\varphi^{2n}$.
- If $x \in \text{im }\varphi^n$, then $x = \varphi^n(x')$ for some $x' \in V$. 
- Also if $x \in \ker \varphi^n$, then $\varphi^{2n}(x') = \varphi^n(x)=0$ so that $x' \in \ker \varphi^{2n}= \ker \varphi^n$ 
These imply that $x = \varphi^n(x') = 0 \implies \ker\varphi^n \cap \text{im }\varphi^n= 0$ . Thus $\varphi^n:\text{im }\varphi^n\to\text{im }\varphi^{2n}$ is an isomorphism. 

Since $\varphi^n$ is an isomorphism then if $x \in V$, then there exists a unique $y \in V$ such that $\varphi^n(x) = \varphi^{2n}(y)$. 
Write $x = (x-\varphi^n(y))+\varphi^n(y)$. Then
- clearly $\varphi^n\in \text{im }\varphi^n$,
- $\varphi^n(x-\varphi^n(y))=\varphi^n(x) - \varphi^{2n}(y)=0$ so $x-\varphi^n(y)\in \ker\varphi^n$.

Since we showed that $\ker\varphi^n \cap \text{im }\varphi^n= 0$, then $V = \ker\varphi^n \oplus \text{im }\varphi^n$.   $\square$


# Lemma

>[!lemma]
>Suppose $P$ is an indecomposable $A$-module. Then $\text{End}_A(P)$ is a local ring with a maximal proper ideal
>$$\mathfrak{m} = \{\varphi\in \text{End}_A(P)\:|\: \varphi^n=0\quad \exists n>0\}$$

##### Proof
