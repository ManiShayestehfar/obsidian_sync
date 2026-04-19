# Centre

>[!Definition] Centre
>The **Centre** of an $\mathbb{F}$-algebra $A$ is 
>$$Z(A) = \{z \in A \:|\:az=za \:\:\:\forall a \in A\}$$
>

## Examples

1. If $A$ is commutative, then $Z(A) = A$
	- e.g. $A = \mathbb{F}G$ for $G$ and abelian group

2. $A = \text{Mat}_n(\mathbb{F)}$
	- Claim: $Z(A) = \mathbb{F}$ as an $\mathbb{F}$-algebra. i.e. $Z(A) = \{\lambda I_n \:|\: \lambda \in \mathbb{F}\}$ (scalar matrices).


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
By (2), $Z(A) = \bigoplus_{D \in \text{Irr}(A)}$