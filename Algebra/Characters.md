# Definition

>[!def] Character
>$V$ a $\mathbb{C}G$-module and fix basis $\{e_1,...,e_n\}$ of $V$. For each element $g$ of $G$, let $\mathbf{g} = (g_{ij})$ be the matrix given by $g e_j = \sum_{i=1}^n g_{ij} e_i$. 
>The **character** $\chi_V$ of $V$ is the map $\chi_V: G \to \mathbb{C}$ given by $\chi(V) = \textrm{tr}(\mathbf{g}) = \sum_{i=1}^n g_{ii}$.
>

- $\chi_V$ extends linearly to a function $\chi_V: \mathbb{C}G \to \mathbb{C}$.

## Properties

>[!proposition]
>Let $V,W$ be $\mathbb{C}G$-modules and $\chi_V,\chi_W$ their characters. Then
>1. $\chi_V$ is independent of the choice of basis
>2. $\chi_V(1) = \dim V$ 
>3. If $g,h$ are conjugate in $G$, then $\chi_V(g)=\chi_V(h)$
>4. $V \cong W \iff \chi_V = \chi_W$
>5. $\chi_{V \oplus W} = \chi_V + \chi_W$ 
>6. $\chi_{V \otimes W}= \chi_V\chi_W$
##### Proof
###### 1.
Recall that for a fixed basis $\{v_1,...,v_n\}$ of $V$ and for $g \in G$, We defined $\mathbf{g} = (g_{ij})\in \text{Mat}_n(\mathbb{C})$ by $gv_j = \sum_{i=1}^n g_{ij}v_i$.
Then $\chi_V(g) = \text{tr}(\mathbf{g})= \sum_{i=1}^n g_{ii}$.
If $\{v_1',...,v_n'\}$ is another basis of $V$, then $v_j' = \sum_{i=1}^n a_{ij}v_j$ for an invertible matrix $A = (a_{ij})\in \text{Mat}_n(\mathbb{C})$.
From week 2: $\mathbf{g}' = \mathbf{g} = A^{-1}\mathbf{g}A$ . 
Hence by linearity of $\text{tr}$, $\chi_{V'}=\text{tr}(\mathbf{g}')= \text{tr}(\mathbf{g}) = \chi_V$.
So the character is independent of the choice of basis.

###### 2.
$1_G$ acts by the identity matrix $I_n$. So $\chi_V(1_G)= \text{tr}(I_n) = n = \dim V$.
###### 3.
If $x \sim y$, then $y = gxg^{-1}$ for some $g \in G$. So $\mathbf{y}=\mathbf{g\:x\:g^{-1}}$, and thus
$$\chi_V(y)= \text{tr}(\mathbf{g}) = \text{tr}(\mathbf{g\:x\:g^{-1}})= \text{tr}(\mathbf{x}) = \chi_v(x).$$
###### 4.
If $\Theta:V \to W$ is an isomorphism, then $\{\Theta(v_1),...,\Theta(v_n)\}$ is a basis of $W$. Then applying $\Theta$ to component action of $\mathbf{g}$ on $v_j\in V$, we get:
$$g \Theta(v_j) = \sum_{j=1}^n g_{ij} \Theta(v_i).$$
So $\chi_V = \chi_W$.

###### 5.
Fix a basis $\{v_1,...,v_n,w_1,...,w_m\}$ of $V \oplus W$ so that each part is the basis of corresponding $V$ and $W$.
Then 
$$\mathbf{g} = \begin{pmatrix}  
\mathbf{g}^v & 0 \\  
0 & \mathbf{g}^w  
\end{pmatrix}$$
So $\text{tr}(\mathbf{g}) = \text{tr}(\mathbf{g}^V) + \text{tr}(\mathbf{g}^W)= \chi_V + \chi_W$.
###### 6.
Week 9 Tutorial




# Examples

## Trivial 

If $V = I_G=$ trivial representation of $\mathbb{C}G$, then $\chi_{I_G}(g)=1$

## Symmetric Group

### Fixed Points

$\mathbb{C}G$ acts on $V=\mathbb{C}^n$ as $ge_i = e_{g(i)}$. i.e. $g(\lambda_1, ..., \lambda _n) = (\lambda_{g^{-1}(1)},...,\lambda_{g^{-1}(n)})$.

>[!Claim]
>$\chi_V(g) = \#\text{Fix}(\mathbf{g})$
>where $\#\text{Fix}(\mathbf{g}) = \{1 \leq i \leq n \:|\: g(i) = i\}$

