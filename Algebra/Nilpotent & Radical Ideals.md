# Nilpotent Ideal

An ideal $I$ of $A$ is **nilpotent** if $I\neq0$ and $I^n=0$ for some $n>0$.

>[!proposition]
>Suppose $I$ is a submodule of $A$ such that $I^n\neq0$. Then $I$ contains an idempotent.
##### Proof
Let $J$ be the smallest/minimal non-nilpotent ideal contained in $I$ (so every ideal of $J$ is nilpotent).
Let $K$ be a minimal ideal of $J$ such that $JK\neq0$. $K$ exists because $J^2 \neq 0$ since $J$ is not nilpotent.

Let $x \in K$ such that $Jx\neq0$, Then $K=Jx$ by minimality of $K$. Hence there exists an element $e \in J$ such that $x = ex$. Consequently $x = ex=e^2x=\cdots$. In particular $e$ is nonzero.

If $e^2 = e$ then $e$ is idempotent and we are done. 
Otherwise, let $N = \text{Ann}_A(x) = \{a\in J\:|\: ax=0\}$. Then $e - e^2 \in N$, so $N$ is a nonzero ideal of $J$. Also $N \neq J$ since $e \not\in N$. However, $J$ is a minimal non-nilpotent ideal, so $N$ must be nilpotent.

Set $e_0:=e$ and $e_{i+1}:=3e_i^2-2e_i^3$.

>[!Claim]
>If $i\geq 0$, then $e_i-e_i^2\in N^{2^i}$ and $x = e_ix=e_i^2x=\cdots$
###### Proof
To prove this, we use induction on $i$. 
- If $i=0$ then $e_0=e$, $e_0-e_0^2\in N$, and $x=e_ix=e_i^2x=\cdots$ so the claim is true.
- By induction assume the claim for $e_i$. Therefore $e_{i+1}x=(3e_i^2-2e_i^3)x= (3-2)x$ and ![[Ring-1767874849382.png]]
  where the last line follows by induction since $e_i-e_i^2 \in N^{2i}$. This completes the proof of claim. $\square$

Now we are done because $e_i\neq0$ since $x=e_ix$. On the other hand, $N$ is nilpotent, so $N^k=0$ for some $k>0$. In particular $N^{2^i}=0$ for $i >0$ so $e_i-e_i^2=0$ for $i >0$. That is, $e_i=e_i^2$ is an idempotent (and $e_i=e_{i+1}$) as soon as $N^{2^i}=0$.  $\square$

## Properties

>[!Proposition]
>1. If $I,J$ are nilpotent, then so is $I + J$.
>2. Every submodule of $A$ contains a unique maximal nilpotent ideal
##### Proof
1. Suppose $I,J$ are nilpotent. Then there exists $m,n>0$ such that for $x \in I$ and $y \in J$, $x^n = 0$ and $y^m = 0$. Then for $x+y \in I +J$, consider 
   $$(x+y)^{m+n+1} = \sum_{k=0}^{m+n+1}\binom{m+n+1}{k}x^{k}y^{m+n+1-k} = 0$$
   since if $k \geq n$, then $x^n =0$, and if $k \geq m+n+1-k \geq m$, so $y^{m+n+1-k}=0$. Hence $I+J$ is nilpotent.
   
2. Take $N$ and $N'$ to be two maximal nilpotent ideals of a submodule $V$ of $A$. Then by result (1) above, $N + N'$ is also a nilpotent ideal of $V$. Hence $N = N + N' = N'$ by maximality. $\square$



# Radical

>[!Definition]
>The **radical** $\text{Rad } A$ of $A$ is its unique maximal nilpotent ideal.
> If $V$ is an $A$-module then the **radical** of $V$ is $\text{Rad }V = (\text{Rad }A)V$.
> - Let $V$ be an $A$-module and define $\text{Rad }^kV:= (\text{Rad }A)^k V$. Then $$V = \text{Rad }^0V\supseteq \text{Rad}^1V\subseteq \text{Rad }^2V \cdots \supseteq \text{Rad }^n V \supseteq 0.$$
  because $(\text{Rad }A)^n= 0$ for some $n >0$ since $\text{Rad }A$ is a nilpotent ideal. 


## Radicals of PIMs

