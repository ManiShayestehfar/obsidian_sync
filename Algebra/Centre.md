# Definition

>[!Definition] Centre
>The **Centre** of an $\mathbb{F}$-algebra $A$ is 
>$$Z(A) = \{z \in A \:|\:az=za \:\:\:\forall a \in A\}$$
>

## Examples

1. If $A$ is commutative, then $Z(A) = A$
	- e.g. $A = \mathbb{F}G$ for $G$ and abelian group

2. $A = \text{Mat}_n(\mathbb{F)}$
	- *Claim:* $Z(A) = \mathbb{F}$ as an $\mathbb{F}$-algebra. i.e. $Z(A) = \{\lambda I_n \:|\: \lambda \in \mathbb{F}\}$ (scalar matrices).


## Propositions

>[!Propositions]
>1. $Z(A)$ is a unital, commutative, $\mathbb{F}$-subalgebra of $A$
>2. If $A_1,...,A_t$ are $\mathbb{F}$-algebras, then $Z(A_1 \oplus \cdots \oplus A_t)= Z(A_1)\oplus \cdots \oplus Z(A_t)$
>3. If $A$ is semisimple, then $\#\text{Irr}(A) \leq\dim Z(A)$
>   with equality if $A$ is Schurian.
##### Proof
###### 1.
By definition $Z(A)$ is a $\mathbb{F}$-vector subspace of $A$. If $z_1,z_2 \in Z(A)$, then $(\lambda z_1+\mu z_2)a = \lambda z_1 a + \mu z_2 a = a(\lambda z_1 + \mu z_2)$.
Also $a(z_1z_2)=(az_2)z_2=(z_1a)z_2=z_1(az_2)=z_1(z_2a)=(z_1z_2)a$.

Finally, $Z(A)$ is unital since $1_A \in Z(A)$.
$Z(A)$ is clearly commutative.

###### 2.
See Week 7 Tutorial

###### 3.
If $A$ is semisimple, $A \cong \bigoplus_{D \in \text{Irr}(A)}\text{Mat}_{a_D}(\mathcal{O}_D)$
By (2), $Z(A) = \bigoplus_{D \in \text{Irr}(A)} Z(\text{Mat}_{a_D}(\mathcal{O}_D))$
So $\dim Z(A) = \sum_{D \in \text{Irr}(A)} \dim Z(\text{Mat}_{a_D}(\mathcal{O}_D))\geq \sum_{D \in \text{Irr}(A)}1 = \# \text{Irr}(A)$
If $A$ is Schurian then the equality holds.
$\square$

### Conjugacy classes and basis for Z(FG)

> [!Proposition]  
> Let $\mathscr{C}_{x_1},\ldots,\mathscr{C}_{x_t}$ be the conjugacy classes of a finite group $G$, where $x_1,\ldots,x_t$ are chosen representatives. For each $i$, define
> 
> $$\overline{x_i}=\sum_{y\in \mathscr{C}_{x_i}}y.$$
> 
> Then ${\overline{x_i}\mid 1\leq i\leq t}$ is a basis for $Z(\mathbb{F}G)$.

##### Proof
###### Well-defined
First, we show that $\overline{x_i}\in Z(\mathbb{F}G)$ for each $i$.  
  
Since $\mathbb{F}G$ has basis $G$, it is enough to show that $\overline{x_i}$ commutes with every $g\in G$. Fix $g\in G$. Then  
$$g\overline{x_i}g^{-1}=\sum_{y\in \mathscr{C}_{x_i}}gyg^{-1}.$$
The map $\mathscr{C}_{x_i}\to\mathscr{C}_{x_i}$ given by $y\mapsto gyg^{-1}$ is a bijection, since conjugation preserves conjugacy classes and has inverse $y\mapsto g^{-1}yg$. Hence  
$$g\overline{x_i}g^{-1}=\sum_{y\in \mathscr{C}_{x_i}}y=\overline{x_i}.$$
Therefore $g\overline{x_i}=\overline{x_i}g$. Since this holds for every $g\in G$, it follows by linearity that $\overline{x_i}\in Z(\mathbb{F}G)$.  

###### Linear Independence
Next, we show that the elements $\overline{x_1},\ldots,\overline{x_t}$ are linearly independent.  
  
Suppose $\sum_{i=1}^t\lambda_i\overline{x_i}=0$, where $\lambda_i\in\mathbb{F}$. Since the conjugacy classes form a disjoint partition of $G$, every $g\in G$ appears in exactly one conjugacy class. Thus, if $g\in\mathscr{C}_{x_i}$, then the coefficient of $g$ in $\sum_{i=1}^t\lambda_i\overline{x_i}$ is $\lambda_i$.  
  
Since $G$ is an $\mathbb{F}$-basis of $\mathbb{F}G$, all coefficients must be zero. Hence $\lambda_i=0$ for every $i$. Therefore $\overline{x_1},\ldots,\overline{x_t}$ are linearly independent.  

###### Span
Finally, we show that the elements $\overline{x_1},\ldots,\overline{x_t}$ span $Z(\mathbb{F}G)$.  
  
Let $a=\sum_{x\in G}\lambda_xx\in Z(\mathbb{F}G)$. 
Since $a$ is central, $gag^{-1}=a$ for every $g\in G$. Expanding gives  
$$gag^{-1}=\sum_{x\in G}\lambda_xgxg^{-1}.$$
Fix $g,y\in G$.
Comparing the coefficient of $y$ on both sides of $gag^{-1}=a$, the coefficient of $y$ on the right-hand side is $\lambda_y$, while on the left-hand side it is $\lambda_{g^{-1}yg}$. Therefore  
$$\lambda_y=\lambda_{g^{-1}yg}.$$
Hence the coefficients $\lambda_x$ are constant on conjugacy classes. Therefore, if $y\in\mathscr{C}_{x_i}$, then $\lambda_y=\lambda_{x_i}$. So  
$$a=\sum_{x\in G}\lambda_xx=\sum_{i=1}^t\sum_{y\in\mathscr{C}_{x_i}}\lambda_yy=\sum_{i=1}^t\lambda_{x_i}\sum_{y\in\mathscr{C}_{x_i}}y=\sum_{i=1}^t\lambda_{x_i}\overline{x_i}.$$
Thus $a\in\operatorname{Span}\{\overline{x_i}\mid 1\leq i\leq t\}$.  

Hence $\{\overline{x_i}\mid 1\leq i\leq t\}$ is a linearly independent spanning set for $Z(\mathbb{F}G)$, and therefore it is a basis. $\square$

>[!Corollary]
>If $\text{char }\mathbb{F} \nmid |G|$, then $\#\text{Irr}(\mathbb{F}G) \leq \#\text{ Conj. Classes}$.