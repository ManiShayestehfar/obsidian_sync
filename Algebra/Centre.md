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

Finally, $Z(A)$ is unital since $1_A \in Z(A)$, and $Z(A)$.
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

Recall that $\overline{x}= \sum_{y \in \mathscr{C}_x}y = \sum_{x \sim y}y$.

>[!Proposition]
>Let $\mathscr{C}_1,...,\mathscr{C}_{x_t}$ be conjugacy classes of $G$.
>Then $\{\overline{x_i}\:|\: 1 \leq i \leq t\}$ is a basis for $Z(\mathbb{F}G)$
##### Proof
Implicitly, $x_1,...,x_t$ is some choice of conjugacy class reps for $G$.

We check:
1. $\overline{x_i} \in Z(\mathbb{F}G)$
2. $\{\overline{x_i}\}$ are linearly independent
3. $\{\overline{x_i}\}$ spans $Z(A)$
###### 1.
We need to show $a \overline{x_i}= \overline{x_i}a$ for all $a \in \mathbb{F}G$.
It is enough to check that $g \overline{x_i}= \overline{x_i}g \iff g \overline{x_i}g^{-1}=\overline{x_i}$ for $g \in G$.
Now $g \overline{x_i}g^{-1}=\sum_{y\sim x_i} gyg^{-1} = \sum_{y \sim x_i y} = \overline{x_i}\implies \overline{x_i} \in Z(\mathbb{F}G)$.

###### 2.
Since $\sim$ is an equivalence relation, $G = \mathscr{C}_{x_1} \sqcup \cdots \sqcup \mathscr{C}_{x_t} \implies$ the $\overline{x_i}$ are sums of disjoint sets.
As $\{x \:|\: x \in G\}$ is a basis of $\mathbb{F}G$, this implies $\sum_{i=1}^t \lambda_i \overline{x_i}=0 \iff \lambda_i=0$.

###### 3.
Suppose $a = \sum_{x\in G}\lambda_x x \in Z(G)$. 
Then $ga=ag$ for $g \in G$. So $\sum_{x \in G} \lambda_xgx = \sum_{x \in G} \lambda_x xg$. So
$$\sum_{x \in G} \lambda_xx = \sum_{x\in G} \lambda_x g^{-1} xg.$$
Comparing the coefficients of $gy \in G$ on both sides:
$\lambda_y = \lambda_{g^{-1}yg}$ since $xg=gy \implies y = g^{-1}xg$. So
$$a = \sum_{i=1}^t \lambda_{x_i}\overline{x_i} \in \text{Span}\{\overline{x_i}\}$$
$\square$

>[!Corollary]
>If $\text{char }\mathbb{F} \nmid |G|$, then $\#\text{Irr}(\mathbb{F}G) \leq \#\text{ Conjg. Classes}$.

