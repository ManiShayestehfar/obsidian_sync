>[!theorem] 
>For any $F \in \mathbf{Hom(C,Set)}$ and any $X \in \mathbf{C}$ there is a bijection $$\text{Hom}_{\mathbf{Hom(C,Set)}}(\text{Hom}_\mathbf{C}(X,\_), F) \to F(X), \quad (\alpha: \text{Hom}_\mathbf{C}(X,\_) \Rightarrow F) \to \alpha_X(\text{id}_X)$$
>Moreover, this correspondence is natural in both $F$ and $X$.


# Yoneda Embedding 

>[!proposition]
>![[Yoneda Lemma-1752583206291.png]]
#### Proof
By construction of Yoneda functors we see that we have injections 
$$\begin{align*}
\mathrm{Hom}_C(X, Y) &\hookrightarrow 
\mathrm{Hom}_{\mathrm{Hom}(C, \mathbf{Set})}
\left( \mathrm{Hom}_C(X, -), \mathrm{Hom}_C(Y, -) \right), \\[5pt]
\mathrm{Hom}_C(X, Y) &\hookrightarrow 
\mathrm{Hom}_{\mathrm{Hom}(C, \mathbf{Set})}
\left( \mathrm{Hom}_C(-, X), \mathrm{Hom}_C(-, Y) \right).
\end{align*}



$$
And by Theorem 1 above, every natural transformation between represented functors arises in this way, showing that the maps above are bijections. It also follows by definition that they are fully faithful.

## Example

For the category $\bf{A_3}$, having three objects and three non-identity morphisms arranged as 
![[Yoneda Lemma-1752584082885.png]]

The Yoneda functor $Y^{op}$ associates
![[Yoneda Lemma-1752585192062.png]]
etc. which identifies $({\mathbf A_3})^{op}$ with the functors of the form $\text{Hom}_{\mathbf{A_3}}(i,\_)$ for $i \in \{1,2,3\}$.