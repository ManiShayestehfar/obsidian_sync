
>[!def] 
>Let $A$ be an [[F-algebra]]. A (left) **$A$-module** is a $\mathbb{F}$-[[vector space]] $V$ that is equipped with a unitary bilinear $A$-action.  i.e.
>$$A \times V \to V \quad;\:(a,v) \to av$$
>such that
>1. **Unital:** $1_A v = v$ for all $v \in V$
>2. **Associativity:** $(ab)v = a(bv)$ for all $a,b \in A$ and $v \in V$
>3. **Bilinearity:** $a(\lambda v + \mu w) = \lambda (av) + \mu (aw)$, and $(\lambda a + \mu b)v = \lambda (av) + \mu (bv)$  for all $a,b \in A$, $\lambda_\mu \in \mathbb{F}$, $v,w \in V$. 

# Examples
- A [[Representation|regular representation]] of $A$. i.e. $A$ an $\mathbb{F}$-algebra, then the right $A$-module with $A$-action as right multiplication. 
  
  *Question:* Is $A$ irreducible as an $A$ module
  Take $a \in A$, then $a = (a_{ij}) \in \text{Mat}_n(\mathbb{F})$ 
  $X = (x_{ij})$, then $ax = \sum_{k=1}^n a_{ih}x_{hj}$ (matrix multiplication). Then on the $j$-th column of $X$, we get subspaces of the form $$D_j = \left\{\begin{pmatrix}0 &\cdots & 0&\lambda_{1j} & 0 &\cdots&0  \\ &&& \vdots &&&  \\
  0 &\cdots & 0&\lambda_{nj} & 0 &\cdots&0 
  \end{pmatrix} \:\mid\: \lambda_{ij} \in \mathbb{F}\right\} \implies aD_j \subseteq D_j$$
  Then $A = D_1 \oplus D_2 \oplus \cdots \oplus D_n$.
  Further $D_j \cong \left\{\begin{pmatrix}\lambda_1  \\ \vdots \\ \lambda_n \end{pmatrix}\: :\: \lambda_i \in \mathbb{F}\right\}$ which means that $A$ acts via matrix multiplication onto the column space $\mathbb{F}^n$. 
  $\implies A$ is NOT irreducible as a left $A$-module, since $A \cong \mathbb{F}^n \oplus \cdots \mathbb{F}^{n} \cong (\mathbb{F})^{\oplus n}$ 
  
  *Question:* Is $\mathbb{F}^n$ irreducible as an $A$-module?
  If $0\neq \begin{pmatrix}\lambda_1  \\ \vdots \\ \lambda_n \end{pmatrix} \in \mathbb{F}^n$, then $\lambda_j \neq 0 \implies$ let $E_{ij}$ be the matrix with $1$ in $ij$ position. Then $E_{ij}v_\lambda = E_{ij}\begin{pmatrix}\lambda_1  \\ \vdots \\ \lambda_j \end{pmatrix} = \begin{pmatrix} 0  \\ \vdots \\ \lambda_j \\ \vdots  \\ 0 \end{pmatrix}$
  Hence all $e_j$ vector are in $Av_\lambda = \mathbb{F}^n$. Hence $\mathbb{F}^n$ is irreducible as an $A$-module.
  
  
  

# Submodules

- An **$A$- submodule** of an $A$-module $V$ is a vector subspace $W$ such that $aw \in W$ for all $a \in A$ and $w \in W$.

- Similarly, an $A$-module **homomorphism** is a vector space homomorphism $\varphi: V \to W$ such that $\varphi(av) = a \varphi(v)$ for all $a \in A$ and $v \in V$.  


>[!tip] Image & Kernel
>Let  $V$ and $W$ be $A$-modules and let $\varphi: V \to W$ be an $A$-module homomorphism. Then
>1. $\ker \varphi = \{v \in V\:|\: \varphi(v) = 0 \}$ is an $A$-submodule of $V$ 
>2. $\text{im }\varphi = \{\phi(v)\:|: v \in V\}$ is an $A$-submodule of $W$.


# Isomorphism Theorems

Suppose $V$ is an $A$-module.

1. Suppose $\varphi:V \to W$ is an $A$-module homomorphism. Then $V/\ker\varphi \cong \text{im }\varphi$ 
2. Suppose $X$ and $Y$ are $A$-submodules of $V$. Then $(X+Y)/Y \cong X/(X\cap Y)$
3. Suppose $U\leq W \leq V$ are $A$-submodules of $V$. Then $V/W \cong (V/U)/(W/U)$
4. Suppose $W$ is a submodule of $V$. Then there is a 1-to-1 inclusion preserving correspondence between the submodules of $V$ that contain $W$ and the submodules of $V/W$.

