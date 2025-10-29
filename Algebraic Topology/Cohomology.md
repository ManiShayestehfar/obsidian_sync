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
>$$\delta: C^n(X;G)\to C^{n+1}(X;G)$ via $\phi \to \phi \circ \partial$$
>i.e. $\delta(\phi(\sigma)) = \sum_{i}(-1)^i \phi(\sigma|_{[v_0,...,\hat{v_i},...,v_n]})$

- $\delta^2 = 0$

>[!def] Singular Cohomology groups with coefficients in $G$
>$$H^n(X;G):=\ker\delta/\text{im }\delta$$ at $C^n(X;G)$, in the cochain complex
>$$\cdots \overset{}{\longleftarrow}C^1(X;G)\overset{\delta}{\longleftarrow}C^0(X;G)\overset{\delta}{\longleftarrow}0$$
>


