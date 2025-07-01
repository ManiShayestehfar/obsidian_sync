# Skeleton

>[!def] Skeleton
>Let $\overline{\text{Ob}(\bf C) / \cong}$ be the choice of representatives of $\text{Ob}(\bf C) / \cong$. 
>Given a category $\bf C$ its **skeleton** $\bf Sk(C)$ is the full subcategory with objects $\overline{\text{Ob}(\bf C) / \cong}$.

-  A category is *skeletal* if it is isomorphic to its skeleton


## Examples

1. The skeleton of $\bf fdVec_{\mathbb{k}}$ is $\bf Mat_{\mathbb{k}}$, the category of matrices. Then $\bf fdVec_{\mathbb{k}} \cong \bf Mat_{\mathbb{k}}$. $\text{Hom}_{\bf Mat_{\mathbb{k}}}(n,m) = \text{Mat}_{m\times n}(\mathbb{k})$  


# Grothendieck Class

>[!def] 
>Let $K_0(\mathbf{C}) = \overline{\text{Ob}(\mathbf{C}) / \cong}$ and call it the **Grothendieck class of** $\mathbf{C}$.
> Elements in $K_0(\mathbf{C})$ are Grothendieck classes of $X \in \mathbf{C}$ and are denoted by $[X]$.

## Examples

1. $K_0(\bf{fdVec_{\mathbb{k}}})\overset{\cong}{\longrightarrow} \mathbb{Z}_{\geq 0}$ as sets, with the map $[\mathbb{k}^n] \to n$ since any $X \in \bf{fdVec_{\mathbb{k}}}$ is isomorphic to $\mathbb{k}^n$ for some $n \in \mathbb{Z}_{\geq 0}$.


# Properties

>[!lemma] 
>Any functor $F \in \mathbf{Hom(C,D)}$ induces a map $$K_0(F) : K_0(\mathbf{C}) \to K_0(\mathbf{D}),\quad [X]\to [F(X)]$$
>Further, if $F$ is an equivalence, then $K_0(F)$ is an isomorphism.