>[!lemma] Lemma 8I
>1. The radical $\text{Rad }A$ of $A$ is a two-sided ideal
>2. Let $V$ be an $A$-module in $A$. Then $V \cap \text{Rad} A$ is the maximal nilpotent $A$-submodule of $V$
>3. Suppose $P$ is a principal indecomposable $A$-module. Then $\text{Rad } P = P \cap \text{Rad }A = (\text{Rad }A)e$ is the maximal nilpotent submodule of $P$, which is a proper ideal of $P$.
##### Proof
###### 1)
Tutorials

###### 2) 
Recall that every $A$-submodule contains a maximal nilpotent submodule, say $N$.
Then $N \subseteq V \cap \text{Rad} A$ as $\text{Rad}A$ is the unique maximal ideal of $A$. On the other hand, $V \cap \text{Rad} A$ is nilpotent, so $V \cap \text{Rad}A\subseteq N$. Hence $N = V \cap \text{Rad }A$.
Note that: $(V \cap \text{Rad }A)^n \subseteq (\text{Rad }A)^n \implies (V \cap \text{Rad }A)^n = 0$. Hence $V \cap \text{Rad }A$ is indeed nilpotent.
###### 3)
Write $P = Ae$ for a primitive idempotent $e\in A$. Then $e \not\in \text{Rad }P$ because $e^2 = e \neq 0$. So $\text{Rad } P \neq P$.
   
**First equality:**
By part (2), $P \cap \text{Rad }A$ is the maximal nilpotent submodule of $P$. So $\text{Rad }P \subseteq P \cap \text{Rad }A$.
Now $A = Ae \oplus A(1_A- e)\implies \text{Rad }A = \text{Rad }Ae \oplus \text{Rad }A(1_A-e)$ where the direct sum remains.
If $x \in P \cap \text{Rad }A$, then $x=xe$ (since $x \in P=Ae$, then $x =ae$, $xe =x$).
Hence $x \in (\text{Rad }A)e\implies (\text{Rad }A)e \subseteq P \cap \text{Rad }A$.

**Second equality:**
$(\text{Rad }A)e$ is a nilpotent ideal in $P$, because 
$$\begin{align*}
[(\text{Rad }A)e]^n &= (\text{Rad }A)e \cdot (\text{Rad }A)e \cdots (\text{Rad }A)e \\[2pt]
&\subseteq (\text{Rad }A)\cdot (\text{Rad }A) \cdots (\text{Rad }A)e  \\[2pt]
&\subseteq (\text{Rad }A)^ne   
\end{align*}$$
Then $(\text{Rad }A)e$ is nilpotent for some $n>0$ because $\text{Rad }A$ is nilpotent.
By part (2), $\text{Rad }P \subseteq P \cap \text{Rad }A$, so $(\text{Rad }A)e = P \cap \text{Rad }A$.

**Third equality:**
$\text{Rad }P = (\text{Rad }A)P = (\text{Rad }A)Ae \subseteq (\text{Rad }A)e$ since $\text{Rad }A$ is a two-sided ideal.
Hence $(\text{Rad }A)e = \text{Rad }P$. $\square$



## Isomorphism bet ween PIMs and Irreducible Modules
$$\left\{\text{PIMs of A}\right\} \overset{\cong}{\longrightarrow} \left\{\text{Irreducible }A\text{-modules}\right\};\qquad P \longmapsto D_p := P/\text{Rad }P$$

Let $A$ be a finite dimensional $\mathbb{F}$-algebra.

>[!theorem] Theorem 8J
>1. $P$ a PIM of $A$. Then $\text{Rad }P$ is the unique maximal proper submodule of $P$. 
> 	  - Consequently, $P/\text{Rad }P$ is an irreducible $A$-module.
>2. $P,Q$ are PIMS of $A$. Then $P \cong Q \iff P/\text{Rad }P \cong Q/\text{Rad }Q$.
>3. $D$ an irreducible $A$-module. Then $D \cong P/\text{Rad }P$ for some PIM $P$ of $A$.
##### Proof
###### 1)
Since $P$ is a principal indecomposable module, Lemma 8C gives us a primitive idempotent $e \in A$ such that $P = Ae$.

Let $M$ be an arbitrary proper submodule of $P$. We aim to show that $M$ is nilpotent. Once this is established, every proper submodule of $P$ is contained in $\operatorname{Rad} P$ (the maximal nilpotent submodule), making $\operatorname{Rad} P$ the unique maximal proper submodule.

