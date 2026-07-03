# Definition

>[!Definition]
>Let $A$ be semisimple, and $D \in \text{Irr}(A)$. Then the $D$-th **isotypic component** of $A$ is
>$$B_D = \langle d \in A \:|\: Ad \cong D \rangle$$
>which is a sum of all $A$-submodules of $A$ that are isomorphic to $D$.

# Properties

>[!Proposition]
>1. $B_D$ is a two-sided ideal of $A$.
>2. $A = \bigoplus_{D \in \text{Irr}(A)} B_D$
>3. If $D \in \text{Irr}(A)$, then $B_D \cong D^{\oplus a_D}$ as a left $A$-module where $a_D = \frac{\dim D}{\dim \mathcal{O}_D}$
> 	- As an $\mathbb{F}$-algebra, $B_D \cong \text{Mat}_{a_D}(\mathcal{O}_D)$
>4. Write $1_A = \sum_{D \in \text{Irr}(A)} e_D$ for $e_D \in B_D$.
>   Then $e_De_E = e_D$ if $D\cong E$ and $0$ otherwise.
>   Also $e_D \in Z(B_D)\subseteq Z(A)$.
##### Proof
###### 1.
Fix $D \in \operatorname{Irr}(A)$.
By definition, $B_D$ is the sum of all left $A$-submodules $M \subseteq A$ such that $M \cong D$. 
Therefore $B_D$ is itself a left $A$-submodule of $A$. 
Hence, for every $a \in A$ and $b \in B_D$, we have $ab \in B_D$. 
Thus $AB_D \subseteq B_D$, so $B_D$ is a left ideal of $A$.

It remains to show that $B_D$ is a right ideal. 
Let $a \in A$. Define $R_a : A \to A$ by $R_a(x)=xa$. 
We claim that $R_a$ is a left $A$-module homomorphism. 
Indeed, for any $c,x \in A$, we have $R_a(cx)=(cx)a=c(xa)=cR_a(x)$. Hence $R_a$ is left $A$-linear.

Now let $M \subseteq B_D$ be a left $A$-submodule with $M \cong D$. 
Since $R_a$ is left $A$-linear, $R_a(M)=Ma$ is a left $A$-submodule of $A$. 
Also, $M$ is simple because $D$ is simple. Therefore $\ker(R_a|_M)$ is either $0$ or $M$.

If $\ker(R_a|_M)=M$, then $Ma=0 \subseteq B_D$. 
If $\ker(R_a|_M)=0$, then $R_a|_M : M \to Ma$ is an isomorphism of left $A$-modules, so $Ma \cong M \cong D$. 
By definition of $B_D$, this implies $Ma \subseteq B_D$.

Thus, for every left $A$-submodule $M \subseteq B_D$ with $M \cong D$, we have $Ma \subseteq B_D$. Since $B_D$ is the sum of all such submodules $M$, it follows that $B_Da \subseteq B_D$.

Since this holds for every $a \in A$, we have $B_DA \subseteq B_D$. Therefore $B_D$ is a right ideal.

###### 2.
Week 9 Tutorial

###### 3.
First, recall that $A \cong \text{End}_A(A)^{op}$ via $a \mapsto \rho_a$ where $\rho_a:A \to A$ is given by $\rho_a(x) =xa$.
Now $A = B_1 \oplus \cdots \oplus B_t$.

>[!Claim]
>If $\rho: B_i \to B_j$ then $\rho=0$ if $i \neq j$

If $\rho \neq0$, then there exists $d \in B_i$ such that $\rho(d) \neq 0$.
Without loss of generality assume $Ad \cong D_i$. then $\rho$ restricts to a nonzero map $D_i \to B_j \cong D_j^{\oplus a_j}$.
$B_j$ has a submodule isomorphic to $D_j$ so $i=j$.

So we have
$$A \cong \text{End}_A(A)^{op} = \bigoplus_{i=1}^t \text{End}_A(B_i)^{op}$$
So $B_i \cong \text{End}_A(B_i)^{op} \cong \text{Mat}_{a_i}(\mathcal{O}_i)$ as $\mathbb{F}$-algebras. Thus $B_i = D_i^{\oplus a_i}$.

###### 4.
Now $1_A = e_1+\cdots +e_t$  with $e_i \in B_i$ since $A = B_1 \oplus \cdots \oplus B_t$.
If $x \in A$, then $x = x1_A=xe_1+\cdots xe_t$.
In particular, if $x \in B_i$, then $x-xe_i = \sum_{j\neq i}xe_j \in \bigoplus_{j\neq i} B_j$.

As $B_i \cap \bigoplus_{j\neq i} B_i = 0$, $x-xe_i = 0$ and $xe_j = 0$ for $j \neq i$. Hence $x = xe_i$.
By the same argument and using the fact that $B_i$ is a right ideal, $x=e_ix$.

Taking $x=e_i$, gives $e_ie_j=\delta_{ij}e_i$. So $e_1,...,e_t$ are idempotents.

>[!Claim]
>$B_i = e_i A e_i$

If $b \in B_i$, then $b=be_i=e_ib \in e_iAe_i$. So $B_i \subseteq e_iAe_i$.
Conversely if $a \in A$, then $e_iae_i \in B_i$. So $B_i = e_iA_ie_i = Ae_i=e_iA$.

>[!Claim]
>$e_i \in Z(B_i) \subseteq Z(A)$

Since $A = B_1 \oplus \cdots \oplus B_t$, there exist elements $e_i \in B_i$ such that $1_G = e_1 + \cdots + e_t$. If $b_i \in B_i$ then $b_i = b_i 1_G = b_i(e_1 + \cdots + e_t) = b_i e_1 + \cdots + b_i e_t$.

If $i \ne j$, then $e_j b_i,, b_i e_j \in B_i \cap B_j$, so $e_j b_i = 0 = b_i e_j$. 
Hence, $b_i = \delta_{i,j} e_j b_i = \delta_{i,j} b_i e_j$. 
Hence, $B_i = e_i A e_i = e_i A = A e_i$, and $e_i$ is a left and right identity on $B_i$. (So, $B_i$ is an $F$-algebra with multiplicative identity $e_i$.) 

In particular, if $b = b_1 + \cdots + b_t \in A$, with $b_i \in B_i$, then $e_i b = b_i = b e_i$, so $e_i \in Z(A)$. Hence, $e_i \in B_i \cap Z(A)$, so $e_i \in Z(B_i)$. 