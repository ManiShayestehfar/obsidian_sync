# Relative Homology Groups

>[!def] $C_n(X,A)$
>$A \subseteq X$, let $C_n(X,A) := C_n(X)/C_n(A)$. i.e. the chains in $A$ are trivial in $C_n(X,A)$.
>- Boundary map $\partial:C_n(X) \to C_{n-1}(X)$ takes $C_n(A)$ to $C_{n-1}(A)$ and so it induces a *quotient boundary map* $\partial: C_n(X,A) \to C_{n-1}(X,A)$ via $x + C_n(A) \longmapsto \partial(x)+C_n(A)$. 

- This gives a sequence of boundary maps $\cdots \overset{}{\longrightarrow} C_n(X,A)\overset{\partial}{\longrightarrow} C_{n-1}(X,A)\overset{}{\longrightarrow}\cdots$
- $\partial^2 = 0$ as before

>[!def] 
>The **relative homology group** $H_n(X,A) := \ker \partial/\text{im }\partial$.
>- Elements of $H_n(X,A)$ are represented by *relative cycles*. i.e. n-chains $\alpha \in C_n(X)$ such that $\partial \alpha \in C_{n-1}(A)$.
>- A relative cycle is trivial in $H_n(X,A) \iff \alpha \in \text{im }\partial \iff$ it is a *relative boundary*. i.e. $\alpha=\partial\beta+\gamma$ for some $\beta\in C_{n+1}(X)$ and $\gamma \in C_n(A)$.

- **Note:** $C_n(X)/C_n(A)$ can be viewed as a subgroup of $C_n(X)$ but $\partial(C_n(X)/C_n(A)) \neq C_{n-1}(X)/C_{n-1}(A)$.

## Properties

>[!proposition]
>Given $A \subseteq X$, we have a long exact sequence 
>
  ![[Relative Homology-1760172984496.png|600]]
##### Proof
Consider
![[Relative Homology-1760238493629.png|430]]
which commutes.
By [[Exact Sequences|Thm 2.16]], we get that 

![[Exact Sequences-1760165061462.png|550]]

is a long exact sequence. But what is $\partial$?
Consider $\partial:H_n(X,A)\to H_{n-1}(A)$ given as $[a + C_n(A)] \mapsto [\partial_n(a)]$ where $a \in C_n(X)$ and $\partial_n(a) \in C_{n-1}(X)$.  $\square$

>[!proposition]
>There is a similar long exact sequence for *reduced* homology groups

>[!corollary]
>If $H_n(X,A)=0$ for all $n$, then $H_n(A)\cong H_n(X)$.
>- Also $H_n(X,A) \cong \widetilde{H}_n(X,A)$ when $A \neq \emptyset$
##### Proof
$$\cdots \overset{}{\longrightarrow}\underbrace{H_{n+1}(X,A)}_{=0} \overset{}{\longrightarrow}H_n(A) \overset{\cong}{\longrightarrow}H_n(X) \overset{}{\longrightarrow}\underbrace{H_n(X,A)}_{=0}\overset{}{\longrightarrow}H_{n-1}(A)\overset{}{\longrightarrow}\cdots$$where the isomorphism comes from the important case in [[Exact Sequences]]. $\square$

*Example:* $A= \{x_0\}$ for $x_0 \in X$. Then $H_n(X,x_0) \cong \widetilde{H}_n(X)$
Then $$\cdots \overset{}{\longrightarrow}\underbrace{\widetilde{H}_n(\{x_0\})}_{=0} \overset{}{\longrightarrow}\widetilde{H}_n(X) \overset{}{\longrightarrow}\widetilde{H}_n(X,\{x_0\})\overset{}{\longrightarrow}\underbrace{\widetilde{H}_{n-1}(\{x_0\})}_{=0}\overset{}{\longrightarrow}\cdots$$ is exact. $\implies \widetilde{H}_n(X) \cong \widetilde{H}_n(X,\{x_0\}) \cong H_n(X,\{x_0\})$. $\implies H_n(X,\{x_0\})\cong \widetilde{H}_n(X)$.

