# Motivation

- This is an algebraic variant of homology
- Big difference: contravariant vs covariant. i.e. it flips the direction of arrows
- We have a "cup product" structure on cohomology groups
	- This gives us a ring structure


# Dual

**Recall:** $A,B$ abelian groups, then $\text{Hom}(A,B) = \{f:A \to B \text{ homomorphisms }\}$
$\text{Hom}(A,B)$ is a group w.r.t the operation on $B$.

Given  $\alpha:A \to B$ a group homom. then we can get $\alpha^*: \text{Hom}(B,G) \to \text{Hom}(A,G)$ via $f \mapsto f\alpha$ for an abelian group $G$. 
- $\alpha^*$ is called the **dual** 

## Properties
1. $\text{Hom}(A \oplus B, G) = \text{Hom}(A,G) \oplus \text{Hom}(B,G)$ 
2. $1^* = 1$
3. $0^* = 0$
4. $(\alpha\beta)^* = \beta^*\alpha^*$
5. $A \overset{}{\longrightarrow}B \overset{}{\longrightarrow} C \overset{}{\longrightarrow}0$ exact implies $A^* \overset{}{\longleftarrow}B^* \overset{}{\longleftarrow} C^* \overset{}{\longleftarrow} 0$ is exact
	Dual of a short exact sequence is not always short exact

## In Chain Complexes

Now given a chain complex of free abelian groups:
$$\cdots \overset{}{\longrightarrow}C_n \overset{\partial_n}{\longrightarrow}C_{n-1} \overset{\partial_{n-1}}{\longrightarrow}C_{n-2}\overset{}{\longrightarrow}\cdots$$
For a fixed abelian group $G$, we get maps 
$$\cdots \overset{}{\longleftarrow}\text{Hom}(C_n,G) \overset{\partial_n^*= \delta_n}{\longleftarrow}\text{Hom}(C_{n-1},G)\overset{\partial_{n-1}^*=\delta_{n-1}}{\longleftarrow}\text{Hom}(C_{n-2},G)\overset{}{\longleftarrow}\cdots$$

$\delta_n =$ **dual coboundary map**, $\text{Hom}(C_n,G)=$ **dual cochain groups**.

If $\partial_n \circ \partial_{n-1}=0$ for all $n\geq 1$, then $\delta_{n-1} \circ \delta_n = 0$.
$\delta_{n}(\delta_{n-1}(f)) = f \delta_n \delta_{n-1} = 0$ 
The above is called a **dual chain complex**.


# Cohomology of Spaces

$X =$ space,
$G =$ abelian group. 
$C^n(X;G)=$ Singular n-cochain with coefficients in $G$ = $\text{Hom}(C_n(X), G)$ 

- For $\phi \in C^n(X;G)\implies \phi : C_n(X) \to G$ is equivalent to $f(n)$s from n-simplices to $G$. 

>[!def] Coboundary map
>$$\delta: C^n(X;G)\to C^{n+1}(X;G) \quad\text{via}\quad\phi \to \phi \circ \partial$$
>i.e. $\delta(\phi(\sigma)) = \sum_{i}(-1)^i \phi(\sigma|_{[v_0,...,\hat{v_i},...,v_n]})$

- $\delta^2 = 0$

# Singular Cohomology

>[!def] Singular Cohomology groups with coefficients in $G$
>$$H^n(X;G):=\ker\delta_{n+1}/\text{im }\delta_{n}$$ at $C^n(X;G)$, in the cochain complex
>$$\cdots \overset{}{\longleftarrow}C^1(X;G)\overset{\delta}{\longleftarrow}C^0(X;G)\overset{\delta}{\longleftarrow}0$$
>

- Cocycle is $\ker \delta$
- Coboundary is $\text{im }\delta$
- n-chain is $C_n(X)$
- A cochain $\phi$ is a cocycle if $\delta\phi = 0$ i.e. $\phi \circ \partial = \phi = 0$ on boundaries

- By the universal coefficient theorem, we get the split short exact sequence:
  $$0 \overset{}{\longrightarrow}\text{Ext}(H_{n-1}(X);G)\overset{}{\longrightarrow}H^n(X;G)\overset{}{\longrightarrow}\text{Hom}(H_n(X),G)\overset{}{\longrightarrow}0$$
1. Cohomology groups are completely determined by $H_n(X)$ and $G$
2. Can get the cohomology group w.r.t coefficients by looking at homology groups w.r.t. $\mathbb{Z}$


## Examples 

