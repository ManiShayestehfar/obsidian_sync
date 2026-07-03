# Definition

>[!Definition]
>A **class function** on $G$ is a map $\varphi: G \to \mathbb{C}$ such that $\varphi(g)=\varphi(h)$ if $g \sim h$.
- i.e. $\varphi$ is constant on conjugacy classes
- Let $\mathcal{C}(G) = \{\text{class functions on } G\}$.

# Examples

1. If $V$ is a $\mathbb{C}G$-module, then $\chi_V \in \mathcal{C}(G)$.

2. Let $C$ be a conjugacy class of $G$. The **indicator function** for $C$ is the map $1_C: G \to \mathbb{C}$ given by $$1_C(x) = \begin{cases}
1 & x \in C  \\
0 & x \not\in C
\end{cases}$$
	so $1_C \in \mathcal{C}(G)$.

## Observations

If $\psi,\varphi \in \mathcal{C}(G)$, then $\lambda \psi + \mu \varphi \in \mathcal{C}(G)$.
$\implies \mathcal{C}(G)$ is a $\mathbb{C}$-vector space.

We can extend $\langle -,- \rangle$ to $\mathcal{C}(G)$ by setting $\langle \psi, \varphi \rangle = \frac{1}{|G|} \sum_{g \in G} \psi(g^{-1})\varphi(g)$.

## Properties

>[!Proposition]
>1. $\{1_C \:|\: C \text{ a conjugacy class of } G\}$ is a basis of $\mathcal{C}(G)$.
>2. $\{\chi_1,...,\chi_t\}$ is a basis of $\mathcal{C}(G)$.
>3. If $\varphi \in \mathcal{C}(G)$, then $\varphi = \sum_{i=1}^t \langle \varphi, \chi_i \rangle \chi_i$
##### Proof
###### 1.
Basically the definition of $\mathcal{C}(G)$.
If $\varphi \in \mathcal{C}(G)$, then $\varphi = \sum_C \varphi(C) 1_C$. $\implies \{1_C\}$ spans $\mathcal{C}(G)$.

Moreover let $\sum_{C} \lambda_C 1_C = 0$. If $x_C \in C$, then $\lambda_C = 0$. 
So $\{1_C\}$ are linearly independent.

###### 2.
As $\# \text{Irr}(\mathbb{C}G)= \# \{\text{conjugacy classes}\} = \dim \mathbb{C}(G)$.
To prove $\{\chi_1,...,\chi_t\}$ is a basis of $\mathcal{C}(G)$, it is enough to show they are linearly independent.
Suppose $\sum_{i=1}^t \lambda_i \chi_i = 0$. For any $j$, $\left \langle \sum_{i=1}^t \lambda_i \chi_i, \chi_j \right\rangle =  0$.
But also $\left \langle \sum_{i=1}^t \lambda_i \chi_i, \chi_j \right\rangle = \sum_{i=1}^t \lambda_i \langle \chi_i,\chi_j \rangle = \lambda_j$
Thus $\lambda_1,...,\lambda_t=0 \implies \{\chi_1,...,\chi_t\}$ is a basis.
###### 3.
By part (2), if $\varphi \in \mathcal{C}(G)$, then $\varphi = \sum_{i=1}^t \lambda_i \chi_i$.
Using Row Orthogonality, $\lambda_i = \langle \varphi, \chi_i \rangle$. 
$\square$

>[!Lemma]
>Let $C_k$ be a conjugacy class of $G$. Then 
>$$1_{C_k} = \frac{|C_k|}{|G|}\sum_{i=1}^t \overline{\chi_i(C_k)}\chi_i$$
##### Proof
By part (3) of the last proposition. $1_{C_k}= \sum_{i=1}^t \langle 1_{C_k}, \chi_i \rangle \chi_i$.
So we need to compute
$$\begin{align*}
\langle 1_{C_k}, \chi_i \rangle &= \frac{1}{|G|} \sum_{g \in G} 1_{C_k}(g^{-1})\chi_i(g) \\
&= \frac{1}{|G|}\ \sum_{g \in G} 1_{C_k}(g)\chi_i(g^{-1}) \\
&= \frac{1}{|G|} \sum_{g \in C_k} \overline{\chi_i(g)} \\
&= \frac{1}{|G|} |C_k|\: \overline{\chi_i(C_k)}
\end{align*}$$
Hence 
$$1_{C_k} = \frac{|C_k|}{|G|} \sum_{i=1}^t \overline{\chi_i(C_k)} \chi_i.$$
$\square$