*Example:* $X = D^n,\: A = \partial D^n \cong S^{n-1}$. Then we need to find $H_n(D^n,\partial D^n)$. Then 
$$\cdots \overset{}{\longrightarrow}\underbrace{H_m(\partial D^n)}_{\widetilde{H}_m(\partial D^n)} \overset{}{\longrightarrow}\underbrace{H_m(D^n)}_{\widetilde{H}_m(D^n) = 0} \overset{}{\longrightarrow}H_m(D,\partial D^n)\overset{}{\longrightarrow}H_{m-1}(\partial D^n)\overset{}{\longrightarrow}\cdots H_0(D^n,\partial D^n)\overset{}{\longrightarrow}0$$
is exact.
So we have that $H_m(D^n,\partial D^n) \cong H_{m-1}(\partial D^n) \cong \widetilde{H}_{m-1}(\partial D^n) \cong \widetilde{H}_{m-1}(S^{n-1})$ for $m > 0$.
Therefore 
$$H_m(D^n, \partial D^n) = \begin{cases}
\mathbb{Z} & m=n  \\
0 & \text{otherwise}
\end{cases}$$
At $m=0$, and $n \neq 1$:  $H_0(\partial D^n) \cong \mathbb{Z}$, $H_0(D^n) \cong \mathbb{Z}$  ...


## Induced Homomorphisms

Suppose we have the homomorphism $f: X\to Y$ where $A \subseteq X$, $B \subseteq Y$ and $f(A) \subseteq B$. Then we can have the induced homomorphism $$f_\#:C_n(X,A) \overset{}{\longrightarrow}C_n(Y,B),\quad\quad x+C_n(A) \longmapsto f(x) + C_n(B)$$
Consider the commuting sequence

![[Relative Homology-1760249593943.png|500]]
where $f_\# \circ \partial = \partial \circ f_\#$.

>[!proposition] Using H Prop 2.9
>Given $f:X \to Y$,  then the chain map $f_\#: H_n(X) \overset{}{\longrightarrow}H_n(Y)$ was induced. Similarly for relative homologies we have $$f_\#: H_n(X,A) \to H_n(Y,B)$$

>[!Proposition] H 2.19
>If $f,g:(X,A) \to (Y,B)$ are homotopic through maps of pairs $(X,A)\to (Y,B)$, then $$f_* = g_*: H_n(X,A) \to H_n(Y,B)$$
##### Proof
Recall the prism operator $P:C_{n}(X) \overset{}{\longrightarrow}C_{n+1}(Y)$  from [[Singular Homology|Thm 2.10]] such that

![[Singular Homology-1760160919680.png|400]]

commutes. i.e. $\partial_{n+1}^{Y,B}\circ P + P \circ \partial_{n}^{X,A} = g_\# - f_\#$. We need to construct a similar operator to show the equivalence of $f_*, g_*$.

Firstly, $P(C_n(A)) \subseteq C_{n+1}(B)$. Hence, we have

![[Relative Homology-1760250577682.png|500]]
i.e. $\partial_{n+1}^{Y,B}\circ P + P \circ \partial_{n}^{X,A} = g_\# - f_\#$.
$\implies$ induces some homomorphism $f_*,g_*$ such that $f_*=g_*$.  $\square$


## Propositions

>[!proposition] H Prop 2.22
>Let $(X,A)$ be a good pair. Then the quotient map $$q:(X,A) \to (X/A,A/A) \quad \overset{\text{induces homom.}}{\longrightarrow}\quad q_*:H_n(X,A) \to H_n(X/A,A/A)\cong \widetilde{H}_n(X/A)$$
>for all $n$.
##### Proof
Let $V$ be a neighbourhood of $A$ in $X$, such that it DRs onto $A$. We get the commutative diagram:
![[Relative Homology-1760270851216.png]]
$f_1$ is an isomorphism since in the long exact sequence of the triple $(X,V,A)$, the groups $H_n(V,A)$ are zero for all $n$, because a DR of $V$ onto $A$ gives a homotopy equivalence of pairs $(V,A) \simeq (A,A)$, and $H_n(A,A)=0$. The DR of $V$ onto $A$ induces a DR of $V/A$ onto $A/A$, so the same argument shows that $g_1$ is an isomorphism. 
$f_1,g_1$ being isomorphisms follow directly from the Excision theorem.







