>[!success] Goal
>If $D$ is an irreducible $\mathbb{C}G$-module, then $\dim D \mid |G|$.


# Algebraic Integers

## Definition

>[!Definition]
>1. An **algebraic integer** is a root of a monic polynomial in $\mathbb{Z}[x]$.
>   Let $\mathbb{A} = \{z \in \mathbb{C} \:|\: p(z) = 0 \text{ for monic polynomial } p \in \mathbb{Z[x]}\}$ 
>2. Similarly, let $\overline{\mathbb{Q}} = \{z \in \mathbb{C} \:|\: q(z) = 0 \text{ for monic polynomial } q \in \mathbb{\mathbb{Q}[x]}\}$

## Example

1. $\mathbb{Z} \subseteq \mathbb{A}$ with $p(x) = x-n$
2. $\mathbb{Q} \subseteq \overline{\mathbb{Q}}$ with $q(x) = x - q$
3. If $r \geq 1$, $n \in \mathbb{Z}$, then $n^{1/r} \in \mathbb{A}$ since this is a root of $x^r - n \in \mathbb{Z}[x]$
4. If $\zeta = \exp (2 \pi i /n)$ is a primitive n-th root of unity, then $\zeta \in \mathbb{A}$, because it is a root of $x^n -1 \in \mathbb{Z}[x]$
5. If $\lambda \in \mathbb{A}$, then $-\lambda , \overline{\lambda} \in \mathbb{A}$.
   Let $p(x) = x^n + p_{n-1}x^{n-1} + ...+ p_1x + p_0 \in \mathbb{Z}[x]$ because $p(\lambda)=0$. Then $p(\overline{\lambda}) = \overline{p(\lambda)}=0$ so $\overline{\lambda}\in \mathbb{A}$.
   Similarly let $\hat{p}(x) = p(-x)\cdot(-1)^n$, then $\hat{p}(-\lambda)=0 \implies -\lambda \in \mathbb{A}$. 
   BUT it is not clear whether $\hat{p}(x)$ is monic or not.


>[!Proposition]
>1. $\mathbb{A}$ is a set of eigenvalues of matrices with integers entries
>2. $\overline{\mathbb{Q}}$ is the set of eigenvalues of matrices with rational entries
##### Proof
###### 1.
If $M \in \text{Mat}_n(\mathbb{Z})$, and if $\lambda$ is an eigenvalue of $M$, then $c_M(\lambda)=0$ where $c_N(x) = \det(xI_n-M) = x^n + ... \in \mathbb{Z}[x]$. Thus $\lambda \in \mathbb{A}$.

Conversely suppose we have monic $p(x) \in \mathbb{Z}[x]$.
The **companion** matrix of $p(x)$ is
$$\begin{pmatrix}-1 & \cdots & \cdots & -p_0 \\TBD \end{pmatrix}$$

>[!Claim]
>$$c_p(x) = p(x)$$

**Proof:**
$c_p(x)= \det(xI-p)$