- This is clear since w.r.t. the standard basis $\{e_1,...,e_n\}$, the only entries on the diagonal of $\mathbf{g}$ gives the fixed points.

### Standard Character
$$V \supseteq W = \left\{(\lambda_1,...,\lambda_n) \:|\: \sum_{i=1}^n \lambda_i =0\right\}$$
Since $V = W \oplus I$, then $\chi_W = \chi_V - \chi_I$.
i.e. $\chi_W(g) = \#\text{Fix}(\mathbf{g}) - 1$ 



# Character Table

>[!Definition]
>An **irreducible character** is the character of an irreducible representation

>[!Definition]
>The **character table** of $G$ is the square matrix with
>- rows indexed with $\chi_1,...,\chi_t$
>- columns indexed by conjugacy classes $C_1,...,C_t$
>- $(i,j)$-th entry is $\chi_i(C_j) = \chi_i(x_j)$ for $x_j \in C_j$

## Examples
### $S_3$ Character Table

|                 | $\{1\}$ | $\{i,j\}$ | $\{i,j,k\}$ |
| --------------- | ------- | --------- | ----------- |
| $\text{triv}$   | 1       | 1         | 1           |
| $\text{std}= W$ | 2       | 0         | -1          |
| $\text{sgn}$    | 1       | -1        | 1           |

--- 
# Inner Product

>[!def] Inner product
>Let $\langle,\rangle: \mathbb{C}G\times \mathbb{C}G\to \mathbb{C}$ be a bilinear map determined by $$\langle g,h\rangle = \begin{cases}
1 & g = h^{-1} \\[3pt] 0 & \text{otherwise}
\end{cases}$$
Equivalently, $\langle\sum_{g\in G} \lambda_gg, \sum_{h\in G} \mu_h h \rangle = \sum_{g \in G}\lambda_g \mu_{g^{-1}}$

- This is not Hermitian, i.e. $\langle u,v \rangle \neq \overline{\langle u,v\rangle}$ so this is not really an inner product in the usual sense.

>[!Lemma]
>If $a,b,c \in \mathbb{C}G$, then $\langle-,-\rangle$ is
>1. **Symmetric:** $\langle a,b \rangle = \langle b, a \rangle$
>2. **Associative:** $\langle ab, c \rangle = \langle a , bc \rangle$
>3. **Non-degenerate:** If $\langle a,x \rangle=0\:\: \forall x \in \mathbb{C}G$, then $a = 0$ 
>
##### Proof
For Symmetry and Associativity it is enough to verify it on the basis (due to bilinearity).
If $g,h,k \in G$, then
- $\langle g,h \rangle = \delta_{gh^{-1}}= \delta_{hg^{-1}} = \langle h, g \rangle$
- $\langle gh, k \rangle = \delta_{(gh)k^{-1}} = \delta_{g(hk)^{-1}} = \langle g, hk \rangle$ ??
  since $gh = k^{-1} \iff g = k^{-1}h^{-1} = (hk)^{-1}$

Finally suppose $0 \neq a \in \mathbb{C}G$.
Write $a = \sum_{g \in G} \lambda_g g$  for $\lambda_g \in \mathbb{C}$.
Since $a \neq 0$, $\lambda_g \neq 0$ for some $g$. Thus $\langle a, g^{-1} \rangle = \lambda_g  \neq 0$.
Hence $\langle -,- \rangle$ is non-degenerate.  $\square$

>[!Proposition]
>Let $d_V = \sum_{g \in G}\chi_V(g^{-1})g \in \mathbb{C}G$. Then
>1. If $a \in \mathbb{C}G$, then $\chi_V(a) = \langle d_V, a \rangle$ 
>2. $d_V \in Z(\mathbb{C}G)$ 
##### Proof
###### 1.
It is enough to show $\chi_V(x)= \langle d_V, x \rangle$ for $x \in G$.
By definition,
$$\begin{align*}
\langle d_V,x \rangle &= \left\langle \sum_{g \in G} \chi_V(g^{-1})g, x \right \rangle \\[3pt]
&= \sum_{g \in G} \chi_V(g^{-1})\: \langle g,x \rangle \\
&= \chi_V(x)
\end{align*}$$
###### 2.
We want $d_V \in Z(\mathbb{C}G) \iff d_Va =ad_V\qquad \forall a \in \mathbb{C}G$. 
Let $x \in \mathbb{C}G$. Then
$$\begin{align*}
\langle d_Va, x \rangle &= \langle d_V,ax \rangle \\
&= \chi_V(ax) \\
&= \chi_V(xa) \\
&= \langle d_V, xa \rangle \\
&= \langle xa, d_V \rangle \\
&= \langle x, ad_V \rangle \\
&= \langle ad_V, x \rangle
\end{align*}$$
So $\langle d_V a - a d_V, x \rangle = 0$ for all $x \in \mathbb{C}G$.
$\implies d_V a - a d_V = 0$ by non-degeneracy.
$\implies d_V a = a d_V \implies d_V \in Z(\mathbb{C}G)$.  $\square$