# Long Exact Sequence of Triple $(X,A,B)$

Let $B \subseteq A \subseteq X$. This gives the SES: $$0 \overset{}{\longrightarrow}C_n(A,B) \overset{i}{\longrightarrow} C_n(X,B) \overset{j}{\longrightarrow}C_n(X,A) \overset{}{\longrightarrow}0$$
where $i$ is the inclusion map and $j$ is the quotient map $\text{id}_\#: C_n(X,B) \to C_n(X,A)$ given by $x + C_n(B) \longmapsto x+ C_n(A)$. 

For exactness we need $\ker j = \text{im }i$, where $\text{im }i=C_n(A)/C_n(B)= C_n(A,B)$, and $\ker j = \{x + C_n(B)\:|\: x+C_n(A) \in C_n(A)\} = (C_n(A) + C_n(B)) /C_n(B) = C_n(A)/C_n(B)$.

This gives the long exact sequence $$\cdots \overset{}{\longrightarrow}H_n(A,B) \overset{}{\longrightarrow}H_n(X,B) \overset{}{\longrightarrow}H_n(X,A) \overset{}{\longrightarrow}H_{n-1}(A,B) \overset{}{\longrightarrow}\cdots$$
## Example

Let $B = \{x_0\}$. Then the following sequence is long exact. 
$$\cdots \overset{}{\longrightarrow}H_n(A,\{x_0\}) \overset{}{\longrightarrow}H_n(X,\{x_0\}) \overset{}{\longrightarrow}H_n(X,A) \overset{}{\longrightarrow}H_{n-1}(A,\{x_0\}) \overset{}{\longrightarrow}\cdots$$ where the chain complex is isomorphic to its reduced kind with $\widetilde{H}$ etc.


## Excision Theorem

>[!theorem] H Thm 2.20
>Given $Z \subseteq A \subseteq X$ such that $\overline{Z}\subseteq \text{int }A$, then $$(X-Z,A-Z)\hookrightarrow (X,A)\quad \overset{\text{induces}}{\longrightarrow}\quad H_n(X-Z,A-Z)\overset{\cong}{\longrightarrow} H_n(X,A)$$
>for all $n$.
- Equivalently, for subspaces $A,B \subseteq X$ such that $X = \text{int }A \cup \text{int }B$, then $$(B, A \cap B)\hookrightarrow (X,A)\quad \overset{\text{induces}}{\longrightarrow}\quad H_n(A,A\cap B)\overset{\cong}{\longrightarrow} H_n(X,A)$$
  where here we set $B = X-Z$,  $Z=X-B$. Then $A\cap B = A - Z$ and the condition $\overline{Z}\subseteq \text{int }A$ is equivalent to $X = \text{int }A \cup \text{int }B$. 
##### Proof


### Excision Theorem for CW Complexes

>[!corollary] H Cor 2.24
>If the CW complex $X = A \cup B$, then 
>$$(B, A \cap B)\hookrightarrow (X,A)\quad \overset{\text{induces}}{\longrightarrow}\quad H_n(A,A\cap B)\overset{\cong}{\longrightarrow} H_n(X,A)$$
##### Proof 
Need the following claim

>[!Claim] 
>$(A\cup B)/A \longrightarrow B/(A\cap B)$ is a homomorphism.

By Prop 2.22, 
- $(X,A)$ induces a quotient map such that $H_n(X,A) \cong H_n(X/A,A/A)$, 
- $(B,A\cap B)$ induces a quotient map such that $H_n(B,A\cap B) \cong H_n(B/(A\cap B),(A\cap B)/(A\cap B))$
and by the claim $H_n(X/A,A/A) \cong H_n(B/(A\cap B),(A\cap B)/(A\cap B))$. Note that this works only if $A \cap B \neq \emptyset$. 

