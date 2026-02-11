![[Part 2-1770464474695.png|500]]
# $\varepsilon$-Thickening

Given $\{x_1,...,x_n\}=X$ in a metric space, we can construct $$X^\varepsilon = \bigcup_{x\in X}B(x,\varepsilon)$$
- **Q:** Is it possible to select $\varepsilon >0$ such that $X^\varepsilon \cong \mathcal{M}?$
	- How to compute the homology of $X^\varepsilon$? Yes under assumptions


# Filtrations

## Vietoris-Rips

Let $(M,d)$ be a finite metric space. $VR_\varepsilon(M)$ is defined as follows:

A set $\{x_0,x_2,...,x_k\}\subset M$ forms a $k$-simplex iff $d(x_i,x_j)\leq \varepsilon$ for all $i,j$.

## Cech

$M$ a finite subset of metric space $(Z,d)$. $C_\varepsilon(M)$ is defined as $\{x_0,...,x_k\}$ form a $k$-simplex iff $\exists z \in Z$ such that $d(z,x_i) \leq \varepsilon$.

i.e. $$C_\varepsilon = \left\{\sigma \subseteq X \:|\: \bigcap_{x\in \sigma} B(x,\varepsilon)\neq \varnothing\right\}$$
- This just the nerve of $X^\varepsilon$


>[!theorem]
>$C_\varepsilon \subset VR_{2\varepsilon}\subset C_{2\varepsilon}$


# Persistence Module

An $\mathbb{N}$-indexed **persistence module** over a field $\mathbb{F}$ (for us mostly $\mathbb{Z}_2$) is a sequence $(V_\bullet,a_\bullet)$ of $\mathbb{F}$-vector spaces and linear maps between them
$$V_0 \overset{a_0}{\longrightarrow}V_1 \overset{a_1}{\longrightarrow}V_2 \overset{a_2}{\longrightarrow}V_3 \overset{a_3}{\longrightarrow}\cdots$$
- *Example:* Every cochain complex is a persistence module
- A persistence module is **finite** if $\dim V_i < \infty$ for all $i$ and $a_i$ are isomorphisms for $i >0$. 
	-E.g. Persistence module obtained by taking the homology of a filtration for finite simplicial complex

## Direct Sum

Direct sum of $(V_\bullet, a_\bullet),(W_\bullet, b_\bullet)$ is $(V_\bullet \oplus W_\bullet, a_\bullet \oplus b_\bullet)$ 

## Indecomposable

A persistence module $(I_\bullet, c_\bullet)$ is **indecomposable** if $(I_\bullet, c_\bullet) \cong (V_\bullet, a_\bullet) \oplus (W_\bullet, b_\bullet)$ such that one of the factors is isomorphic to $(I_\bullet, c_\bullet)$ and the other is trivial.

## Indecomposability of Interval Modules

Let $(I_\bullet, c_\bullet)$, non-zero $\mathbb{N}$-indexed. 
If there exists two indices, $i \leq j$ and $j \in \mathbb{N}\cup \{\infty\}$ such that
$$\dim I_p = \begin{cases}
1 & i \leq p \leq j \\[3pt]
0 & \text{otherwise}
\end{cases}$$
and $$\text{rank }(c_p: I_p \to I_{p+1}) = \begin{cases}
1 & i \leq p \leq j  \\[2pt]
0 & \text{otherwise}
\end{cases}$$then $(I_\bullet, c_\bullet)$ is indecomposable.

>[!proof] 
> Recall that if $I_\bullet \cong V_\bullet \oplus W_\bullet$, then $\text{End }I_\bullet$ only contains a non-trivial idempotent $e$. 
> 
> Hence we just need to show that $\text{End }I_\bullet$ has only the idempotents $0$ and $\text{id}$.




# Persistent Group

*Terminology:* $a_{j-1}\circ a_{j-2}\circ ...\circ a_i: V_i \to V_j$

