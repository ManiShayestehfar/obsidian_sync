Let $G$ be a *finite* group, and $\mathbb{F}$ a field.

>[!info] Definition
>An **$\mathbb{F}G$-module** or a **representation of $G$**, is an $\mathbb{F}$-[[vector space]] $V$ that comes equipped with a unitary linear $G$-action. i.e. a map $G \times V\to V$ given by $(g,v)\to gv$ such that 
>
>**Unital:** $1_G v = v$  for all $v \in V$
>**Associative:** $(gh)v = g(hv)$  for $g,h\in G$ and $v \in V$
>**Linear:** $(\lambda v + \mu w)g = \lambda vg + \mu wg$  for all $g \in G$, $\lambda, \mu \in \mathbb{F}$, and $v,w\in V$ 


- Strictly, the former definition is a **left $G$-module**. The same applied for a right module where $V \times G \to V$ is given by $(g,v) \to vg$ 
- Fix a basis $\{e_1,...,e_n\}$ of $V$ and for each $g \in G$, define the matrix $\mathbf{g} = (g_ij)$ by
	$$ge_j = \sum_{i=1}^ng_{ij}\:e_i$$
---
## FG-Module Examples

1. $G = GL_n(\mathbb{F}) = \{\text{invertible}\:\: n \times n \:\:\text{matrices made of}\:\: \mathbb{F}\}$ 
The natural representation is 
$$V = \mathbb{F}^n = \left\{\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix}\:\Bigg|\: \lambda_i \in \mathbb{F}\right\} 
$$
If $A = (a_ij) \in G$, then $A\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix}$ is given by matrix multiplication

2. $G = S_n = \text{symmetric group of permutation of}\:\:\{1,2,...,n\}$. 
$V = \mathbb{F}^n$ with $S_n$-action
$$a\begin{pmatrix}\lambda_1 \\ \vdots \\ \lambda_n\end{pmatrix} := \begin{pmatrix}\lambda_{a(1)} \\ \vdots \\ \lambda_{a(n)}\end{pmatrix}$$
---

- A matrix **representation** of $G$ is a group homomorphism $\rho: G \to GL_n(\mathbb{F})$, the group of invertible  $n\times n$ matrices with entries in $\mathbb{F}$.

>[!tip] Proposition 1
>Let $V$ be an $n$-dimensional $G$-module. Then $V$ determines a representation $\rho_V: G\to GL_n(\mathbb{f})$ 

![[Screenshot 2025-03-06 at 12.50.18 pm.png]]