# Irreducibility

- An $A$-module $V$ is **irreducible** (or **simple**) if $V$ contains no nonzero proper submodules.
- It is **completely reducible**, or **semi-simple** if it is a direct sum of irreducible $A$-modules.


## Some Propositions

>[!proposition] 
>Suppose $V$ is an $A$-module. 
>
>1. $V$ is irreducible $\implies \: V \cong A/M$ for some maximal ideal $M$ of $A$
>2. $n = \dim V$ $\implies \: V \cong A^{\oplus n} / X$ for some $A$-submodules $X$ of $A^{\oplus n}$ 
##### Proof of (1)
 A an [[F-Algebra]]. Let $v$ be any nonzero element of $V$. Then $Av = \{av \:|\: a \in A\}$ is a nonzero submodule of $V$. Since $V$ is irreducible, then $V = Av$.
 
Define a map $\varphi: A \to V$ by $\varphi(a) = av$. $\varphi$ is linear as $A$ acts linearly on $V$. e.g. for $a,b \in A$, $\varphi(a+b) = (a+b)v = av + bv = \varphi(a) + \varphi(b)$. Similarly $\varphi$ commutes with scalar multiplication. 

In addition, $\varphi$ is an $A$-module homomorphism as 
$$\varphi(ax) = (ax)v = a(xv) = a\varphi(x) \quad a,x\in A.$$
Also $\varphi$ is surjective since $V = Av = \text{im }\varphi$, so $V \cong A / \text{ker }\varphi$ by the First Isomorphism Theorem.

Moreover since $V$ is irreducible, $\ker \varphi$ is a maximal ideal of $A$ by the Isomorphism theorems above.  $\square$ 

>[!warning] Note
>The submodules of $A$ are exactly its left [[Ring|ideals]] 


>[!lemma]
>$V \subseteq A$.
>$V$ a submodule of $A \iff$ $V$ is a left-ideal of $A$
>

##### Proof
Here we treat $A$ as a **left $A$-module over itself**.  i.e. scalar multiplication is ring multiplication where both scalars and set elements being acted on come from $A$.
###### $(\Rightarrow)$ 
If $V$ is a submodule of $A$, then $V$ is an $\mathbb{F}$-vector subspace of $A$ and so $v-w \in V$ for $v,w \in V$. Also since $V$ is an $A$-module, it's closed under left multiplication. i.e. $av \in V$ for all $a \in A,$ $v\in V$.  We then have both
1. Additive closure (i.e. $v - w \in V$), and
2. left multiplication closure
and therefore $V$ is a left-ideal.
###### $(\Leftarrow)$ 
If $V$ is a left-ideal of $A$, then by additive closure, $v-w\in V$ and so $V$ is an $\mathbb{F}$-vector subspace, and it is closed under left multiplication by $A$. 
Hence it is an $A$-submodule. 
 


>[!corollary]
>Suppose $A$ is a finite-dim $\mathbb{F}$-algebra. Then, there are only *finitely* many irreducible $A$-modules, up to isomorphism.
##### Proof 
If $D$ is an irreducible $A$-module, then from [[Filtration and Composition Series|lemma 4]] $D$ is a composition factor of $A$. As $A$ is finite dimensional, it can only have a finite number of composition factors.        $\square$


# Decomposition of A-modules given A Semisimple

>[!proposition]
>If $A$ is a semisimple $\mathbb{F}$-algebra, and $V$ is an $A$-module, then $V$ is a semisimple $A$-module. 
##### Proof

We know $A = D_1 \oplus D_2 \oplus \cdots \oplus D_r$ as a direct some of irreducible submodules. Then
$$V = AV = \{av \:|\: a \in A, v \in V\} = D_1V + \cdots D_rV$$
Pick a basis $\{e_1,..,e_n\}$ for $V$, and let $1 \leq a \leq n$ and $1 \leq i \leq r$.
Then $D_i e_a = \{de_a \:|\: d \in D_i\}$ is a submodule of $V$ as it is a vector subspace of $V$ closed under left multiplication by $A$. 
If $D_ie_a\neq 0$, then $D_i \cong D_ie_a$ by Schur's lemma as there is an nonzero $A$-homomorphism from $d \mapsto de_a$. Thus $V = D_1 + D_2 + \cdots D_r$.

This is *a priori* not a direct sum, but If $D,D'$ are irreducible submodules of $V$, then either $D = D'$ or $D \cap D' = 0$. Therefore we can indeed write $V = D_1 \oplus D_2 \oplus \cdots \oplus D_r$. $\square$

**Remark:** the proof relies on the fact that we can view $A$ as both an algebra and an $A$-modules.
