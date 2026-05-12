>[!success] Goal
>If $D$ is an irreducible $\mathbb{C}G$-module, then $\dim D \mid |G|$.


# Algebraic Integers

## Definition

>[!Definition]
>1. An **algebraic integer** is a root of a monic polynomial in $\mathbb{Z}[x]$.
>   Let $\mathbb{A} = \{z \in \mathbb{C} \:|\: p(z) = 0 \text{ for monic polynomial } p \in \mathbb{Z}[x]\}$ 
>2. Similarly, let $\overline{\mathbb{Q}} = \{z \in \mathbb{C} \:|\: q(z) = 0 \text{ for monic polynomial } q \in \mathbb{\mathbb{Q}}[x]\}$

## Example

1. $\mathbb{Z} \subseteq \mathbb{A}$ with $p(x) = x-n$
2. $\mathbb{Q} \subseteq \overline{\mathbb{Q}}$ with $q(x) = x - q$
3. If $r \geq 1$, $n \in \mathbb{Z}$, then $n^{1/r} \in \mathbb{A}$ since this is a root of $x^r - n \in \mathbb{Z}[x]$
4. If $\zeta = \exp (2 \pi i /n)$ is a primitive n-th root of unity, then $\zeta \in \mathbb{A}$, because it is a root of $x^n -1 \in \mathbb{Z}[x]$
5. If $\lambda \in \mathbb{A}$, then $-\lambda , \overline{\lambda} \in \mathbb{A}$.
   Let $p(x) = x^n + p_{n-1}x^{n-1} + ...+ p_1x + p_0 \in \mathbb{Z}[x]$ because $p(\lambda)=0$. Then $p(\overline{\lambda}) = \overline{p(\lambda)}=0$ so $\overline{\lambda}\in \mathbb{A}$.
   Similarly let $\hat{p}(x) = p(-x)\cdot(-1)^n$, then $\hat{p}(-\lambda)=0 \implies -\lambda \in \mathbb{A}$. 
   BUT it is not clear whether $\hat{p}(x)$ is monic or not.

## Algebraic Sets as Eigenvalue Sets

>[!Proposition]
>1. $\mathbb{A}$ is a set of eigenvalues of matrices with integers entries
>2. $\overline{\mathbb{Q}}$ is the set of eigenvalues of matrices with rational entries
##### Proof
###### 1.
If $M \in \text{Mat}_n(\mathbb{Z})$, and if $\lambda$ is an eigenvalue of $M$, then $c_M(\lambda)=0$ where $c_N(x) = \det(xI_n-M) = x^n + ... \in \mathbb{Z}[x]$. Thus $\lambda \in \mathbb{A}$.

Conversely suppose we have monic $p(x) \in \mathbb{Z}[x]$ such that $p(\lambda)=0$ (i.e. $\lambda \in \mathbb{A}$ is algebraic).
The **companion** matrix of $p(x)$ is
![[Screenshot 2026-05-12 at 1.38.18 pm.png|250]]
Expanding the determinant along the first row gives

![[Screenshot 2026-05-12 at 1.39.01 pm.png]]
where the last equality follow by induction on $n$.
Hence the characteristic equation of $P$ is $\det(P-xI)= p(x)$, so $\lambda \in \mathbb{A}$ is the eigenvalue of an integer valued matrix.

- The argument for $\overline{\mathbb{Q}}$ follows similarly. 
$\square$

### Propositions

>[!Proposition]
>The set $\mathbb{A}$ is a ring and $\overline{\mathbb{Q}}$ is a field
##### Proof
Let $\lambda, \mu \in \mathbb{A}$. Then there exists matrices $X \in \text{Mat}_m(\mathbb{Z})$, $Y \in \text{Mat}_n(\mathbb{Z})$ and vectors $u \in \mathbb{C}^m, v \in \mathbb{C}^n$ such that $Xu =\lambda u$ and $Yv = \mu v$.

Define $X \otimes Y$ to be the block-matrix in $\text{Mat}_{mn}(\mathbb{Z})$
$$X \otimes Y =
\begin{bmatrix}
x_{11}Y & \cdots & x_{1m}Y \\
\vdots & \ddots & \vdots \\
x_{m1}Y & \cdots & x_{mm}Y
\end{bmatrix}$$
where $X = (x_{ij})$, $Y=(y_{kl})$.
Equivalently, $(X \otimes Y)_{ab} = x_{ij}y_{kl}$ where $a = (i-1)m+k$ and $b = (j-1)m+l$.
Think of $X \otimes Y$ as acting on $\mathbb{C}^{mn}$ which has a basis 
$$(u_1 \otimes v_1, \cdots, u_1 \otimes v_n, u_2\otimes v_1, \cdots, u_2 \otimes v_n, \cdots ,u_m \otimes v_1,...,u_m \otimes v_n)$$
where $\mathbb{C}^m = \langle u_1,...,u_m \rangle$, $\mathbb{C}^n = \langle v_1,...,v_n\rangle$.
If $(x \otimes y) \in \mathbb{C}^{mn}$, then $(X \otimes Y)(x \otimes y) = Xx \otimes Yy$.
In particular 
$$(X \otimes Y)(u \otimes v) = Xu \otimes Yv = \lambda u \otimes \mu v = \lambda\mu(u \otimes v)$$
So $\lambda \mu$ is an eigenvalue of $X \otimes Y$ $\implies \lambda \mu \in \mathbb{A}$.

Similarly $(X \otimes I_m \pm I_n \otimes Y) ( u \otimes v) = (X \otimes I_n)(u \otimes v) \pm (I_n \otimes Y) (u \otimes v) = \lambda u \otimes v \pm \mu u \otimes v = (\lambda \pm \mu)(u $