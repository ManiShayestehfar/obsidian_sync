>[!def] 
>$S$ a set. A **free abelian group** on $S$ is an abelian group $F$, with function $\varphi:S \to F$ such that:
>- For any abelian group $A$, and function $\varphi:S \to F$, there exists a *unique* homomorphism $f:F \to A$ such that the following diagram commutes:
>![[Free Abelian Group-1754735963238.png|300]]
>i.e. $\psi = f \circ \varphi$ 

- $\varphi$ is injective, often identify $\varphi(S) \subseteq F$ with $S$, i.e. regard $\varphi$ as inclusion.
- $\varphi(S)$ *generates* $F$, i.e. element of $F$ is equal to a finite product of elements of $\varphi(S)$ and their inverses.

# Facts

>[!proposition] unique up to isomorphism
>Let $F,F'$ be free abelian groups on $S$ with respect to maps $\varphi:S \to F$, $\varphi':S \to F'$. Then there exists a unique isomorphism $h:F\to F'$ such that the following diagram commutes: (the diagram is the same as above but with $F'$ instead of $A$)

>[!proposition] existence
>For any $S$, the direct sum $\bigoplus_{s \in S} \mathbb{Z}$ is free abelian on $S$ with respect to the map $\varphi:S \to \bigoplus_{s \in S} \mathbb{Z}$, $s \mapsto g_s$ where $g_s:S \to \mathbb{Z}$ is given by:$$g_s(x) = \begin{cases}
1 & x=s  \\
0 & x \neq s
\end{cases}$$
In particular, for the finite $S$ with $|S|=n$, the free abelian group on $S$ is $\mathbb{Z}^n$ with $\varphi(s) = (0,...,0,1,0,...,0)$ where 1 is at the s-th position.









