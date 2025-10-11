# Relative Homology Groups

>[!def] $C_n(X,A)$
>$A \subseteq X$, let $C_n(X,A) := C_n(X)/C_n(A)$. i.e. the chains in $A$ are trivial in $C_n(X,A)$.
>- Boundary map $\partial:C_n(X) \to C_{n-1}(X)$ takes $C_n(A)$ to $C_{n-1}(A)$ and so it induces a *quotient boundary map* $\partial: C_n(X,A) \to C_{n-1}(X,A)$ via $x + C_n(A) \longmapsto \partial(x)+C_n(A)$. 

- This gives a sequence of boundary maps $\cdots \overset{}{\longrightarrow} C_n(X,A)\overset{\partial}{\longrightarrow} C_{n-1}(X,A)\overset{}{\longrightarrow}\cdots$
- $\partial^2 = 0$ as before

>[!def] 
>The **relative homology group** $H_n(X,A) := \ker \partial/\text{im }\partial$.
>- Elements of $H_n(X,A)$ are represented by *relative cycles*. i.e. n-chains $\alpha \in C_n(X)$ such that $\partial \alpha \in C_{n-1}(A)$.
>- A relative cycle is trivial in $H_n(X,A) \iff \alpha \in \text{im }\partial \iff$ it is a *relative boundary*. i.e. $\alpha=\partial\beta+\gamma$ for some $\beta\in C_{n+1}(X)$ and $\gamma \in C_n(A)$.

- **Note:** $C_n(X)/C_n(A)$ can be viewed as a subgroup of $C_n(X)$ but $\partial(C_n(X)/C_n(A)) \neq C_{n-1}(X)/C_{n-1}(A)$.

## Property

- Given $A \subseteq X$, we have a long exact sequence 
  ![[Relative Homology-1760172984496.png|600]]
