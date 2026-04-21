# Open Map

>[!Definition]
>$X,Y$ normed vector spaces. A function $f:X \to Y$ is **open** if 
>$$U \text{ open in } X \implies f(U) \text{ open in } Y$$

## Example

1. $\sin: \mathbb{R} \to \mathbb{R}$ is *NOT* open. e.e.g $\sin(-10,10) = [-1,1]$ (closed)
2. $f(x) = x$ is open for $f: \mathbb{R} \to \mathbb{R}$.


# Open Mapping Theorem

>[!Theorem] Banach-Schauder Theorem
>Let $X,Y$ be Banach. If $T \in \mathcal{L}(X,Y)$ is *surjective*, then $T$ is *open*.
##### Proof



## Corollaries
### Bounded Inverse Theorem

OMT is important in understanding inverse operators
>[!Corollary]
>Let $X,Y$ be Banach. 
>$$T \in \mathcal{L}(X,Y) \text{ is bijective} \qquad\implies\qquad T^{-1}\in \mathcal{L}(Y,X)$$
>- The key point is the *continuity* of $T^{-1}$.
##### Proof
Let $U \subseteq X$ be open. Then by OMT $(T^{-1})^{-1}(U) = T(U)$ is open, so $T^{-1} \in \mathcal{L}(Y,X)$ since inverse images of open sets are open. $\square$

#### Example
Completeness of both $X,Y$ is important.
Take $T: \ell_F \to \ell_F$ given by $Tx = (x_1/1,x_2/2,x_3/3,...)$ is continuous and bijective.
Yet $T^{-1}x = (x_1,2x_2,3x_3,...)$ is not continuous since $\|T^{-1}e_n\| = n\|e_n\| \to \infty$.

*What if we replaced $\ell_F$ with $\ell^\infty$?*
Then $T: \ell^\infty \to \ell^\infty$ still still makes sense (i.e. it is continuous and injective).
However, it fails to be surjective, because if $x \in \ell^\infty$, then $Tx = (x_1/1,x_2/2,...) \in c_0$.


>[!Corollary]
>Let $X,Y$ be Banach. If $T \in \mathcal{L}(X,Y)$ is bijective, then there are constants, $c,C>0$ such that 
>$$c\|x\| \leq \|Tx\| \leq C\|x\| \qquad \forall x \in X$$
##### Proof
NEED TO PROVE

>[!Corollary]
>Let $(X, \|\cdot\|)$ and $(X, \|\cdot\|')$ be Banach.
>If $\|x\| \leq C \|x\|'$ for all $x \in X$, then $\|\cdot\|$ and $\|\cdot\|'$ are equivalent.

##### Proof
NEED TO PROVE