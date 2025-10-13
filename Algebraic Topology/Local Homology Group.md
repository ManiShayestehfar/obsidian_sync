# Definition

>[!def] 
>The **local homology group** of a space $X$ and a point $x \in X$ is $H_n(X,X-\{x\})$.

- It is useful to find when spaces are not locally homeomorphic

>[!Claim]
>Any homeomorphism $f:X \to Y$ must induce $$H_n(X,X-\{x\}) \cong H_n(Y,y-\{f(x)\})$$
>for all $n$ and $x$.


# Equivalence between Simplicial and Singular Homology

Let $X$ be a $\Delta$-complex, $A \subseteq X$ a subcomplex. i.e. a subspace that is the union of cells of $X$. 

## Relative Chain

>[!def]
>A **relative chain** is $$\Delta_n(X,A) := \Delta_n(X)/\Delta_n(A)$$

- This gives a long exact sequence of nth-simplicial homology groups: $$\cdots \overset{}{\longrightarrow}H_n^\Delta(A)\overset{}{\longrightarrow}H_n^\Delta(X)\overset{}{\longrightarrow}H_n^\Delta(X,A)\overset{\partial}{\longrightarrow}H_{n-1}^\Delta(A)\overset{}{\longrightarrow}\cdots$$
- The homomorphism $H_n^\Delta(X,A) \overset{}{\longrightarrow}H_n(X,A)$ is induced from $\Delta_n(X,A) \overset{}{\longrightarrow} C_n(X,A)$ given by $[v_0,...,v_n] + \Delta_n(A)\longmapsto (r:\Delta^n\to X) + C_n(A)$.

# Theorems

>[!Theorem] H Thm 2.27
>For all $\Delta$-complex pairs $(X,A)$, $$H_n^\Delta(X,A) \overset{\cong}{\longrightarrow} H_n(X,A)$$ for all $n$.

**Note:** $\Delta$-complex pair $(X,A)$ denotes that $A$ is a subcomplex of $X$
##### Proof

*Case 1:* $A = \emptyset$,
Then $H_n^\Delta(X,A) \cong H_n^\Delta(X)$ and $H_n(X,A) \cong H_n(X)$ for all $n$. 

*Case 2:* $A \neq \emptyset$,
follows from case 1, and the "5-lemma". i.e. If 
![[Local Homology Group-1760354830970.png|420]]
1. Diagram is commutative
2. All objects are abelian groups
3. All rows are exact
4. $l,m,p,q$ are isomorphisms

then $n$ is an isomorphism.

###### Proof of Case 2:
![[Local Homology Group-1760355871619.png|550]]is a commutative diagram. From case 1 and 5-lemma, we get $H_n^\Delta(X,A)\cong H_n(X,A)$ for all $n$.

###### Proof of Case 1:

1. $X$ is finite-dimensional
   $X^k =$ k-skeleton of $X$.
   
   ![[Local Homology Group-1760356100721.png|600]]
   
   is commutative. Let $f_i$ denote the $i$-th vertical map from left to right.
    We know the rows are exact. To apply 5-lemma, we need 1) $f_1,f_4$ to be isomorphisms, and $f_2,f_5$ to be isomorphisms <mark style="background: #FFF3A3A6;">TBD</mark>
1. $X$ is infinite-dimensional
   The proof follows from (1) and the following lemma.
	   *lemma:* Any compact set $C \subseteq X$ intersects finitely many open simplices of $X$.   