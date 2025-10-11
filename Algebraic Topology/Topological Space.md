>[!def] 
>Set $X$ with collection of subsets $\tau$ s.t
>1. $\emptyset, X \in \tau$ 
>2. Arbitrary union of sets from $\tau$ is in $\tau$
>3. Finite intersection of sets from $\tau$ is in $\tau$

Elements of $\tau$: open sets, $V \subseteq X$ is **closed** if $X\backslash V \in \tau$.

# Examples

## Subspace Topology

If $(X,\tau_x)$ is a topological space, and $Y \subseteq X$, then the **subspace topology** on $Y$ is $\tau_Y = \{U\cap Y | u \in \tau_x\}$

## Product Topology

$X \times Y = \{(x,y) | x \in X, y \in Y\}$ has a **product topology** with base $\{U \times V|U \in \tau_x, V \in \tau_y\}$/
e.g. $\mathbb{R}^2 = \mathbb{R} \times \mathbb{R}$

## Quotient Topology

Suppose we have an equivalence relation $\sim$ on $X$ with equivalence class $[x]$. Define $Y := X/\sim = \{[x] \:|\: x \in X\}$ "set of all equivalence classes".  

# Compactness

>[!def] 
>$(X,\tau)$ is **compact** if every open cover has a finite subcover. i.e. if $X = \bigcup_{i \in I} u_i$ for $u_i \in \tau$, then there exists $i_1,...,i_n \in I$ such that $X = \bigcup_{i=1}^n u_i$

## Heine-Borel

>[!thm]
>$Y \subseteq \mathbb{R}^n$ is compact $\iff$ it is closed + bounded


# Hausdorff

>[!def] 
>A Top space is **Hausdorff** if $\forall x,y \in X$, $\exists U,V \in \tau$ such that $x \in U, y \in V$, and $U \cap V = \emptyset$.
>
- Any metric space is Hausdorff as we can use the metric to find the distance between two points and construct non-intersecting balls centered at those points.

# Connectedness & Path-Connectedness

>[!def] 
>A Top space is **connected** if it cannot be expressed as a disjoint union of two non-empty open subsets.

- e.g. $S^0$ is not connected, but for $n\geq 1$ $S^n$ is connected

>[!def]
>A **path** $p$ in $X$ is a [[Continuity (Top)|continuous]] map $p:[0,1] \to X$

>[!thm] 
>$X$ is **path-connected** if $\forall x,y \in X$, there exists a path $p$ in $X$ with $p(0)=x$ and $p(1)=y$.

- Path connected $\implies$ connected


# Homeomorphism

>[!def] 
>$f:X\to Y$ is a **homeomorphism** if:
>1. $f$ is continuous
>2. $f$ is bijective
>3. $f^{-1}$ is continuous

- if there exists such a homeomorphism, then $X \cong Y$.


# Union

>[!def]
>$X \sqcup Y$ the **disjoint union** forms the topology $\tau_{X\sqcup Y} = \{U \sqcup V \:|\: U \in \tau_x, V \in \tau_Y\}$


# Cone

>[!def] 
>The **cone** of $X$ is $CX= (X \times [0,1]) / (X \times \{1\})$


# Suspension

>[!def] 
>$SX = (X \times [-1,1]) / (X\times \{1\}, X \times \{-1\})$


# Join

>[!def] 
>$X * Y$ joins every point of $X$ to every point of $Y$.
>$X * Y = X \times Y \times [0,1] / \sim$
>- $(x,y,0) \sim (x,y',0)\quad\quad \forall x\in X, y,y' \in Y$
>- $(x,y,1) \sim (x',y',1)\quad\quad \forall x,x'\in X, y \in Y$
>  
>  We also have associativity: $(X*Y)*Z = X*(Y*Z)$


# Wedge Sum

>[!def]
>Fix $x_0 \in X$, $y_0\in Y$. $X \vee Y = X \sqcup Y / (x_0=y_0)$ 


# Direct Product

>[!def] 
>The **direct product** $\prod_{i \in I} G_i$ is the group with elements $g: I \to \sqcup_{i \in I} G_i$  such that $g(i) \in G_i$ for all $i \in I$, and group operation defined by $(gh)(i) = g(i)h(i)$.

i.e. the multiplication is component-wise

>[!def]
>The **direct sum** $\bigoplus_{i\in I}G_i$ is defined similarly with the extra requirement that $g(i)=1$ for all but finitely many $i \in I$.

For *finite* $I$, the direct sum and product are equivalent.


# Simply-Connected

>[!def] Simply-Connected
>For $X$ path-connected, $X$ is **simply-connected** if $X$ is path connected and $\pi_1(X)\cong 1$.


# Locally Path-Connected

>[!def] 
>$X$ is **locally path-connected** if for all $x \in X$ and all open neighbourhoods $U$ or $x$, there exists an open neighbourhood $V$ of $x$ with $V \subseteq U$ such that $V$ is path-connected.
>![[Pasted image 20251007123350.png|300]]



# Semi-locally simply-connected

**Recall:** Simply connected $\implies$ path-connected + trivial $\pi_1$ 

>[!def]
>A space $X$ is **semi-locally simply-connected** if every $x \in X$ has an open neighbourhood $U$ such that the map $\pi_1(U,x) \to \pi_1(X,x)$ induced by $U \hookrightarrow X$ has trivial image. 
>i.e. every loop in $U$ based at $x$ is nullhomotopic in $X$.

## Examples

$S^1$ 

## Non-examples

Hawaiian earring embedded in $\mathbb{R}^2$ 

## Properties

>[!lemma] 
>If $X$ has a simply-connected covering space $\widetilde{X}$, then $X$ is semi-locally simply-connected.
##### Proof

==DO THE PROOF==


# Good Pair

>[!def]
>$A \subseteq X$. Say $(X,A)$ is a **good pair** if $A$ is 
>1. non-empty
>2. closed
>3. DR of some open set in $X$

## Examples

1. $X =D^n, \:\: A=\partial D^n = S^{n-1}$
2. $X$ a CW-complex, $A$ a non-empty subcomplex

