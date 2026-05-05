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
#
