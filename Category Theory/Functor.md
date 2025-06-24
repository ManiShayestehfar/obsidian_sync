# Definition

>[!def] Functors
>A **functor** $F:\mathbf{C} \to \mathbf{D}$  between two categories $\mathbf{C}$ and $\mathbf{D}$ is a map sending:
>1. An object $X \in F(\mathbf{C})$ to $F(X) \in \mathbf{D}$;
>2. $(f: X\to Y) \in \mathbf{C}$ to a morphism $(F(f): F(X) \to F(Y)) \in \mathbf{D}$ 
>   
such that
>1. Composition is preserved. i.e. $F(gf) = F(g)F(f)$
>2. Identities are preserved i.e. $F({\text{id}_{X}}) = \text{id}_{F(X)}$
>

## Identity Functor

>[!def] Identity functor
>$\text{id}_{\mathbf{C}}: \mathbf{C} \to \mathbf{C}$, sends each object and each morphism to themselves.


# Lemmas

>[!lemma] 
>If $F$ and $G$ are functors, then so is $GF$.














  