For $i,j \in \mathbb{N}$, $j \geq i$. The **persistent homology group** of the persistence module $(V_\bullet,a_\bullet)$ is the subspace of $V_j$ given by $$PH_{ij}(V_\bullet,a_\bullet) = \text{im }(a_{ij})\subset V_j$$
- $PH_{ij}(V_\bullet,a_\bullet) \subset PH_{i'j}(V_\bullet,a_\bullet)$ for $i' \geq i$

## Birth & Death

Given $(V_\bullet,a_\bullet)$, $v\in V_i$ is 
- **born at filtration index $i$** if $v \not\in \text{im }a_{i-1}$,
- **die at filtration index $j \geq i$** if $j$ is the smallest index such that $a_{ij}(v)=0$.
	- If $a_{ij}(v) \neq0$, then death time of $v$ is $+\infty$. 

### In terms of Simplex Filteration

$[\alpha] \in H_k(FK_i)$ is **born** at index $i$ and **died** at index $j$ if and only if there exists $\sigma_i,\sigma_j$ creating/undoing the homology class of only $[\alpha]$.

## Persistence Homology from Filtration

$PH_{k}^i(FK)$ consists of homology classes $H_k(F_iK)$ that continue to generate non trivial homology in $H_k(F_jK)$

![[Part 2-1770466744678.png|600]]


# Simplex-wise Filtration

$(FK_i)_{i \in I}$ for $I$ a subset of $\mathbb{Z}$ such that $FK_i = FK_{i-1}\cup \sigma_i$


# Barcodes

A morphism between persistence modules $(V_\bullet,a_\bullet)$ and $(W_\bullet, b_\bullet)$ is a family of linear maps $\phi_k: V_k\longrightarrow W_k$ such that $b_i \circ \phi_i = \phi_{i+1}\circ a_i$ 

![[Screenshot 2026-02-08 at 9.58.42 am.png|600]]

- if all $\phi_i$ are isomorphisms then the morphism is an isomorphism of persistence modules.
	- So $(V_\bullet,a_\bullet) \cong (W_\bullet, b_\bullet)$ form categories.


# Interval Module

For all $0 \leq i \leq j \leq \infty$, the $\mathbb{N}$-indexed persistence module $(I_\bullet^{i,j}, c^{ij}_\bullet)$ is given by 
$$I_p^{i,j} = \begin{cases}
\mathbb{F} & i \leq p \leq j  \\[3pt]
0 & \text{otherwise} 
\end{cases}$$
$$c_p^{ij} = \begin{cases}
\text{id}_\mathbb{F} & i \leq p \leq j  \\[3pt]
0 & \text{otherwise}
\end{cases}$$
is called the **interval module**.


# Structure Theorem 

$(V_\bullet,a_\bullet)$ a finite-type $\mathbb{N}$-indexed persistence module. There exists a set $Bcd(V_\bullet,a_\bullet)$ of integer pairs $0 \leq i \leq j \leq \infty$ with $(i \neq \infty)$ and $\mu: Bcd(V_\bullet,a_\bullet) \to \mathbb{N}_{>0}$  such that 
$$(V_\bullet,a_\bullet) \cong \bigoplus _{i,j} (I_\bullet^{i,j}, c_\bullet^{ij})^{\mu(i,j)}$$
which is unique up to isomorphism.

>[!proof]
>
>Let $(V_\bullet,a_\bullet)$ is of finite type. 
>Then there exists $n>0$ such that $a_i:V_i\to V_{i+1}$ for all $i > n$. Consider $V = \bigoplus_i^nV_i$, and the linear map $t: V \to V$ given by $t(v_0,...,v_n) = (0,a_0(v_0),...,a_{n-1}(v_{n-1}))$.
>
>This gives $V$ a structure of a finitely generated $\mathbb{F}[t]$-module.
>
>Since $\mathbb{F}$ is a field, then $\mathbb{F}[t]$ is a PID and so we have a structure theorem of finitely generated modules over a PID: $V = \text{Free Part} \oplus \text{Torsion}$
>
>The free part is a direct sum of $\mathbb{F}[t]$-modules of the form $(t^i) \mathbb{F}[t]$ for some $i \geq 0$. Each summand is isomorphic to $(I_\bullet^{i,\infty}, c_\bullet^{i\infty})$
>The torsion part is direct sum of the form $(t^i) \mathbb{F}[t]/ (t^j)$. Each summand is isomorphic to $(I_\bullet^{i,j}, c_\bullet^{ij})$
>
>
>


## Example

![[Part 2-1770529860680.png|600]]
![[Part 2-1770534670514.png|400]]


# Generalisation of Persistence Modules

- In Category theory language a persistence module is a function $M: (X,\leq) \longrightarrow \textbf{Vec}_k$, where $(X,\leq)$ is a totally ordered set
	- *why not a poset?* We can actually use a poset lol. E.g. $\mathbb{N} \times \mathbb{N}$ or $\mathbb{R} \times \mathbb{R}$

## PM with Posets

- Functor $F: P \to \textbf{Top}$ (simplicial complexes) such that $x \leq y \implies F_x \leq F_y$. We call this a **filtration**.
- The $P$-indexed persistence module then is $M: P \to \textbf{Vec}_k$

- Structure Theorem BREAKS!
### Structure Theorem Replacement

Take $M: P \to \textbf{Vec}_k$. 
If $M$ is pointwise finite-dimensional, then $$M \cong \bigoplus_{d \in \Omega}M^d$$ where $M^d$ is indecomposable, and the direct sum is unique up to isomorphism.
  
### Good Barcode

$B$ is a multiset of subsets of $P$. Then $B$ is a **good barcode** if 
$$\forall \: x \leq y \in P,\quad \text{rank }(M_x \to M_y) = |\{S \in B \::\: x,y \in S\}|$$
for vector spaces $M_x,M_y$.

![[Part 2-1770638115265.png|600]]



# Stability Theorem

"We want the properties of a perturbation of a point cloud to be comparable and similar to the initial point cloud."

![[Part 2-1770638401683.png|400]]


## $\mathbb{R}_+$- Persistence Module

An $\mathbb{R}_+$-Persistence module is $(V_\bullet,a_\bullet)$ where:
- $V_t$ is a $\mathbb{F}$-vector space $\forall t \in \mathbb{R}_+$
- $a_{t \leq s}: V_s \to V_t$  whenever $t \leq s$
	- $a_{t\leq t}$ is the identity + composition is well-defined

As for $\mathbb{N}$-PM, $\mathbb{R}_+$-PM are also functors $(\mathbb{R}_+, <) \to \textbf{Vec}_k$

![[Part 2-1770639029040.png|500]]

The $\mathbb{R}_+$-persistence module $M$ is **tame** if 
1. $V_t$ is finite-dimensional for all $t\geq 0$
2. Only finitely many $t \geq 0$ such that $a_{t-\varepsilon\leq t+\varepsilon}$ is NOT an isomorphism

## Interval Modules

 We can define interval modules $(I_\bullet^{t_i,t_j}, c_\bullet^{t_it_j})$ supported on $[t_i,t_j]$ as
 $$I_t^{t_i,t_j} = \begin{cases}
\mathbb{F} & t_i \leq t \leq t_j  \\
0 & \text{otherwise}
\end{cases}\quad\quad \text{and}\quad\quad c_{s\leq t}^{t_it_j} =\begin{cases}
\text{id}_\mathbb{F} & [s,t] \subseteq [t_i,t_j]  \\
0 & \text{otherwise}
\end{cases}$$


## Structure Theorem (for tame $\mathbb{R}_+$- PM)

$$(V_\bullet,a_\bullet) \cong \bigoplus_{[s,t]}(I_\bullet^{s,t}, c_\bullet^{\mu(s,t)})\quad \text{for}\quad [s,t] \in Bar(V_\bullet,a_\bullet)$$

### $\varepsilon$-interleaving

For every $\varepsilon \geq 0$, an **$\varepsilon$-interleaving** between $(V_\bullet,a_\bullet)$ and $(W_\bullet,a_\bullet)$ consists of two families of maps $\{\phi_t:V_t \to W_{t + \varepsilon}\}$ and $\{\psi_t:W_t \to V_{t+\varepsilon}\}$ such that
1. $\phi_t \circ a_{s\leq t} = b_{s+\varepsilon,t+\varepsilon}\circ \phi_s$
2. $\psi_t \circ b_{s\leq t} = a_{s+\varepsilon,t+\varepsilon}\circ \psi_s$
   
   ![[Part 2-1770677964059.png|500]]

3. $\psi_{t+\varepsilon} \circ \phi_t = a_{t\leq t+ 2\varepsilon}$
4. $\phi_{t+\varepsilon} \circ \psi_t = b_{t\leq t+ 2\varepsilon}$
   
   ![[Part 2-1770677992150.png|500]]

$$\implies \text{A $0$-interleaving is an isomorphism between $V$ and $W$}$$

### Interleaving Distance

The **interleaving distance** $d_I((V_\bullet,a_\bullet), (W_\bullet,a_\bullet))$ is defined as the $\inf_\varepsilon$ such that there exists a $\varepsilon$-interleaving between $V,W$.

#### Proposition

$P,Q$ point clouds in $\mathbb{R}^n$ and let them be "close", meaning:
- $\exists\: \bar{q}\in Q$ such that $d(p,\bar{q})\leq \varepsilon$, $\forall p \in P$ 
- $\exists\: \bar{p} \in P$ such that $d(\bar{p},q)\leq \varepsilon$, $\forall q \in Q$

Then $\forall k\geq0$ the $k$-th persistence homology modules of $VR(P)$ and $VR(Q)$ are $2\varepsilon$-interleaved

>[!proof]
>By assumption we have $\alpha:P \to Q,\beta:Q\to P$ such that $\|p-\alpha(p)\|\leq \varepsilon \: \forall p \in P$ and $\|q-\beta(q)\|\leq \varepsilon \: \forall q \in Q$ where $\|\cdot\|$ is the Euclidean norm.
>
>These induce simplicial maps $\{\alpha_t: VR_t(P) \to VR_{t + 2\varepsilon}(Q)\:|\: t \geq 0\}$ and $\{\beta_t: VR_t(Q) \to VR_{t + 2\varepsilon}(P)\:|\: t \geq 0\}$.
>Why? If $\|p-p'\|\leq t\implies \|\alpha(p)-\alpha(p')\|\leq t + 2\varepsilon$. Similarly for $\beta$
>
>$\alpha_t^*,\beta_t^*$ maps induced in homology define a $2\varepsilon$-interleaving
>
>Same holds for other filtrations as well.


