
# Partial Ordering

>[!def] Partial Ordering
>A relation $<$ on a set $X$ is called a **partial ordering** of $X$ if:
>- *reflexivity:* $x < x$ for all $x \in X$
>- *Transitivity:* $x < y$ and $y < z \implies x < z$
>- *Anti-symmetry:* $x<y$ and $y < x \implies x=y$ 
>

## Examples

- $(\mathbb{R}, \leq)$ the usual ordering 
- $\mathcal{S}$ a collection of subsets of $X$. Then $(\mathcal{S}, \subseteq)$ is a poset.
- Every subset of a poset is still a poset by the induced partial order.


# Maximal, Upper bound, Chain, Totally-ordered set, First element

>[!def] 
>$(X,<)$ a poset. Then
>1. $m \in X$ is **maximal** in $X$ if $\forall x \in X$ with $m < x$, we have $x < m$
>2. $m \in X$ is an **upper bound** for $S \subseteq X$ if $x < m$ for all $x \in S$
>3. A subset $C \subseteq X$ is a **chain** in $X$ if $x < y$ or $y < x$ for all $x,y \in C$
>4. The poset $(X,<)$ is a **totally ordered set** if it is a chain
>5. $(X,<)$ a poset and $x_0 \in X$ is such that $x_0 < x$ for all $x \in X$, then $x_0$ is a **first element**

# Well-ordered Set 

>[!def] Well-ordered Set
>A poset $(X,<)$ is a **well-ordered set** if every subset has a first element

- Well-ordered $\implies$ Totally-ordered

## Example

1. $(\mathbb{N}, <)$ is well-ordered but clearly $(\mathbb{Z},<), (\mathbb{R},<)$ are not well-ordered but they are totally-ordered.

