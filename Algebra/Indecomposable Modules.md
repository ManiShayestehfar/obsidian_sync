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


## Lemma

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


# Krull-Schmidt

>[!theorem] Krull-Schmidt Theorem
>Let $V$ be an $A$-module such that $V \cong M_1 \oplus \cdots \oplus M_r$ and $V \cong N_1 \oplus \cdots \oplus N_s$ where each $M_i,N_j$ are indecomposable. 
>Then $r=s$, and after relabelling, $M_i \cong N_i$.

##### Proof
![[Indecomposable Modules-1767786640178.png]]
$\color{red} \text{REDO THIS PROOF}$


# Principal Indecomposable A-modules (PIM)

>[!definition] 
>The **principal indecomposable** $A$-modules are the indecomposable direct summands $P_1,...,P_t$ of $A$.



# Idempotents

- An **idempotent** is a nonzero element $e \in A$ such that $e^2=e$
- Two idempotents $f,g$ are **orthogonal** if $fg=gf=0$
- An idempotent $e$ is **primitive** if it cannot be written as sum of two orthogonal idempotents

## Example

$A = \text{Mat}_2(\mathbb{F})$. Set $$e = \begin{pmatrix}1 & 0 \\ 0 & 0\end{pmatrix},\quad f=\begin{pmatrix}0 & 0 \\ 0 & 1\end{pmatrix}$$
Then $e,f$ are orthogonal and $1_A= e+f$. Also $e,f$ are both primitive. 

## Lemma

>[!lemma] Lemma 8C
>1. Suppose $e$ is an idempotent in $A$. Then $Ae$ is indecomposable $\iff$ $e$ is primitive
>2. Suppose $P$ is a principal indecomposable $A$-module. Then $P=Ae$ for some primitive idempotent $e$.
>3. Suppose $e,f$ are orthogonal idempotents. Then $A(e+f)=Ae\oplus Af$

##### Proof
###### 1. $(\Rightarrow)$
Assume $e$ is not primitive, then $e = e_1 + e_2$ such that $e_1e_2=e_2e_1=0$. Then for $a \in A$
1. $ae = a(e_1+e_2)=ae_1+ae_2 \in Ae_1 + Ae_2$.
   So $A_e \subseteq Ae_1 + Ae_2$. The reverse is clear as $e_1,e_2 \in Ae$. Hence $Ae=Ae_1+Ae_2$.
2. If $x \in Ae_1\cap Ae_2$, write $x = ae_1=be_2$. But $x = xe_1 = (be_2)e_1=b(e_2e_1)=0$ so $x=0$ and so $Ae_1 \cap Ae_2 = 0$. 
Thus $Ae = Ae_1 \oplus Ae_2$.  $\square$

$(\Leftarrow)$
TBD
