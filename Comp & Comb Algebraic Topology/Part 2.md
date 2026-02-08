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

