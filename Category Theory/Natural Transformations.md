# Definition
>[!def] Natural Transformation
>A **natural transformation** $\alpha: F \Rightarrow G$ between functors $F,G: \mathbf{C \to \mathbf{D}}$ is a collection of morphisms in $\mathbf{D}$ $$\{\alpha_X: F(X)\to G(X) \:|\: X\in \mathbf{C}\}$$
>such that the following diagram commutes for all $X,Y,f\in \mathbf{C}$:
>
>![[Natural Transformations-1750944210965.png|200]]
>
>- We may consider $\alpha$ as a morphism from $F$ to $G$.

## Vertical Composition

- Composition of natural transformation

![[Natural Transformations-1750944460457.png|400]]

## Identity Natural Transformation

$\text{ID}_F: F \to F$ such that $(\text{ID}_F)_X = \text{id}_X$


# Lemmas

>[!lemma]
>If $\alpha,\beta$ are natural transformations, then so is $\beta \alpha$


# Examples

## Category of functors

$\textbf{Hom}(\mathbf{C}, \mathbf{D})$ is category of functors from $\mathbf{C}$ to $\mathbf{D}$. 
- The objects are functors
- The morphisms are natural transformations, composition being vertical composition
- An example is *endofunctors*, $\textbf{End}(\mathbf{C}) = \textbf{Hom}(\mathbf{C}, \mathbf{C})$.


 
