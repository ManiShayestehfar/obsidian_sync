Let $G$ be a *finite* group, and $\mathbb{F}$ a field.

>[!info] Definition
>An **$\mathbb{F}G$-module** or a **representation of $G$**, is an $\mathbb{F}$-[[vector space]] $V$ that comes equipped with a unitary linear $G$-action. i.e. a map $G \times V\to V$ given by $(g,v)\to gv$ such that 
>
>**Unital:** $1_G v = v$  for all $v \in V$
>**Associative:** $(gh)v = g(hv)$  for $g,h\in G$ and $v \in V$
>**Linear:** $(\lambda v + \mu w)g = \lambda vg + \mu wg$  for all $g \in G$, $\lambda, \mu \in \mathbb{F}$, and $v,w\in V$ 

- Strictly, the former definition is a **left $G$-module**. The same applied for a right module where $V \times G \to V$ is given by $(g,v) \to vg$ 
- Fix a basis $\{e_1,...,e_n\}$ of $V$ and for each $g \in G$, define the matrix $\mathbf{g} = (g_{ij})$ by
	$$ge_j = \sum_{i=1}^ng_{ij}\:e_i$$
- A matrix **representation** of $G$ is a group homomorphism $\rho: G \to GL_n(\mathbb{F})$, the group of invertible  $n\times n$ matrices with entries in $\mathbb{F}$.

>[!tip] Proposition 1
>Let $V$ be an $n$-dimensional $G$-module. Then $V$ determines a representation $\rho_V: G\to GL_n(\mathbb{f})$ 

![[Screenshot 2025-03-06 at 12.50.18 pm.png]]

## FG-Module Examples

1. $G = GL_n(\mathbb{F}) = \{\text{invertible}\:\: n \times n \:\:\text{matrices made of}\:\: \mathbb{F}\}$ 
The natural representation is 
$$V = \mathbb{F}^n = \left\{\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix}\:\Bigg|\: \lambda_i \in \mathbb{F}\right\} 
$$
If $A = (a_ij) \in G$, then $A\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix}$ is given by matrix multiplication

2. $G = S_n = \text{symmetric group of permutation of}\:\:\{1,2,...,n\}$. 
$V = \mathbb{F}^n$ with $S_n$-action
$$a\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix} := \begin{pmatrix}\lambda_{a(1)} \\ \vdots \\ \lambda_{a(n)}\end{pmatrix}$$

## $G-$Module Homo/Isomorphisms
- Let $V,W$ be $G-$modules.

> [!info] G-Module Homomorphism
> A **$G-$Module Homomorphism** is a linear transf. $\phi : V \to W$ that commutes with the $G-$action. i.e. $\phi(gv) = g\phi(v)$ for all $g\in G$, $v\in V$.

> [!info] G-Module Isomorphism
> A **$G-$Module Isomorphism** is a bijective $G-$module homomorphism, $\phi : V \to W$ that commutes with the $G-$action. i.e. $\phi(gv) = g\phi(v)$ for all $g\in G$, $v\in V$. We write $V\cong W$. 

# Submodules
- Let $V,W$ be $G-$modules, and let
$$\begin{align*}
\text{Hom}_G(V,W)&=\{\phi:V\to W\:|\:\phi\:\text{a G-module homomorphism}\} \\[6pt]
\text{End}_G(V) = \text{Hom}_G(V,V) &= \{\phi:V\to V\:|\:\phi\:\text{a G-module endomorphism}\} 
\end{align*}$$
- **NOTE:** $\text{End}_G(V)$ is a [[Ring|ring]], multiplication given by composition of maps.

>[!info] Definition
>If $V$ is an $\mathbb{F}$-vector space then a subset $W$ of $V$ is a **submodule** of $G$ if 
>
>1. $W$ is a subspace of $V$
>2. $wg \in W$ for all $w \in W$ and all $g \in G$
>   
>   Every submodule $W$ of a $G-$module is by definition a $G-$module.


> [!tip] Lemma 1
> ![[Pasted image 20250306222032.png]]
##### Proof for a)
1.  Clearly $\ker\varphi \subset V$ 
2. Let $g \in G$. $\varphi(vg) = g\varphi(v) = g\cdot 0 = 0$ and so $vg \in \ker \varphi$, where the choice of $v$ and $g$ were arbitrary. $\square$ 
##### Proof for b)
1. $\text{im}\:\phi \subset W$   
2. Let $w = \varphi(v)$ for $v \in V$ and $w \in W$. And $gw = g\varphi(w) = \varphi(gw) \in \text{im}\: W$ for all $g \in G$ and so $gw \in \text{im }W$. $\square$ 







