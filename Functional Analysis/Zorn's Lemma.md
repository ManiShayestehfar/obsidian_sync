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