1. $n=0$, then $H^{0}(X,G) \cong \text{Hom}(H_0(X),G)$ 
   i.e. no $\text{Ext}$ groups
   Elements of $H^0(X,G)$ are $f(n)$'s from path-connected components of $X$ to $G$. Or $f(n)$'s that are constant on the path-connected components of $X$ to $G$.

2. $n=1$, $H_0(X) =$ free $\implies \text{Ext}(H_0;G) = 0 \implies H^1(X;G)\cong \text{Hom}(H_1(X),G)$
   If $X$ is path-connected, $H^1(X,G)\cong \text{Hom}(\pi_1^{ab},G)\cong \text{Hom}(\pi_1(X),G)$

3. $F$ a field, then $H^n(X,F) \cong \text{Hom}_F(H_n(X,F),F)$ the $\text{Hom}_F$ includes $F$-module homomorphisms


# Induced Homomorphisms

Take $f:X \to Y$. Then we had $f_\#:C_n(X) \to C_n(Y)$. Now consider
$$f^\#: C^n(Y) \to C^n(X)$$
and get an induced homomorphism 
$$f^*: H^n(Y,B;G)\to H^n(X,A;G)$$
which gives the commutative diagram
![[Cohomology-1761701616116.png|700]]


# Homotopy Invariance

If we have $f \simeq g: (X,A)\to (Y,B)$, then we get $f^*=g^*: H^n(Y,B)\to H^n(X,A)$

# Excision Theorem

$Z \subset A \subset X$ such that $\bar{Z}\subset \text{int }A$, then 
$i:(X-Z,A-Z) \hookrightarrow(X,A)$ induces 
$i^*: H^n(X,A;G)\overset{\cong}{\longrightarrow} H^n(X-Z,A-Z;G)$  $\forall n$

# Axioms 
Let $(X,A)$ be a CW-pair

1. Have a long exact sequence: $$\cdots \overset{}{\longrightarrow}\widetilde{H}^n(X/A)\overset{}{\longrightarrow}\widetilde{H}^n(X)\overset{}{\longrightarrow}\widetilde{H}^n(A)\overset{}{\longrightarrow}\widetilde{H}^{n+1}(X/A)\overset{}{\longrightarrow}\cdots$$
2. If $X = \bigvee_\alpha X_\alpha$, then
   $\pi_\alpha i_\alpha^*: \widetilde{H}^n(x)\overset{\cong}{\longrightarrow} \prod_\alpha \widetilde{H}^n(X_\alpha)$  $\forall n$


# Simplicial Cohomology Groups

Let $X = \Delta$-complex, $A \subseteq X$ a subcomplex, Then 
$$\Delta^n(X,A;G):= \text{Hom}(\Delta_n(X,A);G)$$
This gives $H^{n}_\Delta(X,A;G)$.

We know that $H_n^\Delta(X,A)\cong H_n(X,A;G)$  $\forall n$.
Then by Corollary 3.4
$$H^n(X,A;G)\cong H_\Delta^n(X,A;G)\quad \forall n$$


# Reduced Cohomology Groups

Look at the augmented chain complex 
$$\cdots \overset{}{\longrightarrow}C_1(X) \overset{}{\longrightarrow}C_0(X) \overset{\varepsilon}{\longrightarrow} \mathbb{Z}\overset{}{\longrightarrow}0$$
induces a cochain complex from which we can get $\widetilde{H}^n(X;G)$, giving
$$\widetilde{H}^n(X;G) \cong H^n(X;G) \quad \forall n >0$$
and $\widetilde{H}^0(X;G) \cong \text{Hom}(\widetilde{H}_0(X),G)$ = "functions that are constant on path-connected components of $X$ to $G$".
We have the familiar result
$$H^0(X;G) \cong \widetilde{H}^0(X;G) \oplus \underbrace{\text{im }\varepsilon^*}_{\cong G}$$

# Relative Cohomology Groups

Recall that for $A \subseteq X$,
$$0 \overset{}{\longrightarrow}C_n(A) \overset{i}{\longrightarrow}C_n(X) \overset{j}{\longrightarrow} \underbrace{C_n(X,A)}_{\cong C_n(X)/C_n(A)}$$
For the Cohomology equivalent define
$$C^n(X,A;G) := \text{Hom}(C_n(X,A), G)$$
as "functions from singular n-cells in $X$ to $G$ that vanish on simplices in $A$"

