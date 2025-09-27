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
>i.e. $\varphi' = h \circ\varphi$
##### Proof
There exists a homomorphism $f: F \to F$ such that $\varphi = f \circ\varphi$. $\text{id}_F$ satisfies this so $f \equiv \text{id}_F$. Also $g \circ h$ satisfies $\varphi= (g \circ h)\circ \varphi$ $\implies g \circ h = f = \text{id}_F$ by uniqueness of $f$. 
Similarly $h \circ g = \text{id}_F$, so $h$ is an isomorphism with inverse $g$, and is unique from the top triangle.  $\square$
 
>[!proposition] existence
>For any $S$, the direct sum $\bigoplus_{s \in S} \mathbb{Z}$ is free abelian on $S$ with respect to the map $\varphi:S \to \bigoplus_{s \in S} \mathbb{Z}$, $s \mapsto g_s$ where $g_s:S \to \mathbb{Z}$ is given by:$$g_s(x) = \begin{cases}
1 & x=s  \\
0 & x \neq s
\end{cases}$$
In particular, for the finite $S$ with $|S|=n$, the free abelian group on $S$ is $\mathbb{Z}^n$ with $\varphi(s) = (0,...,0,1,0,...,0)$ where 1 is at the s-th position.


>[!proposition]
>Any abelian group $A$ is the homomorphic image of some free abelian group $F$. 
>i.e. $\exists S,F,\psi,\varphi$ as in the definition of a free abelian group such that $A = f(F)$.
##### Proof
$S \subseteq A$ is a set of generators for $A$. e.g. $S = A$ with inclusion $\psi:S \to A$. Let $F$ be the free abelian group on $S$, say w.r.t. $\varphi:S \to F$. 
Then by the universal property, there exists a unique homomorphism $f:F \to A$ with $\psi= f \circ \varphi$ so $S = \psi(S) = (f\circ \psi)(S) \subseteq f(F)$.
Since $f$ is a homomorphism, and $S$ generates $A$, then $S \subseteq f(F) \implies$ $A \subseteq f(F) \implies A = f(F)$. 








