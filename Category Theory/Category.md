# Category

> [!def] Categories
> A **category** $\mathbf{C}$ consists of 
> - A collection of *objects* $\text{Ob}(\mathbf{C})$;
> - A set of *morphisms* $\text{Hom}_{\mathbf{C}}(X,Y)$ for all $X,Y \in \mathbf{C}$
> such that
> 1. exists a morphism $g\circ f \in \text{Hom}_\mathbf{C}(X,Z)$ for all $f \in \text{Hom}_\mathbf{C}(X,Y)$ and $g \in \text{Hom}_\mathbf{C}(Y,Z)$;
> 2. exists a morphism $\text{id}_X$ for all $X \in \mathbf{C}$ satisfying $\text{id}_Y f = f = f\text{id}_X$ for all $f \in \text{Hom}_\mathbf{C}(X,Y);$
> 3. morphisms are associative. i.e. $h(gf) = (hg)f$ 

# Some Facts

- The $\text{End}_\mathbf{C}(X)$ is a monoid. Categories are in some sense monoids that are glued together

# Pair Category

>[!def] Pair Categories
>For any category $\mathbf{C}$, the **pair category** $\mathbf{C} \times \mathbf{C}$ is the category whose objects and morphisms are pairs of their corresponding types. i.e.
>$$\text{Ob}(\mathbf{C} \times \mathbf{C}) = \{(X,Y) \:|\: X,Y \in \mathbf{C}\},$$$$\text{Hom}_{\mathbf{C} \times \mathbf{C}}((X,Y), (Z,A)) = \text{Hom}_{\mathbf{C}}(X,Z) \times \text{Hom}_{\mathbf{C}}(Y,A)$$
>and composition is defined component-wise. Similarly we define $\mathbf{C} \times \mathbf{C} \times ... \times \mathbf{C}$.

# Opposite Category

>[!def] Opposite Categories
>For any cat $\mathbf{C}$, the **opposite category** $\mathbf{C}^{op}$ is the category with the same objects and morphisms, but reversed composition.
>
>We write $f^{op}$ for opposite morphisms.

## Dual/Co statements

For example
- $P_\mathbf{C}(X)$ is '' $\forall Y \in \mathbf{C} \:\:\exists! \:\:f:X \to Y \in \mathbf{C}$ ''
- $P_\mathbf{C^{op}}(X)$ is '' $\forall Y \in \mathbf{C^{op}} \:\:\exists! \:\:f:X \to Y \in \mathbf{C^op}$ ''
- - $P^{op}_\mathbf{C}(X)$ is '' $\forall Y \in \mathbf{C} \:\:\exists! \:\:f:X \gets Y \in \mathbf{C}$ ''

## Duality Principle
$$\text{Property $P$ holds $\forall$ categories $\iff$ property $P^{op}$ holds $\forall$ categories}$$



# Example of Categories

## Category of Categories

- Objects are categories,
- Morphisms are functors

![[Screenshot 2025-06-25 at 8.18.33 AM.png|400]]

