---

# Character of Regular Representation

$\rho = \chi_{\mathbb{C}G}$ is the character of the regular representation of $\mathbb{C}G$.

>[!Lemma]
>If $g \in G$, then 
>$$\rho(g) = \begin{cases}
|G| & g = 1_G  \\
0 & \text{otherwise}
\end{cases}$$
Consequently $d_{\rho} = d_{\mathbb{C}G}= |G|1_G$.
Moreover, if $V$ is any $\mathbb{C}G$-module, then $\rho(d) = |G|\chi_V(1)=|G|\dim V$.
##### Proof
The elements $\{x \:|\: x \in G\}$ gives a basis for $\mathbb{C}G$. If $g \in G$, then $gx=x \iff g = 1_G$.
So 
$$\rho(g) = \begin{cases}
|G| & g = 1_G  \\
0 & g \neq 1_G
\end{cases}$$
By definition, $d_\rho = \sum_{g \in G} \rho(g^{-1})g = |G|1_G$.
Finally, if $V$ is a $\mathbb{C}G$-module, then
$$\begin{align*}
\rho(d_V) = \langle d_\rho, d_V \rangle &= \langle |G|\cdot 1_G, d_V \rangle \\
&= |G|\langle1_G, d_V \rangle \\
&= |G| \langle d_V, 1_G \rangle \\
&= |G| \chi_V(1_G) \\
&= |G| \dim V \qquad \square
\end{align*}$$

Recall:
- $D_1,...,D_t$ irreducible $\mathbb{C}G$-modules, with $\chi_1,...,\chi_t$ where $\chi_i = \chi_{D_i}$.
  $\mathbb{C}G= B_1 \oplus \cdots \oplus B_t$ where $B_i$ is the $D_i$-th isotopic factor of $\mathbb{C}G$.
- $1_G = e_1+\cdots+e_t$ for unique $e_i \in B_i$ $\implies r_ir_j = \delta_{ij} e_i$
- $e_i \in Z(B_i) = \mathbb{C}\cdot e_i$
- $B_i \cong \text{Mat}_{\chi_i(1)}(\mathbb{C})$ where $\chi_i(1) = \dim D_i$



# Central Idempotents from Characters

>[!Theorem]
>Suppose $1 \leq i \leq t$, then
>$$e_i = \frac{\chi_i(1)}{|G|} d_i = \frac{\chi_i(1)}{|G|}\sum_{g \in G}\chi_i(g^{-1})g$$
##### Proof
If $x \in \mathbb{C}G$, then $x = 1_G x = (e_1 + \cdots + e_t)x= e_1x+e_2x +\cdots +e_t x$.
By definition, if $1 \leq j \leq t$ then $e_j x \in B_j$ since $B_j$ is a two-sided ideal.

Now $D_i$ is isomorphic to a summand of $B_i$. If $e_j x \in B_j$, then $e_jx D_i = 0$ if $j \neq i$, because $e_jx D_i \subseteq B_j\cdot B_i\subseteq B_j \cap B_i = 0$. 
$\implies \chi_i(e_jx) = 0$.
Hence, if $j \neq i$ and $x \in \mathbb{C}G$, then $\langle d_ie_j, x \rangle = \langle d_i, e_j x \rangle = \chi_i(e_jx)=0$.
By non-degeneracy of the bilinear form, $d_ie_j =0$. So $d_i = d_ie_1 + \cdots + d_ie_t = d_ie_i \in Z(B_i) = \mathbb{C}e_i$.
i.e. $d_i = \lambda e_i$ for some $\lambda \in \mathbb{C}$.

Now, by the lemma above, 
$$|G|\chi_i(1) = \rho(d_i) = \rho(\lambda e_i) = \lambda \rho(e_i) = \lambda \dim B_i = \lambda \chi_i(1)^2.$$
Since $\mathbb{C}G = B_1 \oplus \cdots \oplus B_t$, $e_i$ acts as the identity on $B_i$ while acting as zero on $B_j$ for $j \neq i$.
Hence $\lambda = |G|/\chi_i(1)$.
Thus 
$$d_i = \frac{|G|}{\chi_i(1)}e_i \iff e_i = \frac{\chi_i(1)}{|G|}d_i\qquad \square$$

