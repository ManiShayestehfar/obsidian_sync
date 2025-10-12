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


# Long Exact Sequence of Triple $(X,A,B)$

Let $B \subseteq A \subseteq X$. This gives the SES: $$0 \overset{}{\longrightarrow}C_n(A,B) \overset{i}{\longrightarrow} C_n(X,B) \overset{j}{\longrightarrow}C_n(X,A) \overset{}{\longrightarrow}0$$
where $i$ is the inclusion map and $j$ is the quotient map $\text{id}_\#: C_n(X,B) \to C_n(X,A)$ given by $x + C_n(B) \longmapsto x+ C_n(A)$. 

For exactness we need $\ker j = \text{im }i$, where $\text{im }i=C_n(A)/C_n(B)= C_n(A,B)$, and $\ker j = \{x + C_n(B)\:|\: x+C_n(A) \in C_n(A)\} = (C_n(A) + C_n(B)) /C_n(B) = C_n(A)/C_n(B)$.

This gives the long exact sequence $$\cdots \overset{}{\longrightarrow}H_n(A,B) \overset{}{\longrightarrow}H_n(X,B) \overset{}{\longrightarrow}H_n(X,A) \overset{}{\longrightarrow}H_{n-1}(A,B) \overset{}{\longrightarrow}\cdots$$
## Example

Let $B = \{x_0\}$. Then the following sequence is long exact. 
$$\cdots \overset{}{\longrightarrow}H_n(A,\{x_0\}) \overset{}{\longrightarrow}H_n(X,\{x_0\}) \overset{}{\longrightarrow}H_n(X,A) \overset{}{\longrightarrow}H_{n-1}(A,\{x_0\}) \overset{}{\longrightarrow}\cdots$$ where the chain complex is isomorphic to its reduced kind with $\widetilde{H}$ etc.

