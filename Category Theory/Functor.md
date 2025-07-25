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

## $\text{Hom}$ Functor

>[!def] $\text{Hom}$ functors
>$$\text{Hom}_\mathbf{C}(X,\_): \mathbf{C} \to \textbf{Set},\begin{cases}
Y \to \text{Hom}_C(X,Y)  \\[4pt]
f \to (f \circ \_ )
\end{cases},\quad \text{Hom}_\mathbf{C}(\_,X): \mathbf{C}^{op} \to \textbf{Set},\begin{cases}
Y \to \text{Hom}_C(Y,X)  \\[4pt]
f \to (\_ \circ f )
\end{cases}$$

This is 
1. Assigning to each object $Y$ an either covariant/contravariant $\text{Hom}(X,Y)$ or vice versa
2. Assigning to each morphism $f:B \to B'$ a function$$\text{Hom}_\mathbf{C}(A,f): \text{Hom}_\mathbf{C}(A,B) \to \text{Hom}_\mathbf{C}(A,B')$$
	or again, vice versa.


## Adjoint Functors

>[!def] Adjoint Functor
>Two functors $(F,G) = (F:\mathbf{C} \to \mathbf{D}, G:\mathbf{D}\to \mathbf{C})$ form an **adjoint pair** if:
>1. There exists a natural transformation $\alpha: \text{Hom}_{\mathbf{D}}({F(\_),\_)}\Rightarrow \text{Hom}_\mathbf{C}(\_, G(\_))$.
>2. For all $X,Y$ there are isomorphism $$\alpha_{X,Y}: \text{Hom}_\mathbf{D}(F(X), Y) \overset{\cong}{\to} \text{Hom}_{\mathbf{D}}(\_, G(\_))$$
>We say $F$ is the *left adjoint* of $G$, and $G$ the *right adjoint* of $F$.

- If a functor is left/right adjoint, then it is unique up to isomorphisms
### Examples

![[Screenshot 2025-07-17 at 9.34.30 pm.png]]
![[Screenshot 2025-07-17 at 10.01.09 pm.png]]

![[Screenshot 2025-07-17 at 10.02.12 pm.png]]

# Properties

>[!lemma] 
>If $F$ and $G$ are functors, then so is $GF$.

>[!proposition] 
>A functor $F:\mathbf{C} \to \mathbf{D}$ is an equivalence if and only if
>- It is *dense*. i.e. for all $Y \in \mathbf{D}$, there exists $X \in \mathbf{C}$ such that $F(X) \cong Y$;
>- It is *faithful*. i.e. $\text{Hom}_\mathbf{C}(X,Y) \hookrightarrow \text{Hom}_\mathbf{C}(F(X),F(Y))$ for all $X,Y \in \mathbf{C}$;
>- It is *full*. i.e. $\text{Hom}_\mathbf{C}(X,Y) \twoheadrightarrow \text{Hom}_\mathbf{C}(F(X),F(Y))$ for all $X,Y \in \mathbf{C}$;
>
>If a functor is full + faithful, then we say it is *fully faithful*.

Proof on page 15-16. Come back to it













  