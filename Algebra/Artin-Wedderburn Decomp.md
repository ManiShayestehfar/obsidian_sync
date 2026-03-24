Recall:   $\text{End}_A(V) = \{T:V\to V \:|\: T \text{ is } \mathbb{F}\text{-linear and } T(av)=aT(v) \:\forall a\in A,v \in V\}$

>[!lemma]
>Suppose $V \cong U_1 \oplus U_2 \oplus \cdots \oplus U_r$ for some $A$-modules $U_1,...,U_r$. Then
>$$\text{End}_A(V) = \{(\varphi_{il})\:|\: \varphi_{il} \in \text{Hom}_A(U_i, U_l)\:\:\text{for}\:\: 1\leq i,l\leq r\}$$


# Artin-Wedderburn Decomposition

>[!Theorem]
>- $\mathbb{F}$ is a field,
>- $A$ is a *semisimple Schurian* $\mathbb{F}$-algebra. 
>- $d_1,...,d_t$ be the dimensions of the irreducible $A$-modules, counted up to isomorphism.
>Then $$A \cong \text{Mat}_{d_1}(\mathbb{F}) \oplus \cdots \oplus \text{Mat}_{d_t}(\mathbb{F})$$ 
##### Proof
ENTER PROOF

## Decomposition of $\mathbb{F}G$

Let $A = \mathbb{F}G$. How do we prove the decomposition?
##### Proof
ENTER PROOF

## Decomposition of $\text{Hom}$

>[!Proposition]
>Let $X_1,...,X_n$ and $Y_1,...,Y_m$ be $A$-modules, and set $X = X_1\oplus ... \oplus X_n$ and $Y = Y_1 \oplus ... \oplus Y_m$ as $\mathbb{F}$-vector spaces. Then $$\text{Hom}_A(X,Y) = \bigoplus_{\substack{1 \leq i \leq n \\ 1 \leq j \leq m}}\text{Hom}_A(X_i,Y_j)$$

##### Proof
Consider the following
![[Artin-Wedderburn Decomp-1774066458966.png]]

By abuse of notation think of $\varphi_{rs}$ as an endomorphism of $X = X_1 \oplus \cdots \oplus X_n$. 
i.e. identify $\varphi_{rs}\in \text{Hom}_A(X_s,X_r)$ and $\pi_s \cdot \varphi_{rs}\cdot i_r$.

Then $\varphi:X\to X$ is completely determined by maps $(\varphi_{rs})_{1\leq r,s\leq n}$.
- Think of $(\varphi_{rs})$ as a matrix with $(r,s)$ entry belonging to $\text{Hom}_A(X_s,X_r)$.

As vector spaces, $\varphi \mapsto (\varphi_{rs})$ gives an isomorphism $\text{End}_A(X)\to \left\{(\varphi_{rs}) \:|\: \substack{\varphi_{rs} \in \text{Hom}_A(X_s,X_r) \\ 1 \leq r,s\leq n}\right\}$.

**Claim:** The matrices on the RHS come equipped with multiplication: $(\varphi_{rs})(\psi_{rs}) = \sum_{j=1}^n\varphi_{rj}\psi_{js}$
This makes sense since $\varphi_{rj}, \psi_{js} \in \text{Hom}_A(X_s,X_r)$ since

![[Artin-Wedderburn Decomp-1774067005976.png|350]]

and thus so does the sum.
Hence the map $\varphi\mapsto (\varphi_{rs})$ is an algebra isomorphism.

Thus
 $$\text{End}_A(X_1\oplus \cdots \oplus X_n) = \{(\varphi_{rs})\:|\: \varphi_{rs} \in \text{Hom}_A(X_s, X_r)\:\:\text{for}\:\: 1\leq r,s\leq n\}$$ as $\mathbb{F}$-algebra. $\square$


# Corollaries

>[!Corollary] 
>Suppose $A$ is completely reducible $\mathbb{F}$-algebra with irreducible $\mathbb{F}$-algebra $D_1,...,D_t$. Then $$\dim A \geq \sum_{i=1}^t (\dim D_i)^2$$
>with equality $\iff A$ is Schurian.
##### Proof
NEED TO PROVE

## Examples
### $S_3$
Let $G=S_3$ and let $\text{char } \mathbb{F}=0$, or $\text{char }\mathbb{F} > 3$.


| Irreps | Name | Action | Dimensio |
| ------ | ---- | ------ | -------- |
|        |      |        |          |

 
