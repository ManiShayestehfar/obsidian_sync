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
	Dual of a short exact sequence is not always exact

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

1. Have a long exact sequence:
   $$\cdots \overset{}{\longrightarrow}\widetilde{H}^n(X/A)\overset{}{\longrightarrow}\widetilde{H}^n(X)\overset{}{\longrightarrow}\widetilde{H}^n(A)\overset{}{\longrightarrow}\widetilde{H}^{n+1}(X/A)\overset{}{\longrightarrow}\cdots$$
2. If $X = \bigvee_\alpha X_\alpha$, then
   $\pi_\alpha i_\alpha^*: \widetilde{H}^n(x)\overset{\cong}{\longrightarrow} \prod_\alpha \widetilde{H}^n(X_\alpha)$  $\forall n$




# Simplicial Cohomology Groups

Let $X = \Delta$-complex, $A \subseteq X$ a subcomplex, Then 
$$\Delta^n(X,A;G):= \text{Hom}(\Delta_n(X,A);G)$$
This gives $H^{n}_\Delta(X,A;G)$.

We know that $H_n^\Delta(X,A)\cong H_n(X,A;G)$  $\forall n$.
Then by Corollary 3.4
$$H^n(X,A;G)\cong H_\Delta^n(X,A;G)\quad \forall n$$