**Case 1: $M$ is nilpotent.** Then $M \subseteq \operatorname{Rad} P$ by definition, and we are done.
**Case 2: $M$ is not nilpotent.** By Proposition 8E, $M$ contains an idempotent $f$. We shall derive a contradiction.

Set $Q = Af$. Since $f \in M \subseteq P$ and $f \neq 0$, the submodule $Q$ is a nonzero submodule of $P$. Note that $e$ is a right identity on $P$ (since $P = Ae$) and $f$ is a right identity on $Q$ (since $Q = Af$).

We claim that the elements $ef$ and $e - ef$ are both nonzero:
- If $ef = 0$, then $Q = Qe = Q(ef) = 0$, contradicting $Q \neq 0$.
- If $e - ef = 0$, then $e = ef$, so $P = Ae = Aef \subseteq Af = Q$. This forces $Q = P$, contradicting the assumption that $M$ (and hence $Q \subseteq M$) is a proper submodule of $P$.

Next, we verify that $e - ef$ is idempotent:
$$

(e - ef)^2 = e^2 - eef - efe + efef = e - ef - ef + ef^2 = e - ef,

$$
using $e^2 = e$, $f^2 = f$, and $fe = f$ (since $f \in P = Ae$ implies $fe = f$).
Similarly, $ef$ is idempotent:
$$

(ef)^2 = efef = ef^2 = ef.

$$
Moreover, $ef$ and $e - ef$ are orthogonal:
$$

(ef)(e - ef) = efe - efef = ef - ef = 0, \qquad (e - ef)(ef) = ef - efef = ef - ef = 0.

$$
Since $e = (e - ef) + ef$ is a sum of two nonzero orthogonal idempotents, $e$ is not primitive. This contradicts our assumption, so Case 2 cannot occur.

Therefore every proper submodule of $P$ is nilpotent, hence contained in $\operatorname{Rad} P$. It follows that $\operatorname{Rad} P$ is the unique maximal proper submodule, and $P / \operatorname{Rad} P$ is irreducible. $\square$
###### 2)
Write $D_P = P / \operatorname{Rad} P$ and $D_Q = Q / \operatorname{Rad} Q$ for the irreducible tops.

**Forward direction:**
Suppose $\varphi : P \to Q$ is an $A$-module isomorphism. Let $\pi_Q : Q \to D_Q$ denote the natural projection. The composition $\pi_Q \circ \varphi : P \longrightarrow D_Q$ is a surjective $A$-module homomorphism. By the First Isomorphism Theorem,
$$

P / \ker(\pi_Q \circ \varphi) \cong \operatorname{im}(\pi_Q \circ \varphi) = D_Q.

$$
Since $D_Q$ is irreducible, $\ker(\pi_Q \circ \varphi)$ is a maximal proper submodule of $P$. By part (a), $P$ has a unique maximal proper submodule, so $\ker(\pi_Q \circ \varphi) = \operatorname{Rad} P$. Therefore $D_P = P / \operatorname{Rad} P \cong D_Q$.

**Converse direction:**
Suppose $\varphi : P / \operatorname{Rad} P \to Q / \operatorname{Rad} Q$ is an $A$-module isomorphism. Write $P = Ae$ for a primitive idempotent $e \in A$, and let $q$ be any element of $Q$ satisfying
$$

\varphi(e + \operatorname{Rad} P) = q + \operatorname{Rad} Q.

$$

*Step 1: The isomorphism $\varphi$ is determined by $q$.* For any $x \in P$, we have $x = xe$ (since $e$ is a right identity on $P = Ae$), so
$$

\varphi(x + \operatorname{Rad} P) = x\varphi(e + \operatorname{Rad} P) = x(q + \operatorname{Rad} Q) = xq + \operatorname{Rad} Q.

$$
In particular, $\varphi(e + \operatorname{Rad} P) = eq + \operatorname{Rad} Q$.

*Step 2: Lift to a module homomorphism $\tilde{\varphi} : P \to Q$.* Define
$$

\tilde{\varphi}(x) = xeq, \qquad x \in P.

$$
This is $\mathbb{F}$-linear by definition, and $\operatorname{im} \tilde{\varphi} \subseteq Q$. For any $a \in A$ and $x \in P$,
$$

