
# Simplicial Complex

$n \in \mathbb{N}$, $[n] := \{0,1,...,n-1\}$. A **simplicial complex** $X$ on $[n]$ is $X \subseteq \mathcal{P}([n])$ such that if $\sigma \in X$ and $\tau \subset \sigma \implies \tau \in X$.

## SCPX Example

- Standard $n$-simplex $\Delta^n = \mathcal{P}([n+1])$ with $\partial\Delta^n = \Delta^n \setminus \{01...n\}$
- Simple graphs (e.g. no self-loops or multi edges)

## Simplicial Map

A **simplicial map** is a (set) map $f: V(X_1) \to V(X_2)$ such that if $\sigma$ is a simplex in $X_1\implies$ $f(\sigma) \in X_2$.
- It should respect identity, composition, and inclusion

*Q:* If $f$ is bijective and simplicial, then is $f^{-1}$ simplicial always? *NO!* e.g
![[Part 1 (Daniele)-1771021556225.png|200]]

## Geometric Simplex

Let $\{x_0,...,x_k\}\subseteq \mathbb{R}^n$ be *affinely independent*. That is, $\{(x_i-x_0)_{i=1,...,k}\}$ is linearly independent.

A **Geometric simplex** spanned by $\{x_0,...,x_k\}$ is $$\left\{ \sum_{i=0}^n t_ix_i \:|\: t_i\geq 0\:,\: \sum_{i=0}^nt_i=1\right\}$$

## Geometric Realisation

Fix $\phi: V(X) \to \mathbb{R}^n$. The **Geometric Realisation** of $X$ w.r.t. $\varphi$ is the union
$$|X|_\phi = \bigcup_{\sigma \in X} |\sigma|_\phi$$ where each $|\sigma|_\phi$ is the geometric simplex spanned by vertices $\langle\phi(v_0), ...,\phi(v_k)\rangle$

- Assume $\phi$ is an **Affine Embedding** e.g. It is injective and $\phi(V(X))$ is affinely independent.
- So the topology should be independent of $\phi$

### Proposition

If $\phi_0,\phi_1$ are affine embeddings of $X \to \mathbb{R}^N$, then $|X|_{\phi_0} \overset{homeo}{\cong}|X|_\phi$


### Links & Stars

$X$ a scpx, $\sigma \in X$. 

- The **Link** of $\sigma$ is $\ell k(\sigma) = \{\tau \in X \:|\: \tau \cap \sigma = \varnothing\:,\:\sigma \cup \tau \in X\}$
- The **Open star** of $\sigma$ is $St(\sigma)= \{\tau \in X \:|\: \sigma \subseteq \tau\}$
- The **Closed star** of $\sigma$ is $\overline{St}(\sigma) = \{\tau \in X \:|\: \tau \cup \sigma \in X\}$
	- $\overline{St} = St \cup \ell k$


# Homology

- Just refer to my notes in [[Simplicial Homology]].

- Just remember that $[\partial_k]\in R^{n_{k-1} \times n_k}$  where $n_k$ is the number of $k$-simplices in the simplicial complex

- **Homotopy Invariant:** $|X| \simeq |X'| \implies H_*(X;R)\cong H_*(X';R)$

#### Theorem

Let $X$ be a simply-connected simplicial complex.  $$\widetilde{H}_*(X;\mathbb{Z})\cong \begin{cases}
\mathbb{Z}^r & \ast = n  \\
0 & \text{otherwise}
\end{cases} $$
then $X \simeq \bigvee^r S^n$. 



# Subdivisions

**Proposition:** $|X| \cong |Sd(X)| \cong |Stellar(X)|$

*Q:* If $|X| \cong |X'|$, then is there a simplicial map $f:X\to X'$ up to subdivisions?
*Partial Answer:*

**Theorem (Brouwer):** Let $f:|X| \to |X'|$, then $\exists N \geq 0$ such that $\hat{f}: Sd^N(X) \to X'$ a simplicial map such that $\hat{f}\simeq f$.


