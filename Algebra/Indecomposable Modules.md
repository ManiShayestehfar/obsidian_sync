# Decomposable vs Indecomposable

>[!def]
>An $A$-module $V$ is
>- **decomposable:** there exists $U,W \subset V$  such that $V = U \oplus W$
>- **indecomposable:** not decomposable

## Examples

1. Trivial submodules are indecomposable
2. Any irreducible module $D$ is indecomposable
3. $G = S_n, V = \mathbb{F}^n \implies$$$\begin{cases}
V = I \oplus W & \text{char} \:\mathbb{F} \nmid n  \\[3pt]
V \text{ is indecomp. } & \text{char}\:\mathbb{F} \mid n \end{cases}$$

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
###### 3.
$(\subseteq)$
$a(e+f) = ae+af \in Ae \oplus Af$ where $Ae \cap Af= 0$ since $ef=fe=0$.

$(\supseteq)$
Take $x \in Ae$ and $y \in Af$. Then $x=ae$ and $y=bf$ for some $a,b \in A$. 
Then 
$$x+y = ae+bf =a(e+f) + (b-a)f \in A(e+f)$$
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
$\implies V = Ae_v = Af \oplus Ag$  (by part (3))
This contradicts $V$ being indecomposable so $e_v$ is primitive
$\square$

>[!success] Moral
>Indecomposable summands of $A$     $\equiv$     Primtive idempotents in $A$


###### 2.
For $P$ a PIM, write $A \cong P \oplus Q$ for some $A$-module $Q$.
Now define the projection map: $\pi: A \to P$ and let $e:= \pi(1_A)\in A$.

For any $a \in A$, $\pi(a) = \pi(a\cdot1_A) = a \cdot\pi(1_A)= ae$,
so every element of $P = \text{im }\pi$ is of the form $ae$. Thus $P = Ae$.

**Idempotence:** 
$$e^2 = \pi(1_A)\pi(1_A) = \pi(1_A \cdot 1_A) = \pi(1_A) = e$$
**Primitivity:**
Suppose $e = e_1+e_2$ where $e_1,e_2$ are orthogonal idempotents.
Then by part (3) of Lemma 8C, $Ae = Ae_1 \oplus Ae_2$.
This would decompose $P$, contradicting the assumption that $P$ is a PIM.
Hence $e$ must me primitive. $\square$


# Fitting's Lemma

>[!lemma] Fitting's Lemma
>Suppose $V$ is an $A$-module and $\varphi: V \to V$ is a module homomorphism. Then $$V = \ker \varphi^n \oplus \text{im }\varphi^n$$ 
>for some $n > 0$.
##### Proof
Since $\ker\varphi \subseteq \ker\varphi^2 \subseteq \cdots$ and $V$ is finite-dimensional, this ascending chain stabilises. Hence there exists $n>0$ such that $\ker\varphi^n=\ker\varphi^{n+1}=\cdots$. In particular, $\ker\varphi^n=\ker\varphi^{2n}$.

Consider the restricted map $\varphi^n|_{\operatorname{im}\varphi^n}:\operatorname{im}\varphi^n\to \operatorname{im}\varphi^{2n}$. This map is surjective by definition. Its kernel is $\ker\varphi^n\cap\operatorname{im}\varphi^n$.

Let $x\in\ker\varphi^n\cap\operatorname{im}\varphi^n$. Then $x=\varphi^n(v)$ for some $v\in V$, and $\varphi^n(x)=0$. Hence $\varphi^{2n}(v)=0$, so $v\in\ker\varphi^{2n}=\ker\varphi^n$. Therefore $x=\varphi^n(v)=0$. Thus $\ker\varphi^n\cap\operatorname{im}\varphi^n=0$.

It remains to show that every $x\in V$ can be written as a sum of an element of $\ker\varphi^n$ and an element of $\operatorname{im}\varphi^n$. Since $\varphi^n|_{\operatorname{im}\varphi^n}:\operatorname{im}\varphi^n\to\operatorname{im}\varphi^{2n}$ is an isomorphism, and $\varphi^n(x)\in\operatorname{im}\varphi^n=\operatorname{im}\varphi^{2n}$, there exists $y\in V$ such that $\varphi^n(x)=\varphi^{2n}(y)$.

Then $x=(x-\varphi^n(y))+\varphi^n(y)$, where $\varphi^n(y)\in\operatorname{im}\varphi^n$, and $\varphi^n(x-\varphi^n(y))=\varphi^n(x)-\varphi^{2n}(y)=0$. Hence $x-\varphi^n(y)\in\ker\varphi^n$.

Therefore $V=\ker\varphi^n+\operatorname{im}\varphi^n$. Since also $\ker\varphi^n\cap\operatorname{im}\varphi^n=0$, we conclude that $V=\ker\varphi^n\oplus\operatorname{im}\varphi^n$. $\square$

## Lemma

>[!lemma] Lemma 7C
>Suppose $P$ is an indecomposable $A$-module. Then $\text{End}_A(P)$ is a [[Ring|local ring]] with a maximal proper ideal
>$$\mathfrak{m} = \{\varphi\in \text{End}_A(P)\:|\: \varphi^n=0\quad \exists n>0\}$$

##### Proof
Let $R=\operatorname{End}_A(P)$, and let $\mathfrak m$ be a maximal proper left ideal of $R$.

First let $\varphi\in\mathfrak m$. By Fitting's lemma, there exists $n>0$ such that $P=\ker\varphi^n\oplus\operatorname{im}\varphi^n$. Since $P$ is indecomposable, either $\ker\varphi^n=0$ or $\operatorname{im}\varphi^n=0$.