Hence we get the chain complex
$$0 \overset{}{\longleftarrow}C^n(A) \overset{i^*}{\longleftarrow}C^n(X)\overset{j^*}{\longleftarrow}C^n(X,A)\overset{}{\longleftarrow}0$$
which implies $C^n(X,A;G)$ is a subgroup of $C^n(X;G)$.
$\delta_n:C^n(X,A;G) \to C^{n+1}(X,A;G)$ which induces $H^n(X,A;G)$ and the long exact sequence
$$\cdots \overset{}{\longleftarrow}H^{n+1}(X,A;G)\overset{}{\longleftarrow}H^n(A;G)\overset{}{\longleftarrow}H^n(X;G)\overset{}{\longleftarrow}H^n(X,A;G)\overset{}{\longleftarrow}\cdots$$
and similarly for the reduced versions.

From the Universal Coefficient Theorem we get the following commutative diagram:
![[Cohomology-1764156596170.png|450]]


# Cellular Cohomology

![[Cohomology-1764156772653.png]]
where $d_n:=\delta_nj_n$ (different from cellular homology)

so $H^n_{CW}:= \ker d_n/\text{im }d_{n-1}$.

>[!Theorem] H Theorem 3.5
>1. $H^n(X;G) \cong H^n_{CW}(X,;G)$   $\forall n$
>2. Cellular cochain complex $\{H^n(X^n,X^{n-1}),d_n\}$ is isomorphic to the chain complex $\{\text{Hom}(H_n(X^n,X^{n-1}); G), d_n\}$ 
>3. $H^k(X^k,X^{k-1};G) \cong \text{Hom}(H_k(X^k,X^{k-1}),G)$  $\forall k$


# Mayer-Vietoris Sequence
## Absolute Case

$X = \text{int} A \cup \text{int} B$. 
$$0 \overset{}{\longrightarrow}C^n(A+B;G)\overset{\Psi}{\longrightarrow} C^n(A;G)\oplus C^n(B;G)\overset{\Phi}{\longrightarrow}C^n(A\cap B;G)\overset{}{\longrightarrow}0$$
is an exact sequence which gives 
$$\cdots \overset{}{\longrightarrow}H^n(X;G) \overset{\Psi}{\longrightarrow}H^n(A;G)\oplus H^n(B;G)\overset{\Phi}{\longrightarrow}H^n(A\cap B;G)\overset{}{\longrightarrow}H^{n+1}(X;G)\overset{}{\longrightarrow}\cdots$$

## Relative Case

Let $X = \text{int } A \cup \text{int }B$  and $Y = \text{int }C \cup \text{int }D$. 
Then we have the exact sequence
$$0 \overset{}{\longrightarrow}C^n(A+B,C+D;G)\overset{\Psi}{\longrightarrow} C^n(A,C;G)\oplus C^n(B,D;G)\overset{\Phi}{\longrightarrow}C^n(A\cap B,C \cap D;G)\overset{}{\longrightarrow}0$$
which gives 
$$\cdots \overset{}{\longrightarrow}H^n(X,Y;G) \overset{\Psi}{\longrightarrow}H^n(A,C;G)\oplus H^n(B,D;G)\overset{\Phi}{\longrightarrow}H^n(A\cap B, C \cap D;G)\overset{}{\longrightarrow}\cdots$$


# Cohomology Ring

>[!Definition] Cohomology Ring
>The **cohomology ring** is $H^*(X;R) = \bigoplus_{n \geq 0} H^n(X;R)$.
>The elements are $\sum_{i\geq 0}^n\alpha_i$ for $\alpha_i \in H^i(X;R)$.

- $\sum_i \alpha_i + \sum_j \beta_j = \sum_k(\alpha_k + \beta_k)$
- $\sum_i\alpha_i \times \sum_j \beta_j = \sum_k(\sum_{i+j=k} \alpha_i\smile \beta_j)$

>[!Proposition] 
>$H^*(X;R)$ is a graded ring


# Cross Product

>[!Definition] Cross Product
>The **cross product** or **external cup product** is 
>$$H^*(X;R)\times H^*(Y;R)\overset{}{\longrightarrow}H^*(X\times Y;R)\quad (a,b)\longmapsto p_1^*(a)\smile p_2^*(b)$$
>where $p_1^*:H^*(X)\to H^*(X\times Y)$ and $p_2^*$ similarly but for $Y$. 
>Each $p_i$ are projections coming from $X \times Y$
>

- This map is generally NOT an isomorphism, but replacing it with a tensor product does work.

>[!Theorem] H Theorem 3.14 Kunneth Formula
>Let $X,Y$ be CW-complexes. Assume $H^k(Y;R)$ is a finitely generated free $R$-module for all $k$. 
>Then the (cross) tensor product map $$ H^*(X;R)\otimes H^*(Y;R)\overset{\psi}{\longrightarrow}H^*(X\times Y;R)$$
>is an isomorphism.

