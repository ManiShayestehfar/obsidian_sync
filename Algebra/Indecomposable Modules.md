# Decomposable vs Indecomposable

>[!def]
>An $A$-module $V$ is
>- **decomposable:** there exists $U,W \subset V$  such that $V = U \oplus W$
>- **indecomposable:** not decomposable

## Examples

1. Trivial submodules are indecomposable
2. Any irreducible module $D$ is indecomposable
3. $G = S_n, V = \mathbb{F}^n \implies$$$\begin{cases}
V = I \oplus W & \text{char} \mathbb{F} \nmid n  \\[3pt]
V \text{ is indecomp. } & \text{char} \mid n \end{cases}$$

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

>[!Definition]
>- An **idempotent** is a nonzero element $e \in A$ such that $e^2=e$
>- Two idempotents $f,g$ are **orthogonal** if $fg=gf=0$
>- An idempotent $e$ is **primitive** if it cannot be written as sum of two orthogonal idempotents

## Example

$A = \text{Mat}_2(\mathbb{F})$. Set $$e = \begin{pmatrix}1 & 0 \\ 0 & 0\end{pmatrix},\quad f=\begin{pmatrix}0 & 0 \\ 0 & 1\end{pmatrix}$$
Then $e,f$ are orthogonal and $1_A= e+f$. Also $e,f$ are both primitive. 

## Lemma

>[!Lemma]
>Every $A$-module is a direct sum of indecomposable modules
##### Proof
Let $V$ be an $A$-module. If $V$ is indecomposable then we are done. Otherwise $V = X \oplus Y$ for some $X,Y$ proper submodules.
Then $\dim X , \dim Y \leq \dim V$. By repeating this argument, we can write $X$ and $Y$ as direct sums of indecomposables.
Hence $V$ is a direct sum of indecomposables.  $\square$


>[!lemma] Lemma 8C
>1. Suppose $e$ is an idempotent in $A$. Then $Ae$ is indecomposable $\iff$ $e$ is primitive
>2. Suppose $P$ is a principal indecomposable $A$-module. Then $P=Ae$ for some primitive idempotent $e$.
>3. Suppose $e,f$ are orthogonal idempotents. Then $A(e+f)=Ae\oplus Af$

##### Proof

###### 3. $(\Rightarrow)$
$(\subseteq)$
$a(e+f) = ae+af \in Ae \oplus Af$ where $Ae \cap Af= 0$ since $ef=fe=0$.

$(\supseteq)$
Take $x \in Ae$ and $y \in Af$. Then $x=ae$ and $y=bf$ for some $a,b \in A$. 
Then $$x+y = ae+bf =a(e+f) + (b-a)f \in A(e+f)$$
$\square$
###### 1. 
Suppose $V$ is an indecomposable summand of $A$. i.e. $A = V \oplus X$ for some $A$-submodule $X$.
$\implies 1_A = e_v + e_x$ for unique $e_v \in V$, $e_x \in X$.

>[!Claim] 
>$V = Ae_v$ and $e_v$ and $e_x$ are orthogonal idempotents. 

-  If $v \in V$, then $v = v\cdot 1_A = ve_v + ve_x$.
  $\implies \underbrace{v - ve_v}_{\in V} = \underbrace{v e_x}_{\in X} \in V \cap X = 0$ 
  $\implies v = v e_v$ and $ve_x = 0$
  $\implies V \subseteq Ae_v \subseteq V \implies V = Ae_v$
  
  Also $e_v = e_v^2 \implies e_v$ is an idempotent (note that $e_v \neq 0$ since $0 \neq V = Ae_v$) and $e_ve_x = 0$.  
  By symmetry if $x\in X$ then $x = xe_x$ and $xe_v = 0$ 
  $\implies e_x = e_x^2$ and $e_xe_v = 0$. 

Finally, if $e_v$ is *not* primitive, then $e_v = f +g$ for orthogonal idempotents $f,g$.
$\implies V = Ae_v = Af \oplus Ag$

###### 2.