If $A \cap B = \emptyset$, then $H_n(B,A \cap B) \cong H_n(B)$, and $$H_n(X/A,A/A) \cong H_n(B/(A\cap B), A/A) \cong H_n(B,A/A) \cong H_n(B).\:\:\:\square$$

## Brouwer 1910 Theorem

>[!theorem] H Thm 2.26
>$U \subseteq \mathbb{R}^m, V \subseteq \mathbb{R}^n$ non-empty open sets. 
>$$U,V\:\text{homeomorphic} \iff m=n$$
>
##### Proof
Take $x\in U$, and consider $H_k(U, U -\{x\})$.

>[!Claim] 
>$$H_k(U,U-\{x\}) \cong H_k(\mathbb{R}^m, \mathbb{R}^{m}-\{x\})$$
###### Proof
 By Excision theorem (restatement), $X= \mathbb{R}^m, A = \mathbb{R}^m-\{x\}, B = U$
$$H_n(U, U \cap (\mathbb{R}^m-\{x\})) \cong H_n(\mathbb{R}^m, \mathbb{R}^m - \{x\})$$
but $H_n(U, U \cap (\mathbb{R}^m - \{x\})) \cong H_n(U,U \cap(U - \{x\}))$, and similarly for $V$.

To say $U,V$ are homeomorphic is to say there exists $h:U \to V$ and $h^{-1}:V \to U$.

We have that $H_k(V,V - \{h(x)\}) \cong H_k(\mathbb{R}^m, \mathbb{R}^m - \{h(x)\})$ for all $k$.

>[!Claim]
>$H_k(\mathbb{R}^m, \mathbb{R}^m - \{h(x)\}) \cong \widetilde{H}_{k-1}(\mathbb{R}^m - \{x\})$ for all $k$.
###### Proof
Using the long exact chain $$\cdots \overset{}{\longrightarrow}H_k(\mathbb{R}^m - \{x\}) \overset{}{\longrightarrow}\underbrace{H_k(\mathbb{R}^m)}_{=0} \overset{}{\longrightarrow}H_k(\mathbb{R}^m,\mathbb{R}^m - \{x\}) \overset{}{\longrightarrow}\underbrace{H_{k-1}(\mathbb{R}^m - \{x\})}_{\widetilde{H}_{k-1}(\mathbb{R}^m - \{x\})} \overset{}{\longrightarrow}\cdots$$
where we recall that $\mathbb{R}^m$ is contractible so $$H_k(\mathbb{R}^m) = H_k(\{point\}) = \begin{cases}
0 & k > 0  \\
\mathbb{Z} & k=0
\end{cases} $$Hence $H_k(U,U-\{x\}) \cong \widetilde{H}_{k-1}(\mathbb{R}^m-\{x\})$, and $H_k(V,V-\{h(x)\}) \cong \widetilde{H}_{k-1}(\mathbb{R}^n - \{h(x)\})$.

Since $\mathbb{R}^m-\{x\}$ DRs to $S^{m-1}$, $$\widetilde{H}_{k-1}(S^{m-1}) = \begin{cases}
\mathbb{Z} & k=m  \\
0 & \text{otherwise}
\end{cases}$$ $$\implies \widetilde{H}_k(U,U-\{x\}) = \begin{cases}
\mathbb{Z} & k=m  \\
0 & \text{otherwise}
\end{cases}$$
$$\widetilde{H}_k(V,V-\{h(x)\}) = \begin{cases}
\mathbb{Z} & k=m  \\
0 & \text{otherwise}
\end{cases}$$
Hence $U,V$ are homeomorphic $\implies H_k(U,U-\{x\}) \overset{\cong}{\longrightarrow} H_k(V,V-\{h(x)\})$ for all $k$.
$\implies m=n$.