\tilde{\varphi}(ax) = (ax)eq = a(xeq) = a\tilde{\varphi}(x),

$$
so $\tilde{\varphi}$ is an $A$-module homomorphism.


*Step 3: Construct the reverse lift.* Let $\psi = \varphi^{-1} : Q / \operatorname{Rad} Q \to P / \operatorname{Rad} P$, and write $Q = Af$ for a primitive idempotent $f$. By the same reasoning as above, there exists $p \in P$ such that
$$

\psi(f + \operatorname{Rad} Q) = p + \operatorname{Rad} P,

$$
and we define the $A$-module homomorphism $\tilde{\psi} : Q \to P$ by
$$

\tilde{\psi}(y) = yfp, \qquad y \in Q.

$$

*Step 4: Show the compositions are invertible.* The maps $\tilde{\psi}\tilde{\varphi} \in \operatorname{End}_A(P)$ and $\tilde{\varphi}\tilde{\psi} \in \operatorname{End}_A(Q)$ are each either nilpotent or invertible, by Lemma 7C (since $P$ and $Q$ are indecomposable).
We compute:
$$

\tilde{\psi}\tilde{\varphi}(e) = \tilde{\psi}(eq) = eqfp, \qquad \tilde{\varphi}\tilde{\psi}(f) = \tilde{\varphi}(fp) = fpeq.

$$
Hence $(\tilde{\psi}\tilde{\varphi})^n(e) = (eqfp)^n$ and $(\tilde{\varphi}\tilde{\psi})^n(f) = (fpeq)^n$, so $\tilde{\psi}\tilde{\varphi}$ is nilpotent if and only if $eqfp$ is nilpotent, and $\tilde{\varphi}\tilde{\psi}$ is nilpotent if and only if $fpeq$ is nilpotent.

Now examine what $\psi \circ \varphi$ and $\varphi \circ \psi$ do:
$$
\begin{align*}
(\psi \circ \varphi)(e + \operatorname{Rad} P) &= \psi(eq + \operatorname{Rad} Q) = eq\psi(f + \operatorname{Rad} Q) = eqfp + \operatorname{Rad} P, \\

(\varphi \circ \psi)(f + \operatorname{Rad} Q) &= \varphi(fp + \operatorname{Rad} P) = fp\varphi(e + \operatorname{Rad} P) = fpeq + \operatorname{Rad} Q.

\end{align*}
$$
Since $\varphi$ and $\psi$ are mutually inverse isomorphisms, $\psi \circ \varphi = \operatorname{id}$ and $\varphi \circ \psi = \operatorname{id}$. In particular, $eqfp + \operatorname{Rad} P = e + \operatorname{Rad} P$ and $fpeq + \operatorname{Rad} Q = f + \operatorname{Rad} Q$, so $eqfp \equiv e \pmod{\operatorname{Rad} P}$ and $fpeq \equiv f \pmod{\operatorname{Rad} Q}$. These elements are therefore not nilpotent (since $e$ and $f$ are idempotent, hence non-nilpotent, and an element congruent to a non-nilpotent element modulo the radical is itself non-nilpotent).

It follows that $\tilde{\psi}\tilde{\varphi}$ and $\tilde{\varphi}\tilde{\psi}$ are both invertible (by the nilpotent-or-invertible dichotomy). In particular, $\tilde{\varphi}$ is both injective and surjective, so $\tilde{\varphi} : P \xrightarrow{\sim} Q$ is an isomorphism, giving $P \cong Q$. $\square$

###### 3)
Let $D$ be an irreducible $A$-module, and write
$$

A = P_1 \oplus P_2 \oplus \cdots \oplus P_t

$$
as a decomposition of the regular module $A$ into principal indecomposable submodules (which exists by the Krull–Schmidt theorem).

By Proposition 4K(a), $D \cong A / M$ for some maximal submodule $M$ of $A$. Since $M$ is maximal, $A = M + P_i$ for at least one index $i$ (otherwise $P_i \subseteq M$ for all $i$, forcing $A = M$, a contradiction). Choose such an $i$ with $P_i \not\subseteq M$.

By the Second Isomorphism Theorem,
$$

D \cong A / M = (M + P_i) / M \cong P_i / (P_i \cap M).

