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

Let $\mathcal{L}(V) = \{S\subseteq V \:|\: S \text{ is linearly indep.}\}$ 
Then $(\mathcal{L}, \subseteq)$ is a non-empty poset.

Then by lemma, it is enough to find a maximal element in $\mathcal{L}$ to prove the existence of Hamel Basis.

Let $C = (\mathcal{L}_\alpha)_{\alpha \geq 1}$ be a chain. So, for $\alpha,\beta \in A$, either $L_\alpha \subseteq L_\beta$ or $L_\beta \subseteq L_\alpha$. Let $$\mathcal{L} = \bigcup_{\alpha \in A} L_\alpha.$$Clearly this is an upper bound, provided that it really is in $\mathcal{L}$. i.e. provided it is linearly independent if $v_1,...,v_n \in \mathcal{L}$, then there are $\alpha_1,...,\alpha_n \in A$ with $v_j \in L_{\alpha_j}$.
Since $C$ is a chain, there is $1 \leq k\leq n$ with $L_{\alpha_j}\subseteq L_{\alpha_k}$ for all $j \in\{1,...,n\}$. 
So $v_1,...,v_n \in L_{\alpha_k}$, since this set is linearly independent, so too is $\mathcal{L}$.

By Zorn's lemma if every chain has an upper bound, then there is a maximal linearly independent set which is the basis, call it $\mathcal{M}$.     $\square$

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

Zorn's Lemma is equivalent to the following: Given $(\mathcal{P}, \leq)$ a non-empty poset such that any chain $C \subseteq \mathcal{P}$ has a *lower* bound contains a *minimal* element.

>[!Theorem] 
>Any $G$-system $(X,G)$ contains a minimal subsystem
##### Proof
Define a poset of $G$-subsystems on $(X,G)$ with "$\leq$" which is containment. 

>[!Claim] 
>Any chain has a lower bound

- If $C \subseteq \mathcal{P}$ is a chain defined as $C := (X_\alpha)_{\alpha \in I}$. 
  Then define $Z := \bigcap_{\alpha \in I}X_\alpha$, which is closed as an intersection of closed sets, and is non-empty by the Finite Intersectivity Property (FIP), which states:
	- If $X$ is a compact set then it has a finite intersectivity property. i.e. 
	  If $(F_\alpha)_{\alpha \in I} \subseteq X$ is a familty of closed subsets such that for any finite subset of indices $J \subseteq I$, $$\bigcap_{\alpha \in J}F_\alpha \neq \varnothing \implies \bigcap_{\alpha \in I}F_\alpha \neq \varnothing$$
	- The point is that $Z$ is a lower bound which is non-empty. $\square$

Now suppose $G \curvearrowright Z$ i.e. $\forall z \in Z$  

## Proof of Hahn-Banach Theorem



