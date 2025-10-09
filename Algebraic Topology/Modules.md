>[!def] (left) R-module
>$R$ a ring. A **(left) R-module** is a set $M$ with 
>1. Binary operation $+:M\times M \to M$ such that $(M,+)$ is an abelian group
>2. An operation $\cdot:T \times M \to M$ such that for all $r,s \in R$ and $m,n \in M$:
>	- $(r+s)\cdot m = r\cdot m + r \cdot n$
>	- $r \cdot (m+n) = r \cdot m + r \cdot n$
>	- $(rs) \cdot m = r \cdot (sm)$
>	- $1_{R}\cdot m = m$

>[!def] Free R-module
>$S$ a set. a **free R-module** on $S$ is an R-module $M$ together with a map $\varphi:S\to M$ such that for all R-modules $N$ and for all maps $\psi:S\to N$, there exists a *unique* R-module homomorphism $f:M \to N$ such that TFDC:
>![[Screenshot 2025-10-09 at 10.54.32 am.png|200]]

- Free $\mathbb{Z}$-module = [[Free Abelian Group]]


# Torsion Subgroup

>[!thm] Classification of finitely generated abelian group / $\mathbb{Z}$-modules
>If $A$ is a finitely generated abelian group, then $A \cong \mathbb{Z}^n \times T$ 
>where $T$ is the finite abelian **torsion subgroup** of $A$.
>i.e. $T = \{a \in A \:|\: a^k =1 \:\:\exists\: k \in \mathbb{Z}\}$ 

- e.g. $A \cong \mathbb{Z^3} \times \mathbb{Z}/2\mathbb{Z} \times (\mathbb{Z}/3\mathbb{Z})^3$
