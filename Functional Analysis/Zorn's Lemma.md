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

By Zorn's lemma if every chain has an upper bound, then there is a maximal element. 

If we have a chain $C \subseteq (\mathcal{L}, \subseteq)$. Take $U := \bigcup_{c \in C} c\subseteq V$.
We need to show that if $v_1,...,v_n \in U$, then $\{v_1,...,v_n\}$ are linearly independent.
Then there exists $c_i \in C$ such that $v_i \leq c_i$. 

## Any topological dynamical system contains a minimal subsystem

## Proof of Hahn-Banach Theorem