$$
Now $P_i / (P_i \cap M)$ is a quotient of $P_i$ that is isomorphic to the irreducible module $D$, so $P_i \cap M$ is a maximal submodule of $P_i$. By the Fourth Isomorphism Theorem (Theorem 4I(d)), this means $P_i \cap M$ is a maximal proper submodule of $P_i$.

By part (a), $P_i$ has a unique maximal proper submodule, namely $\operatorname{Rad} P_i$. Therefore $P_i \cap M = \operatorname{Rad} P_i$, and
$$

D \cong P_i / \operatorname{Rad} P_i,

$$
as required. $\square$



>[!Theorem] Theorem 8K
>Suppose $A$ is a finite dimensional $\mathbb{F}$-algebra. Then TFAE:
>1. The algebra $A$ is semisimple $\iff \text{Rad }A=0$
>2. Every $A$-module $V$ is semisimple $\iff \text{Rad }V = 0$
>3. Every PIM is irreducible
>4. $A$ is completely reducible $\iff$ direct sum of irreducibles
>5. $A$ is a sum of irreducible $A$-modules (not necessarily direct)
>6. Every $A$-module is a sum of irreducibles
>7. Every  $A$-module is completely reducible (direct sum of irreducibles)

##### Proof
###### 1 -> 2
Obvious as $\text{Rad }A=0 \implies \text{Rad }V = (\text{Rad }A)V=0$
###### 2 -> 3
$P$ a PIM. By (2), $\text{Rad }P =0 \implies P/\text{Rad }P\cong P$. So $P$ is irreducible.
###### 3 -> 4
Write $A=P_1,...,P_z$ (each a PIM). By (3), each $P_i$ is irreducible, and so $A$ is completely reducible.
###### 4 -> 5
Every direct sum is a sum
###### 5 -> 6
Write $A = D_1+\cdots + D_z$ (each irreducible $A$-modules). Let $V$ be any $A$-module.
Then $\Theta: A^{\oplus n} \to V$ is an isomorphism for $n \geq 1$.
Then $V = \sum_{\substack{1 \leq i \leq n \\ 1 \leq j \leq z}} \text{im }\Theta(D_{ij})$.
So $A^{\oplus n} = D_{11}+ \cdots  + D_{1z} + \cdots D_{n1} + \cdots D_{nz}$.
By Schur's lemma, $\Theta|_{D_{ij}}=0$ or $\cong D_{ij}$. Thus $V$ is a sum of irreducible modules.
###### 6 -> 7
Suppose $V$ is an $A$-module and $V=D_1+\cdots+D_z$ (each irreducible modules).
Let $I \subseteq \{1,..,z\}$ be minimal such that $V = \sum_{i \in I}D_i$.

**Claim:** $V = \bigoplus_{i \in I} D_i$.
If this was not true, there exists $j \in I$ such that $0 \neq d \in D_j \cap \sum_{i \in I \setminus \{j\}} D_i = 0$.
Then $D_j= Ad$ since $D_j$ is irreducible. So 
$$D_j \subseteq Ad \subseteq \sum_{ i \in I \setminus \{j\}} AD_i = \sum_{\substack{i \in I \\ i \neq j}} D_i$$
Contradicting the minimality of $I$.
Hence $V = \bigoplus_{i \in I} D_i$. 

###### 7 -> 1
If every $A$-module is completely reducible, then in particular, every PIM is completely reducible. Hence every PIM is irreducible.
By $(7) \Rightarrow (3)$, $\text{Rad }P=0$.
Write $A = P_1 \oplus \cdots \oplus P_z$ for $P_i$ indecomposable. 
$\implies \text{Rad }A = (\text{Rad }P_1)\oplus \cdots \oplus (\text{Rad }P_z) = 0$.
That is, $A$ is semisimple. 
$\square$



## Corollaries

>[!corollary]
>The following are equivalent:
>1. Characteristic of $\mathbb{F}$ does not divide order of $G$
>2. Every $\mathbb{F}G$-module is completely reducible
>3. The group algebra is semisimple
>4. Every indecomposable $\mathbb{F}G$-module is irreducible
>5. $\text{Rad }\mathbb{F}G = 0$ 

##### Proof

