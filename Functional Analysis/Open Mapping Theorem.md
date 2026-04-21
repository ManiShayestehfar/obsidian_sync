# Open Map

>[!Definition]
>$X,Y$ normed vector spaces. A function $f:X \to Y$ is **open** if 
>$$U \text{ open in } X \implies f(U) \text{ open in } Y$$

## Example

1. $\sin: \mathbb{R} \to \mathbb{R}$ is *NOT* open. e.e.g $\sin(-10,10) = [-1,1]$ (closed)
2. $f(x) = x$ is open for $f: \mathbb{R} \to \mathbb{R}$.

---
# Open Mapping Theorem

>[!Theorem] Banach-Schauder Theorem
>Let $X,Y$ be Banach. If $T \in \mathcal{L}(X,Y)$ is *surjective*, then $T$ is *open*.
##### Proof

>[!Lemma] Lemma 1
>Let $T\in \mathcal{L}(X,Y)$. $X,Y$ Banach.
>The following are equivalent:
>1. $T$ is open
>2. $\exists r >0$ such that $B_Y(0,r)\subset T(\overline{B(0,1)})$.
>3. $\exists r >0$ such that $B_Y(0,r) \subset \overline{T(\overline{B(0,1)})}$
###### Proof
**1 -> 2:**  $0 \in T(B(0,1))$ since $T(0) = 0$. So $\exists r >0$ such that $B_Y(0,r) \subseteq T(\overline{B(0,1)})$.

**2 -> 3:** Clearly $T(\overline{B(0,1)})$ is inside its closure.

**3 -> 1:** Let $U \subseteq X$ be open, and take $x \in U$.
We need to show $\exists r >0$ such that $\forall y \in B(Tx,r): \: y \in T(U)$. 

Since $U$ is open, $\exists \epsilon>0$ such that $x+ \epsilon \cdot \overline{B(0,1)}\subseteq U$.
$\implies T(x+ \epsilon \cdot \overline{B(0,1)})\subseteq T(U)$.
But by linearity of $T$, $\implies T(x+ \epsilon \cdot \overline{B(0,1)}) = T(x) + \epsilon \cdot T(\overline{B(0,1)}) \subseteq T(U)$. 
Using the assumption, $Tx + \epsilon \cdot B_Y(0,r) \subseteq T(U)$.
Therefore, $Tx + \epsilon\cdot r B_Y(0,1)\subseteq T(U)\implies B(Tx, \epsilon r) \subseteq T(U)$.

**3 -> 1:** Assume $\exists r > 0$ such that $B_Y(0,r) \subseteq \overline{T(\overline{B(0,1)})}$.
We need to show $\exists \epsilon >0$ such that $B_Y(0,\epsilon) \subset  \overline{T(\overline{B(0,1)})}$.

*Claim:* $\epsilon = r/2$ works.
Let $y \in B_Y(0,r/2)$. $\implies 2y \in B_Y(0,r)$.
By the assumption, $\exists x_1 \in \overline{B_X(0,1)}$ (i.e.e $\|x_1\|\leq 1$) such that $\|2y - Tx_1\|_Y < r/2$. 
Call $y_1 := 2y-Tx_1$. Then $\|y_1\|\in B_Y(0,r/2)$.
$\implies \exists x_2 \in \overline{B_X(0,1)}$ (i.e. $\|x_2\| \leq 1$) such that $\|ty_1- Tx_2\| < r/2$.

Doing this procedure $n$-times, we get:
$\|2^ny - 2^{n-1}Tx_1 - 2^{n-2}Tx_2 - ... - Tx_n\| < r/2$ (where $\|x_j\| \leq 1$)
Then 
$$\left\| y - \sum_{k=1}^n \frac{1}{2^k} Tx_k\right\| < \frac{r}{2^{n+1}}.$$
 
>[!Lemma] Lemma 2
>Let $S \subseteq V$ (a normed vector space) be *convex* and *symmetric* ($x \in S \implies -x \in S$). Then
>1. If $\text{int}(S) \neq \varnothing \implies 0 \in \text{int}(S)$
>2. $\overline{S}$ is also convex and symmetric.
###### Proof
**1.** If $x \in \text{int}(S)$, then $\exists \epsilon>0$ such that $B(x,\epsilon) \subseteq S$.
Then for all $y \in Y$ with $\|y\| < \epsilon$, we have $x\pm y \in S$.
Since $S$ is symmetric, then $-(x\pm y)\in S$. $\implies x+y,-x+y \in S$.
Since $S$ is convex, take $\lambda =1/2$: $1/2(x+y) + 1/2(-x+y) = y \in S$.
So $\forall \|y\| < \epsilon$, $B(0,\epsilon)\subseteq S$.

**2.** is obvious $\square$

If $Y$ is a normed space, for all $n \geq 1$ we can define the map $S_n y := ny$  where $S_n:Y \to Y$ is a *homeomorphism* (check).
$\implies \forall$ closed set $A \subseteq Y$ we have $\overline{S_n(A)} = S_n(A)$ (since the image of a homeomorphism is closed, since the preimage is closed).

Since $T$ is surjective, we have $Y = \bigcup_{n=1}^\infty \overline{T(n \overline{B(0,1)})}$.
By Baire's Theorem: $\exists n \geq 1$ such that $\text{int}(\overline{T(n\cdot \overline{B(0,1)})})\neq \varnothing$.
Since $T$ is linear, $T(n \cdot \overline{B(0,1)}) = n\cdot T(\overline{B(0,1)})$.
Hence $\text{int}(n \cdot\overline{T(\overline{B(0,1)})})\neq \varnothing\ \implies \text{int}(\overline{T(\overline{B(0,1)})})\neq \varnothing$

Applying Lemma 2(b) twice, and the fact that $T(S)$ is convex, symmetric provided that $S$ is convex and symmetric.

By Lemma 2(a), $\exists r>0$ such that $B(0,r) \subset \overline{T(\overline{B(0,1)})}$.
Now by Lemma 1(c), $T$ is open. $\square$

---

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