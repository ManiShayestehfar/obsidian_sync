# Statement

- Let $A$ be a non-empty, finite, countable or uncountable set. 
- For each $\alpha \in A$ assign a non-empty set $X_\alpha$. 
- Consider the Cartesian product $\prod_{\alpha \in A}X_\alpha$ consisting of all "collections" $(x_\alpha)_{\alpha\in A}$ where $x_\alpha \in X_\alpha$. 
	- Formally: the Cartesian product is the set of functions $x:A \to \cup_{\alpha \in A} X_\alpha$ such that $x(\alpha) \in X_\alpha$.
*Fundamental question:* Is $\prod_{\alpha \in A}  X_\alpha$ non-empty in general?

**Axiom of Choice:** Assume $\prod_{\alpha \in A} X_\alpha \neq \varnothing$ whenever $A \neq \varnothing$ and $X_\alpha \neq \varnothing$ for all $\alpha \in A$.

## In terms of Posets

>[!corollary]
>Suppose $(X,<)$ is a poset such that each chain in $X$ has an upper bound. Then $X$ has a maximal element.

>[!Theorem]
>The following assertions are equivalent:
>1. Axiom of choice
>2. Zorn's lemma
>3. Every set can be well-ordered


# Applications of Zorn's Lemma

## Existence of Hamel basis of a vector space

Let $V$ be a vector space over $\mathbb{K}$. $S \subseteq V$ is called a **Hamel** basis of $V$ if:
1. $S$ is linearly independent for all finitely many vectors $v_1,...,v_n \in S$ 
2. $\text{Span}(S) = V$ i.e. $\forall v \in V$, there exists $v_1,...,v_n \in S$ and $\lambda_1,...,\lambda_n \in \mathbb{K}$ such that $\sum_{i=1}^n {\lambda_iv_i}= v$ .

>[!Lemma]
>$S \subseteq V$ is a Hamel basis if one of the following holds:
>1. $S$ is a *maximal* linearly independent subset of $V$
>2. $S$ is a *maximal* spanning set of $V$. i.e. $\forall v \in S,\: \text{Span}(S \setminus\{0\}) \neq V$
>3. $S$ is linearly independent and $\text{Span}(S) = V$
##### Proof (of existence of Hamel Basis)
*Poset construction:*
Let $\mathcal L=\{S\subseteq V \mid S \text{ is linearly independent}\}$.  
Then $(\mathcal{L}, \subseteq)$ is a non-empty poset (non-empty since $\varnothing\in\mathcal L$)

*Chain and bounding union:*
We want to apply Zorn's lemma, so we need an upper bound.
Let $C=\{L_\alpha\}_{\alpha\in A}$ be a chain in $\mathcal L$. Thus, for any $\alpha,\beta\in A$, either $L_\alpha\subseteq L_\beta$ or $L_\beta\subseteq L_\alpha$.  
  
Define 
$$L=\bigcup_{\alpha\in A}L_\alpha.$$
Clearly $L_\alpha\subseteq L$ for every $\alpha\in A$, so $L$ is an upper bound for $C$, provided that $L\in\mathcal L$. Therefore, we need to show that $L$ is linearly independent.  

*Linear independence of L:*
Take finitely many vectors $v_1,\dots,v_n\in L$.
By definition of $L$, for each $j\in\{1,\dots,n\}$, there exists $\alpha_j\in A$ such that $v_j\in L_{\alpha_j}$.  
  
Since $C$ is a chain, the finitely many sets $L_{\alpha_1},\dots,L_{\alpha_n}$ are totally ordered by inclusion. Hence one of them contains all the others. That is, there exists some $k\in\{1,\dots,n\}$ such that $L_{\alpha_j}\subseteq L_{\alpha_k}$ for every $j\in\{1,\dots,n\}$.  Therefore $v_1,\dots,v_n\in L_{\alpha_k}$.  
  
