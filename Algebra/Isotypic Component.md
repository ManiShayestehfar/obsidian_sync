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
$A$ is semisimple so there exists $a_i>0$ and $A$-submodules $\{D_{ij} \:|\: 1\leq i \leq t, 1 \leq j \leq a_i\}$ where each $D_{ij}\cong D_i$ for $1 \leq j \leq a_i$. So
$$A = \bigoplus_{i=1}^t \bigoplus_{j=1}^{a_i}D_{ij}$$
as a left $A$-module. 
By definition $D_{ij}\subseteq D_i$, so $\bigoplus_{j=1}^{a_i}D_{ij}\subseteq B_{D_i} =: B_i$. Hence $\dim B_i \geq a_i^2$.
By the Krull-Schmidt theorem, $B_i \cap B_j =0$ if $i \neq j$.

Therefore $A = B_1 \oplus \cdots \oplus B_t$ and $B_i = \bigoplus_{j=1}^{a_i}D_{ij} \cong D_i^{\oplus a_i}$ as an $A$-module, by counting dimensions.

Now suppose $D \subseteq B_i$ where $D \cong D_i$. Id $Da \neq 0$ for some $a \in A$, then define a map $\varphi: D \to Da$ by $\varphi(d)=da$. Since multiplication in $A$ is linear and associative, $\varphi$ is an $A$-module homomorphism.
Since $Da \neq0$, the image of $\varphi$ is nonzero so $\varphi$ is an isomorphism by Schur's lemma.
Hence $Da \cong D \cong D_i$, so $Da \subseteq B_i$. 
Therefore $B_i$ is a two-sided ideal of $A$.

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
$$A \cong \text{End}_A(A)^{op} = \bigoplus_{i=1}^t \text{End}_A(B)^{op}$$
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