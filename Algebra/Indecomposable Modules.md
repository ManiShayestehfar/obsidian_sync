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
Let $\mathfrak{m}$ be a maximal ideal of $\text{End}_A(P)$.
Let $\psi\not\in \mathfrak{m}$.
Since $\mathfrak{m}$ is proper, then $1_P=a\psi + \varphi$ for $a \in \text{End}_A(P)$ and $\varphi \in \mathfrak{m}$.
By Fitting's lemma $\text{End}_A(P) = \text{im }\varphi^n \oplus \ker\varphi^n$ for some $n>0$. Since $P$ is indecomposable by assumption, then $\text{im }\varphi^n=0$ or $\ker \varphi^n=0$. 
Since $\mathfrak{m}$ is a proper ideal and $\varphi \in \mathfrak{m}$, then $\varphi^n$ cannot be an isomorphism, hence non-injective (it is surjective since $\varphi^n \in \text{End}_A(P)$) so $\ker \varphi^n \neq 0$. Thus $\text{im }\varphi^n=0$. i.e. $\varphi^n = 0$.
$$(1+\varphi + \cdots +\varphi^{n-1})a\psi = (1+\varphi + \cdots +\varphi^{n-1})(1-\varphi)= 1 - \varphi^n = 1$$
Thus $\psi$ is invertible and so we have shown that any $\psi \in \text{End}_A(P)\setminus \mathfrak{m}$ is invertible, thus it must generate $\text{End}_A(P)$. 
This implies that $\mathfrak{m}$ is unique because if $\mathfrak{m}'\neq \mathfrak{m}$ was another maximal ideal, then $\psi \in \mathfrak{m}' \setminus \mathfrak{m}$ would be an element of $\text{End}_A(P) \setminus \mathfrak{m}'$ that was not invertible. A contradiction.

We need to show that $\mathfrak{m} = \{\varphi\in \text{End}_A(P)\:|\: \varphi^n=0\quad \exists n>0\}$.
By the argument above it is clear that $\mathfrak{m}\subseteq \{\varphi\in \text{End}_A(P)\:|\: \varphi^n=0\quad \exists n>0\}$.
To show the reverse inclusion, it is enough to show that if $\psi \not\in \mathfrak{m}$, then $\psi^n \neq 0$. 
From before if $\psi \not\in \mathfrak{m}$, then $\psi$ is invertible $\implies$ $\psi$ is not nilpotent. So $\mathfrak{m} = \{\varphi\in \text{End}_A(P)\:|\: \varphi^n=0\quad \exists n>0\} \subseteq \mathfrak{m}$. 
$\square$

