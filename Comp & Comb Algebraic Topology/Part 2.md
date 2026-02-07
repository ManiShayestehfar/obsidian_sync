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


# Persistent Group

*Terminology:* $a_{j-1}\circ a_{j-2}\circ ...\circ a_i: V_i \to V_j$

For $i,j \in \mathbb{N}$, $j \geq i$. The **persistent homology group** of the persistence module $(V_\bullet,a_\bullet)$ is the subspace of $V_j$ given by $$PH_{ij}(V_\bullet,a_\bullet) = \text{im }(a_{ij})\subset V_j$$
- $PH_{ij}(V_\bullet,a_\bullet) \subset PH_{i'j}(V_\bullet,a_\bullet)$ for $i' \geq i$

## Birth & Death

Given $(V_\bullet,a_\bullet)$, $v\in V_i$ is 
- **born at filtration index $i$** if $v \not\in \text{im }a_{i-1}$,
- **die at filtration index $j \geq i$** if $j$ is the smallest index such that $a_{ij}(v)=0$.
	- If $a_{ij}(v) \neq0$, then death time of $v$ is $+\infty$. 

## Persistence Homology from Filtration

$PH_{k}^i(FK)$ consists of homology classes $H_k(F_iK)$ that continue to generate non trivial homology in $H_k(F_jK)$

![[Part 2-1770466744678.png|600]]


# Simplex-wise Filtration

$(FK_i)_{i \in I}$ for $I$ a subset of $\mathbb{Z}$ such that $FK_i = FK_{i-1}\cup \sigma_i$