# Triangulation

A **triangulation** of an $k$-manifold $M^k$ is a homeomorphism $t:|X| \to M$ for some finite scpx $X$.
- e.g. $D^n \longleftrightarrow|\Delta^n|$ and $S^n \longleftrightarrow |\partial\Delta^{n+1}|$

## Minimal Triangulation

Let $\cal{M}$ be the set of closed oriented connected $k$-manifolds. 
Then $\mu_k: \mathcal{M} \to \mathbb{N}$ given by $M \longmapsto \text{min \# of k-spx in a triangulation of } M$  

- This allows us to find minimal triangulations

## Euler Characteristic

$X$ a scpx. It's **Euler characteristic** is an invariant $$\chi(X) = \sum_{\sigma \in X}(-1)^{\dim \sigma} = \sum_{i=0}^{\dim X}(-1)^i c_i$$ where $c_i$ is the number of $i$-simplices in $X$.



# Posets

A **Poset** $(P,\leq)$ is a finite set with a relation $\leq$ such that 
1. $\forall x \in P, x \leq x$
2. $\forall x, y \in P$, $x \geq y$ and $y \geq x \implies x =y$
3. $\forall x,y,z \in P$, $x\geq y$ and $y \geq z \implies x \geq z$

- Write $x \dot < y$ if $y\geq x$ and $\not \exists z \neq y,x$ such that $y\geq z \geq x$
	- i.e. nothing in between

## Examples

- $(\mathbb{N},\leq),(\mathbb{N},|)$
- $S$ a set and $P$ a poset. $\text{Fun}(S,P)$ is a poset with $f \leq g \iff f(x) \leq g(x)\:\:\forall x \in S$
- Boolean poset $B(n)$ is a poset of subsets of $[n]$ ordered by $\subseteq$
  ![[Part 1 (Daniele)-1771032448834.png]]

## Face Posets

$\mathcal{F}:\text{SCPXs}\to \text{Posets}$ with $X \mapsto \mathcal{F}(X)$ where vertices of $\mathcal{F}(X)$ are simplices of $X$ and $\subseteq$ is face inclusion

![[Part 1 (Daniele)-1771032576597.png]]

#### Remarks

Face posets of $X$ is "graph representation" of the $(C_*(X), \partial)$ over $\mathbb{Z}_2$ where 
- Simplices $\longleftrightarrow$ elements in $\mathcal{F}(X)$
- $\partial \longleftrightarrow$ Poset (strict) containments $\dot <$
This only works for *thin posets*.

### Simplicial Map

$X$ a simplicial complex and $P$ a poset. We say a map $f: X\to P$ is **simplicial** if
- it sends $[n]$ to elements of $P$ and 
- simplices in $X$ to chains in $P$: $a_1 \geq a_2\geq a_3 \geq ... \geq a_k$

#### Quillen's Fiber Theorem

Let $f:X \to P$ be simplicial. If all fibers $f^{-1}(P_{\geq x})$ for $x \in P$ are contractible, then $X \simeq P$. i.e. $|X| \simeq |\Delta(P)|$.

## Poset Homology

Let $P$ be a poset that is 
1. **ranked:** $\exists \ell: P \to \mathbb{N}$ s.t. $x \dot < y \implies \ell(y) = \ell(x)+1$
2. **thin/square:** between every two $x,y$, there exists strictly $z,z'$ s.t. $x \:\dot >\: z,z'\:\dot >\: y$

Let $A$ be an abelian category. Then choose $F: P \to A$ and define $$C_F^n(P) = \bigoplus_{x\in P, \ell(x)=n} F(x),$$
and $$d_F^n: C_F^n(P) \longrightarrow C_F^{n-1}(P)\quad,\quad d_F^n = \sum_{x\in P,\ell(x)=n}\:\: \sum_{x'\in P,x \dot < x'} F(x \:\dot <\:x')$$Thus we can define the **poset homology of $P$ with coefficients $F$**:  $H_*(P;F)$


### Example
Let $P = \mathcal{F}(X)$,   $F_{\mathbb{Z}_2}: P \to \mathbb{Z}_2\text{Vect}$ the constant functor such that 
- $F_{\mathbb{Z}_2}(x) = \mathbb{Z}_2(x)\:\: \forall x \in P$,
- $F_{\mathbb{Z}_2}(x\to y)= \mathbb{Z}_2 \overset{\cong}{\longrightarrow}\mathbb{Z}_2$

Then $H_*(\mathcal{F}(X); F_{\mathbb{Z}_2}) \cong H_*(X;\mathbb{Z}_2)$

![[Part 1 (Daniele)-1771069682143.png]]




# Bordism

Given $X$ a top space, consider $CB_k(X) := \langle k-\dim \text{ submanifolds} \subseteq X\rangle / \sim$  
where $S_1 \sim S_2 \iff \exists W \subseteq X \times[0,1]$ s.t. $S_1\sqcup S_2 = \partial W$

![[Part 1 (Daniele)-1771036075844.png|400]]



# Presentation

Let $M$ be a finitely-generated R-module. 
A **presentation** for $M$ is a short exact sequence  $$R^s \overset{f}{\longrightarrow} R^t \overset{g}{\twoheadrightarrow}M \overset{}{\longrightarrow}0$$
- $\ker g$ gives relations for $M$

## Examples

![[Part 1 (Daniele)-1771037195191.png]]

- something about Smith Normal Form (See page 16-17 of notes)


# Fundamental Theorem of Finitely Generated Abelian Groups

$G$ a finitely-generated Abelian group. Then $$G \cong \mathbb{Z}^{n-k}\oplus \bigoplus_{i=1}^k \mathbb{Z}/ q_i\mathbb{Z}$$ where $q_i$s are powers of primes and $\text{rank }G = n-k$

Another use case is 
$$G \cong \mathbb{Z}^{n-k}\oplus \bigoplus _{i=1}^k \mathbb{Z}/\alpha_i\mathbb{Z}$$ where $\alpha_i |\alpha_{i+1}$ are invariant factors.



# Categories

See either my notes, or CCAT notes pages 19-21


# Combinatorial Alexander Duality

$X$ a simplicial complex over $[n]$.
It's **dual** $X^* =\{s \in \mathcal{P}([n]) \:|\: [n]\setminus s \not \in X\}$. 
	- $(X^*)^* = X$
Then $$\widetilde{H}_i(X;\mathbb{Z}_2) \cong \widetilde{H}^{n-i-3}(X^*;\mathbb{Z}_2)$$



# Cover

$X$ a top space. A **cover** of $X$ is $\mathcal{U} = \{U_i\}_{i \in I}$ such that $U_i$ are open and $X = \bigcup_{i \in I} U_i$

## Good

**Notation:** For $J \subseteq I$, call $U_J := \cap_{ j \in J} U_j$.

$\mathcal{U}$ is **good** if it is:
1. Locally finite
2. $U_J$ either empty or null-homotopic $\forall J \subseteq I$

### Remark

If $\mathcal{U}$ is good cover of $X$ $\implies H_*(N(\mathcal{U}); F_{\mathbb{Z}_2}) \cong H(X;\mathbb{Z}_2)$ 


### Examples

![[Part 1 (Daniele)-1771066922141.png]]
![[Part 1 (Daniele)-1771067032129.png|450]]

## Nerve 

The **nerve** $N(\mathcal{U})$ of the cover $\mathcal{U}$ is the simplicial complex with vertices the $U_i$'s and $k$-simplices the $U_J$ such that $U_J \neq \varnothing$ and $|J| = k+1$

### Nerve Theorem

Let  $\mathcal{U} = \{U_i\}_{i \in I}$ where $|I| < \infty$ be a good cover of $X$. Then $N(\mathcal{U})\simeq X$.