But $L_{\alpha_k}\in\mathcal L$, so $L_{\alpha_k}$ is linearly independent. Hence the vectors $v_1,\dots,v_n$ are linearly independent. Since every finite subset of $L$ is linearly independent, $L$ is linearly independent. Thus $L\in\mathcal L$.  

*Zorn's lemma:*
Therefore every chain in $\mathcal L$ has an upper bound in $\mathcal L$. 
By Zorn's lemma, $\mathcal L$ has a maximal element. Call it $M$. 
Thus $M$ is a maximal linearly independent subset of $V$.  $\square$


## Any topological dynamical system contains a minimal subsystem

### Dynamical System

>[!Definition] $G$-dynamical system
>Let $G$ be a group, $X$ a compact metric space. 
>We say $(X,G)$ is a **$G$-Dynamical System** if $G$ acts on $X$ via homomorphisms.
>i.e. there exists homeomorphisms $T_g:X \to X$ such that $\forall g \in G:$
>1. $T_h \circ T_g = T_{hg}$
>2. $T_1 = \text{id}$. 

- A **subsystem** is any non-empty closed $Z \subset X$ which is $G$-invariant.
#### Examples
1. $X = S^1, G = \mathbb{Z}$, and $T_1 = R_\alpha$ where $R_\alpha$ is rotation by angle $\alpha \in \mathbb{Z}$. All $T_g$ are determined by $T_1.$ 

### Minimality

>[!Definition] Minimal dynamical system
>A dynamical system $(X,G)$ is **minimal** if any closed non-empty $G$-invariant subset $Y \subseteq X$ is only $Y=X$.

- $Y$ is $G$**-invariant** if $\forall g \in G: gY = Y$
- *Example:* $X=S^1$, $G=\mathbb{Z}$ acts by rotation $R_\alpha$, 
  $(X,R_\alpha)$ minimal $\iff$ $\alpha \not \in \pi\mathbb{Q}$.


### Proof of Minimality

Zorn's Lemma is equivalent to the following: Given $(\mathcal{P}, \leq)$ a non-empty poset such that any chain $C \subseteq \mathcal{P}$ has a *lower* bound, contains a *minimal* element.

>[!Theorem] 
>Any $G$-system $(X,G)$ contains a minimal subsystem
##### Proof
Define a poset of $G$-subsystems on $(X,G)$ with "$\leq$" which is containment. 

>[!Claim] 
>Any chain has a lower bound

- If $C \subseteq \mathcal{P}$ is a chain defined as $C := (X_\alpha)_{\alpha \in I}$. 
  Then define $Z := \bigcap_{\alpha \in I}X_\alpha$, which is closed as an intersection of closed sets, and is non-empty by the Finite Intersectivity Property (FIP), which states:
	- If $X$ is a compact set then it has a finite intersectivity property. i.e. 
	  If $(F_\alpha)_{\alpha \in I} \subseteq X$ is a family of closed subsets such that for any finite subset of indices $J \subseteq I$, $$\bigcap_{\alpha \in J}F_\alpha \neq \varnothing \implies \bigcap_{\alpha \in I}F_\alpha \neq \varnothing$$
	- The point is that $Z$ is a lower bound which is non-empty. $\square$

Now suppose $G \curvearrowright Z$ i.e. $\forall z \in Z: gz \in Z$ and $gZ =Z$. 
Take $z \in \bigcap_{\alpha \in I} X_\alpha\implies gz \in X_\alpha$ $\forall \alpha \in I$.
$\implies gz \in Z$ $\implies gZ \subseteq Z$.
$\therefore Z \subseteq X$ is a $G$-subsystem. $\square$


Finally, by Zorn's lemma, there exists $Z_0 \subseteq X$ (closed, non-empty) $G$-system which is minimal. $\square$

### Why do we care?

>[!Result 1]
>$(X,G)$ is minimal $\iff$ $\forall x \in X$, $\overline{G\cdot x} = X$

>[!Result 2]
>If $(X,G)$ is minimal, then $\forall x \in X$ we have
>$\forall \varepsilon >0,$ $\exists$ infinitely many $g \in G$ such that $d(x,gx) < \varepsilon$.