###  $\varepsilon$-matching

Consider $(V_\bullet,a_\bullet)$ and its barcode $Bar(V_\bullet,a_\bullet)$. This is a multiset of intervals $[s,t]\subseteq \mathbb{R_+} \cup \{\infty\}$.

For $\varepsilon \geq 0$, an **$\varepsilon$-matching** between multisets $B,B'$ of intervals is a bijection $\rho:B_0\to B_0'$  where $B_0\subset B$ and $B_0'\subset B'$ such that
- Every $[s,t]$ in $(B\setminus B_0)\cup (B'\setminus B_0')$ has length $t-s \leq 2\varepsilon$
- If $\rho([s,t]) = [s',t'] \implies$ $|s-s'|\leq \varepsilon$ and $|t-t'|\leq \varepsilon$

### Bottleneck Distance

The **Bottleneck distance** $d_B(B,B')$ is the $\inf_\varepsilon$ such that there exists a $\varepsilon$-matching between $B,B'$

#### Theorem

For all $(V_\bullet,a_\bullet), (W_\bullet,b_\bullet)$ tame, then $d_I((V_\bullet,a_\bullet), (W_\bullet,b_\bullet)) = d_B(Bar(V_\bullet,a_\bullet), Bar(W_\bullet,b_\bullet))$


 ![[Part 2 (Agnese)-1770681212937.png|450]]
 ![[Part 2 (Agnese)-1770681280927.png|450]]


### Wasserstein Distance

Let $D,D'$ be persistence diagrams. The **Wasserstein Distance** is defined as

$$d_{W,P}(D,D') = \min_{m \in M(D,D')} \left(\sum_{(a,b)\in m} \|a-b\|_p^p \:+\: \sum \|s - \text{proj}_\Delta(s)\|_p^p\right)^{1/p}$$
where $M(D,D')$ is set of matchings, $\Delta$ is the diagonal and the second term's sum is taken over all points in both $D,D'$ that are not paired by a matching.
- So the first sum is over matchings and the second sum is on unmatched points.

1. $d_{W,P}$ offers a setting that allows to define "barycentres" of persistence diagrams
2. The "winning" matching (i.e. the one realising the distance) defines a way of matching the corresponding homology classes.


# Persistent Landscapes

1. Given an $\mathbb{R}_+$-indexed persistent module $(V_\bullet,a_\bullet)$, we define $\lambda: \mathbb{N}\times \mathbb{R} \to \mathbb{R}$ by $$ \lambda(k,t) = \sup\left\{h \geq 0 \:|\: \text{rank }(a_{t-h\leq t+h}) \geq k\right\}$$
2. Equivalently, take the barcode for $(V_\bullet,a_\bullet)$, say $B = \{I_{ij}\}$. Then $$\lambda(k,t) = \sup\{h \geq 0 \:|\: [t-h,t+h]\subseteq I\:\:\text{for at least $k$ distinct intervals}\}$$
3. Equivalently, consider now a persistence diagram $D= \{(a_i,b_i)\}_{i \in I}$. For $a<b$, $f_{(a,b)}(t) = \max(0, \min(a+t,b-t))$.
   Then $$\lambda(k,t) = k\max\{f_{(a_i,b_i)}(t)\}_{i \in I}$$
   where $k\max$ is the $k$-th largest element.

- A landscape is a degree of functions

-  $\lambda_1,\lambda_2,...:\mathbb{R} \to \mathbb{R}$ are piecewise linear maps with slope $-1,0,1$. Then the **critical points** of $\lambda_k$ are those values where the slope changes

>[!theorem]
>$$\text{Diagrams} \cong \text{Landscapes}$$


## Example

Given a persistence diagram
![[Part 2 (Agnese)-1770811338250.png|250]]

First rotate the diagram
![[Part 2 (Agnese)-1770811376024.png]]

Then $\lambda(k,t)$ is
![[Part 2 (Agnese)-1770811902514.png|450]]


## Average Landscapes
$$\bar{\lambda}(k,t) = \frac{1}{n}\sum_{j=1}^n\lambda^{(j)}(k,t)$$
- The average is NOT necessarily a persistent diagram


# PH-Hypergraphs

*Motivation:* How can we systematically compute cycles generating PH classes? 
*Solutions:* What if we look at a generating cycle for all classes of our persistent diagram and "collate" them into a single structured object?

## Definition

From a point cloud, get its persistence homology and a choice of generating cycle for each class. Then the **PH-hypergraph** consists of
- Vertices as points in the point clouds
- For every cycle, you can add a hyperedge containing the vertices forming the cycle