>[!Corollary] 
>$\mathbb{C}G = \bigoplus_{i=1}\bigoplus_{j=1}^{\chi_i(1)} D_{ij}$  with $D_{ij}\cong D_i$. Then
>$1_G = e_1 + \cdots + e_t = \sum_{i=1}^t\sum_{j=1}^{\chi_i(1)} e_{ij}$. Importantly
>$$e_i = \sum_{j=1}^{\chi_i(1)} e_{ij}$$
>where the left hand side is a *unique* central primitive idempotent, but $e_{ij}$ is a *non-unique* primitive idempotent (not central).

---


# Character Inner Product

>[!Definition]
>Let $\chi$ and $\psi$ be characters of two $\mathbb{C}G$-modules. Then
>$$\begin{align*}
\langle \chi , \psi \rangle &= \frac{1}{|G|} \sum_{g \in G} \chi(g^{-1})\psi(g) \in \mathbb{C} \\[3pt]
&= \frac{1}{|G|} \sum_{g \in G} \chi(g)\psi(g^{-1})
\end{align*}$$

- $x \sim y \implies \chi(x) = \chi(y)$
- Also $y = gxg^{-1} \iff y^{-1} = (gxg^{-1})^{-1} = gx^{-1}g^{-1}$. So $y^{-1}\sim x^{-1}$.
  So $\chi(g^{-1})\psi(g)$ is **conjugacy class invariant**

## In terms of Conjugacy Classes

>[!Corollary]
>If $C_1,...,C_t$ are conjugacy classes of $G$, and we fix $x_i \in C_i$ for $1 \leq i \leq t$, then
>$$\langle\chi, \psi \rangle = \frac{1}{|G|}\sum_{g \in G} \chi(g^{-1})\psi(g) = \frac{1}{|G|}\sum_{i=1}^t |C_i| \chi(x_i^{-1})\psi(x_i)$$

### Properties

- Since character is linear, $\langle -,- \rangle$ is a bilinear function
- $\langle \chi, \psi \rangle = \langle \psi, \chi \rangle$ 

#### Character Inner product in terms of $d$
An important but trivial observation:

$$\begin{align*}
\langle \chi, \psi \rangle &= \frac{1}{|G|}\sum_{g \in G} \chi(g^{-1})\psi(g) \\
&= \frac{1}{|G|}\psi\left(\sum_{g \in G}\chi(g^{-1})g\right) \tag{by linearity of $\psi$} \\
&= \frac{1}{|G|}\psi(d_\chi) 
\end{align*}$$
But 
$$\langle d_\chi, d_\psi\rangle = \left \langle\sum_{g \in G}\chi(g^{-1})g,\: \sum_{h \in G}\psi(h^{-1})h\right \rangle = \sum_{g,h \in G} \chi(g^{-1})\psi(h^{-1}) \langle g,h \rangle = \sum_{g\in G} \chi(g^{-1})\psi(g) = |G|\langle\chi ,\psi \rangle $$
where the second-last equality holds since $\langle g , h \rangle = 1 \iff h = g^{-1}$ and $0$ otherwise.
Thus
$$\langle\chi, \psi \rangle = \frac{1}{|G|} \langle d_\chi, d_\psi \rangle.$$
- Importantly, the left-hand-side is a *character bilinear form*, whereas the right-hand-side is a *$\mathbb{C}G$ bilinear form*.


# Row Orthogonality

>[!Theorem]
>Suppose $1 \leq i,j \leq t$. Then 
>$$\langle \chi_i, \chi_j \rangle = \delta_{ij}$$
##### Proof
By definition 
$$\langle\chi_i, \chi_j \rangle = \frac{1}{|G|}\sum_{g \in G} \chi_i(g^{-1})\chi_j(g) = \frac{1}{|G|}\chi_i\left(\sum_{g \in G} \chi_i(g^{-1})g\right) = \frac{1}{|G|}\chi_j(d_i)$$
Recall that $e_i = \frac{\chi_i(1)}{|G|}d_i$, then
$$\frac{1}{|G|}\chi_j(d_i) = \frac{1}{|G|} \cdot \frac{|G|}{\chi_i(1)}\chi_j(e_i) = \begin{cases}
1 & i = j  \\
0 & i \neq j
\end{cases} = \delta_{ij}$$
since $e_i$ acts on $D_i$ as identity and as the zero map on $D_j \subseteq B_j$. $\square$

