>[!success] Goal
>If $D$ is an irreducible $\mathbb{C}G$-module, then $\dim D \mid |G|$.

# Step 1: Characters are algebraic integers

>[!Corollary]
>Let $\chi$ be a character and $g \in G$. Then $\chi(g) \in \mathbb{A}$.
##### Proof
By diagonalising the action of $g$ on $V$, where $\chi = \chi_V$, then 
$$\chi(g) = \sum_{i=1}^n\lambda_i$$
where $\lambda_i$ are $m$-th roots of unity where $m = |g|$. As the $m$-th root of unity is in $\mathbb{A}$, then so is $\chi(g)$. $\square$


# Step 2: $\mathbb{A} \cap \mathbb{Q}$

>[!Lemma]
>$$\mathbb{A} \cap \mathbb{Q} = \mathbb{Z}$$
##### Proof
Let $a/b \in \mathbb{A} \cap \mathbb{Q}$.
WLOG assume $\gcd(a,b)=1$ where $a,b \in \mathbb{Z}$. 
Since $a/b \in \mathbb{A}$, there exists a monic polynomial $p(x) \in \mathbb{Z}[x]$ such that $p(a/b)=0$.
That is, 
$$(a/b)^n+ p_{n-1}(a/b)^{n-1}+\cdots+ p_1(a/b) + p_0=0$$
So 
$$a^n + p_{n-1}a^{n-1}b+ \cdots + p_1ab^{n-1}+ p_0b^n =0$$
$\implies a^n = -b(p_{b-1}a^{n-1}+\cdots p_1 ab^{n-2} + p_0b^{n-1})$.
If $p\neq 1$ is a prime divisor of $b$, then $p \mid a^n \implies p \mid a$ which is a contradiction since $\gcd(a,b)=1 \implies b= \pm 1$.
Hence $a/b = \pm a \in \mathbb{Z}$. Therefore $\mathbb{A} \cap \mathbb{Q} \subseteq \mathbb{Z}$. The other inclusion is trivial. $\square$


>[!Corollary]
>If $\chi$ is a character and $g \in G$, then $\chi(g) \in \mathbb{Q} \implies \chi(g) \in \mathbb{Z}$.


# Step 3: Characters of $\mathbb{C}G$-Modules in Algebraic Set

>[!Lemma]
>Let $\chi = \chi_i$ be the irreducible character of $D= D_i$. Let $C$ be a conjugacy class of $G$. Then
>$$\frac{|C|\chi(C)}{\chi(1)} \in \mathbb{A}.$$
>
##### Proof
Let $z_c = \sum_{x \in C}x \in  Z(\mathbb{C}G)$.
Notice, if $g \in G$, then $g$ acts on $\mathbb{C}G$ with respect to the basis $\{x \:|\: x\in G\}$ by permutation matrix. i.e. matrix with nonzero entries in each row and column and that entry is $1$.
So $g$ acts by a matrix in $\text{Mat}_{|G|}(\mathbb{Z})$.

So $Z_c$ acts on $\mathbb{C}G$ via a matrix in $\text{Mat}_{|G|}(\mathbb{Z})$. Thus eigenvalues of $z_c$ on $\mathbb{C}G$ are in $\mathbb{A}$.
Now $\mathbb{C}G \cong \bigoplus_{j=1}^i D_j^{\oplus \dim D_j}$ by the Artin-Wedderburn theorem.
Hence the eigenvalues of $z_c$ on each $D_j$ are in $\mathbb{A}$.

Notice that we can define a linear map $\Theta_c: D_j \to D_j$ by $\Theta_c(x) = z_cx$ for $x \in D_j$.
In fact, $\Theta_c$ is a $\mathbb{C}G$-module homomorphism because if $g \in G$, then $\Theta_c(gx) =z_c(gx)=g(z_cx)=g\Theta_c(x)$ since $z_c \in Z(\mathbb{C}G)$.
Hence by Schur's lemma $\Theta_c(x) = \lambda_c x$ for some $\lambda_c \in \mathbb{C}$. Thus $\lambda_c \in \mathbb{A}$.

Taking characters: 
$\chi(z_c) = \text{tr}(\lambda_c I_{|G|}) = \lambda_c \chi(1).$
But also $\chi(z_c) = \chi\left(\sum_{x \in C}x\right)= \sum_{x \in C}\chi(x) = |C|\chi(C)$.
Thus 
$$\lambda c = \frac{|C| \chi(C)}{\chi(1)} \in \mathbb{A}.$$
$\square$

# Step 4: Proving the Goal

>[!Theorem]
>Let $D = D_i$ be an irreducible $\mathbb{C}G$-module. Then $\dim D \mid |G|$.
##### Proof
Recall that the primitive central idempotent for $D = D_i$ is
$$e_i = \frac{\chi(1)}{|G|} d_{\chi_i}=\frac{\chi(1)}{|G|}\sum_{g \in G} \chi(g^{-1})g.$$
Apply $\chi = \chi_i$ to both sides:
$$\chi(e_i) = \frac{\chi(1)}{|G|} \sum_{g \in G} \chi(g^{-1})\chi(g)$$
$\chi(e_i) = \chi(1)$ since $e_i$ is the identity on $D_i$. Then
$$\chi(1) = \frac{\chi(1)}{|G|} \sum_{k=1}^t |C_k| \overline{\chi(C_k)}\:\chi(C_k)$$
 So rearranging and dividing by $\chi(1)$ gives
 $$\frac{|G|}{\chi(1)} = \sum_{k=1}^t \frac{|C_k| \chi(C_k) \: }{\chi(1)}\overline{\chi(C_k)}.$$
 $\frac{|C_k| \chi(C_k) \: }{\chi(1)} = \lambda_c \in \mathbb{A}$ using the lemma above, and $\overline{\chi(C_k)} \in \mathbb{A}$ as it is the conjugate of an irreducible character. So the whole summand is in $\mathbb{A}$. But clearly $|G|/\chi(1) \in \mathbb{Q}$. So the right-hand-side is in $\mathbb{A} \cap \mathbb{Q} = \mathbb{Z}$ from the lemma in step (2).

Hence $|G|/$