If $\ker\varphi^n=0$, then $\varphi^n$ is injective, hence an isomorphism since $P$ is finite-dimensional. Therefore $\varphi$ is an isomorphism, so $\varphi$ is a unit in $R$. But no proper left ideal contains a unit, contradicting $\varphi\in\mathfrak m$. Hence $\operatorname{im}\varphi^n=0$, so $\varphi^n=0$. Thus every element of $\mathfrak m$ is nilpotent.

Now let $\psi\notin\mathfrak m$. Since $\mathfrak m$ is maximal, the left ideal generated by $\mathfrak m$ and $\psi$ is all of $R$. Hence there exist $a\in R$ and $\varphi\in\mathfrak m$ such that $1=a\psi+\varphi$. Since $\varphi\in\mathfrak m$, we have $\varphi^n=0$ for some $n>0$. Therefore
$$(1+\varphi+\cdots+\varphi^{n-1})a\psi=(1+\varphi+\cdots+\varphi^{n-1})(1-\varphi)=1-\varphi^n=1.$$
So $\psi$ has a left inverse. Hence $\psi$ is injective, and since $P$ is finite-dimensional, $\psi$ is an isomorphism. Thus every element of $R\setminus\mathfrak m$ is a unit.

It follows that $\mathfrak m$ is the unique maximal proper left ideal of $R$, since any proper left ideal cannot contain a unit and hence must be contained in $\mathfrak m$.

Finally, we have already shown that every element of $\mathfrak m$ is nilpotent. Conversely, if $\psi\notin\mathfrak m$, then $\psi$ is a unit, so $\psi$ is not nilpotent. Hence the nilpotent elements are precisely the elements of $\mathfrak m$. Therefore
$$\mathfrak m=\{\varphi\in\operatorname{End}_A(P)\mid \varphi^n=0 \text{ for some } n>0\},$$
and $\operatorname{End}_A(P)$ is local. $\square$


# Krull-Schmidt

>[!theorem] Krull-Schmidt Theorem
>Let $V$ be an $A$-module such that $V \cong M_1 \oplus \cdots \oplus M_r$ and $V \cong N_1 \oplus \cdots \oplus N_s$ where each $M_i,N_j$ are indecomposable. 
>Then $r=s$, and after relabelling, $M_i \cong N_i$.
##### Proof
We argue by induction on $r$. Define the maps $\mu_r,\nu_i \in \text{End}_A(V)$ to be $A$-module endomorphisms given as
$$\mu_r: V \twoheadrightarrow M_r \hookrightarrow V \qquad ,\qquad \nu_i: V \twoheadrightarrow N_i \hookrightarrow V  $$
Then $1_V = \nu_1+\cdots +\nu_s$ so $\mu_r = \mu_r(\nu_1+\cdots+\nu_r)$. 
By restriction consider $\mu_r\nu_j$ as an endomorphism of $M_r$. Since $\mu_r$ restricts to the identity map on $M_r$, then at least one of $\mu_r\nu_j$ must be an isomorphism by Lemma 7C.
WLOG assume $\mu_r \nu_s$ is that isomorphism. Hence we have the map
$$M_r \overset{\nu_s}{\longrightarrow}N_s \overset{\mu_r}{\longrightarrow} M_r.$$
By construction, $\mu_r\nu_s$ restricts to an isomorphism from $M_r$ to itself.
Similarly $\nu_s \mu_r \in \text{End}_A(N_s)$. If $\nu_s\mu_r$ was not at isomorphism, it would be nilpotent by Fitting's lemma (since $N_s$ is indecomposable, if $\nu_s\mu_r$ is not an isomorphism, then $\text{im }((\nu_s\mu_r)^n)=0$)
But $(\nu_s\mu_r)^n = 0\implies (\mu_r\nu_s)^{n+1} = \mu_r(\nu_s\mu_r)^n\nu_s=0$, which is a contradiction since we established that $\mu_r\nu_s$ is an isomorphism. Therefore, $\nu_s\mu_r$ is an isomorphism as well.
Thus both $\nu_s,\mu_r$ are isomorphisms so that $M_r \cong N_s$.

Now consider the $A$-module: $(N_1 \oplus \cdots \oplus N_{s-1}) + M_r$.
This may seem like a proper submodule of $V$. But 
$$(N_1 \oplus \cdots \oplus N_{s-1}) \cap M_r = \{m \in M_r \:|\: \nu_s(m) =0\}=0$$
1. First equality comes from the fact that an element $m \in M_r$ is in the direct sum of $N_i$ if $\nu_s(m)=0$.
2. Second equality holds since we established that $\nu_s$ is an isomorphism from $M_r$ to $N_s$, so $\ker \nu_s = 0$. 
Since $\dim M_r = \dim N_s$, counting dimensions shows that $V = N_1 \oplus \cdots \oplus N_{s-1} \oplus M_r$. 
Finally we use the second isomorphism to show:
$$M_1 \oplus \cdots M_{r-1} \cong V/M_r \cong \frac{N_1 \oplus \cdots \oplus N_{s-1} \oplus M_r}{M_r} \cong N_1 \oplus \cdots \oplus N_{s-1}.$$
The theorem now follows by induction on $s$. $\square$

## Corollaries

>[!Corollary]
>Suppose $V \oplus X \cong W \oplus X$ for $A$-modules $V,W,X$. Then $V \cong W$.
- The proof is a direct and easy application of Krull-Schmidt: Decompose into direct sum of indecomposables, by Krull-Schmidt we can cancel the $X$-terms and the $V$ and $W$ indecomposables are isomorphic up to relabelling.


