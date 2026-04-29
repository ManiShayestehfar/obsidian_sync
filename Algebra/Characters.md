# Definition

>[!def] Character
>$V$ a $\mathbb{C}G$-module and fix basis $\{e_1,...,e_n\}$ of $V$. For each element $g$ of $G$, let $\mathbf{g} = (g_{ij})$ be the matrix given by $g e_j = \sum_{i=1}^n g_{ij} e_i$. 
>The **character** $\chi_V$ of $V$ is the map $\chi_V: G \to \mathbb{C}$ given by $\chi(V) = \textrm{tr}(\mathbf{g}) = \sum_{i=1}^n g_{ii}$.
>

- $\chi_V$ extends linearly to a function $\chi_V: \mathbb{C}G \to \mathbb{C}$.

# Properties

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
$$V \supseteq W = \left\{\right\}$$







--- 
# Inner Product

>[!def] Inner product
>Let $\langle,\rangle: \mathbb{C}G\times \mathbb{C}G\to \mathbb{C}$ be a bilinear map determined by $$\langle g,h\rangle = \begin{cases}
1 & g = h^{-1} \\[3pt] 0 & \text{otherwise}
\end{cases}$$
Equivalently, $\langle\sum_{g\in G} \lambda_gg, \sum_{h\in G} \mu_h h \rangle = \sum_{g \in G}\lambda_g \mu_{g^{-1}}$

- This is not Hermitian, i.e. $\langle u,v \rangle \neq \overline{\langle u,v\rangle}$ so this is not really an inner product in the usual sense.