(1) to (2) follows from [[Maschke's Theorem]]. By the last theorem parts (2), (3), (4)
 are equivalent. Only need to show (5) -> (1).
###### 5 -> 1
We prove by contrapositive that if the characteristic of $\mathbb{F}$ does divide $|G|$, then $\text{Rad }\mathbb{F}G \neq 0$. 

In particular in $\mathbb{F}$, $|G| = |G|\cdot 1_{\mathbb{F}}=0$.  Let $x_G = \sum_{x\in G} x$. Then $gx_G =x_G$ for all $g \in G$. So $x_G^2 = |G|x_G = 0$ in $\mathbb{F}G$. Hence $\mathbb{F}x_G$ is a nonzero nilpotent ideal of $\mathbb{F}G$, so $\text{Rad }\mathbb{F}G \neq 0$. 
$\square$


## Quotienting By Radicals

By Artin-Wedderburn theorem we know that 
$$A \cong \bigoplus_{D \in \text{Irr}(A)} P^{\oplus a_D}$$
for some $a_D >0$.

Let $R = \text{Rad }A$ and $\overline{A}=A/R = A/\text{Rad }A$.

>[!Proposition]
>$\overline{A}$ is an $\mathbb{F}$-algebra
##### Proof
By construction $\overline{A}$ is an $\mathbb{F}$-vector space with 
- $(a+R)+(b+R) = (a+b)+R$
- $(a+R)(b+R) = ab + R$
- $\lambda(a+R) = \lambda a+ R$   
for all $a,b \in A$ and $\lambda \in \mathbb{F}$.
We need to check that $\overline{A}$ is a ring. Since $A$ is a ring, we just need to make sure multiplication is well-defined. Suppose $a + R = a'+R \iff a-a' \in R$ and $b + R = b' + R \iff b-b' \in R$.
Now $ab = a(b-b')+ab'=a(b-b') + (a-a')b' + a'b' = a'b'$.  Since the first two terms are in $R$ (and because $R$ is a two-sided ideal). 
Then $ab + R = a'b' + R$.
Hence $\overline{A}$ is an $\mathbb{F}$-algebra. $\square$


### Theorems

>[!Theorem]
>1. $\text{Irr}(\overline{A}) = \text{Irr}(A)$
>	- In particular, every irreducible $\overline{A}$-module is an irreducible $A$-module (and vice-versa)
>2. If $A \cong \bigoplus_{D \in \text{Irr}(A)} P_D^{\oplus a_D}$, then $\overline{A}\bigoplus_{D \in \text{Irr}(\overline{A})} D^{\oplus a_D}$
> 	- i.e. $[A :P_D] = [\overline{A}:D]$
>3. $\overline{A}$ is semisimple
>4. $A$ is Schurian $\iff$ $\overline{A}$ is Schurian
>5. $$\dim A \leq \sum_{D \in \text{Irr}(A)}(\dim P_d)(\dim D)\qquad,\qquad \dim \overline{A} \leq \sum_{D \in \text{Irr}(\overline{A})} (\dim D)^2$$
>   with equality $\iff A$ is Schurian.
##### Proof
###### 1. 
Let $D':=(\text{Rad }A)D$. Since $D$ is irreducible, then $D' =0$. 
Hence there is a well-defined action of $\overline{A}$ on $D_i$ given by: 
$$(a+\text{Rad }A)d = ad\qquad \forall d \in D_i, a\in A.$$
If $d$ is a nonzero element of $D_i$, then $D_i = Ad$ since $D_i$ is irreducible as an $A$-module. Hence $D_i = \overline{A}d$ is also an irreducible $\overline{A}$-module.

For the reverse inclusion, for each $i$, consider $\pi_i:A \to P_i$ the projection map and define $\pi:\overline{A}\to D_1 \oplus \cdots \oplus D_t$ by $\pi(a+\text{Rad }A) = (\pi_1(a)+\text{Rad }P_1,...,\pi_t(a)+\text{Rad }P_t)$  for all $a \in A$.

*Well-definedness:* If $a + \text{Rad }A = a' + \text{Rad }A$, then $a-a' \in \text{Rad }A$ so $\pi_i(a-a') \in \text{Rad }P_i$ since $\text{Rad }P_i = P_i \cap \text{Rad }A$ (by Lemma 8I-3). So $\pi_i(a) + \text{Rad }A = \pi_i(a') + \text{Rad }A$, for all $i$.

*Homomorphism:*  Each $\pi_i$ is an $A$-module homomorphism, and so $\pi$ is an $\overline{A}$-module homomorphism.



###### 2.

###### 3.

###### 4.

###### 5.