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