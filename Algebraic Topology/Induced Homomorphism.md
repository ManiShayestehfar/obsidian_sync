**Notation:** If $x_0\in X, y_0 \in Y$, then for $\varphi:X \to Y$ with $\varphi(x_0) = y_0$, write $\varphi: (X,x_0) \to (Y,y_0)$.

>[!lemma] 
>Any continuous map $\varphi:(X,x_0)\to (Y,y_0)$ induces a homomorphism $\varphi_*:\pi_1(X,x_0) \to \pi_1(Y,y_0)$ given by $\varphi_*([f]) = [\varphi \circ f]$.
>If $\varphi$ is already a homeomorphism then $\varphi_*$ is an isomorphism.
- $\pi_1$ is a functor and so it preserves functorial properties
##### Proof

*Well-defined:* If $f_t$ is a homotopy of loops based at $x_0$ in $X$, then $\varphi \circ f_t$ is a homotopy of loops based at $y_0$ in $Y$. So $\varphi_*([f_0]) = [\varphi \circ f_0] = [\varphi \circ f_1] = \varphi_*([f_1])$.

*Homomorphism:* $\varphi \circ(f\cdot g) = (\varphi \circ f) \cdot (\varphi \circ g)$ from the definition of composition of paths. So $$\begin{align*}
\varphi_*([f][g]) &= \varphi_*([f\cdot g]) \\
&= [\varphi \circ (f \cdot g) ] \\
&= [(\varphi \circ f) \cdot (\varphi \circ g)] \\
&= [\varphi \circ f][\varphi \circ g] \\
&= \varphi_*([f])\varphi_*([g])
\end{align*}$$
*Isomorphism from Homeo:* If $\varphi$ is a homeomorphism, then $\exists\: \varphi^{-1}:Y \to X$ that is continuous.
Consider two compositions $\varphi^{-1} \circ\varphi = \text{id}_X$, and $\varphi \circ\varphi^{-1}= \text{id}_Y$. Then the induced homomorphism
$$\begin{align*}
(\varphi^{-1}\circ \varphi)_* &= (\varphi^{-1})_* \circ\varphi_* = (\text{id}_X)_* = \text{id}_{\pi_1(X,x_0)} \\
(\varphi\circ \varphi^{-1})_* &= \varphi_* \circ (\varphi^{-1})_* = (\text{id}_Y)_* = \text{id}_{\pi_1(Y,y_0)}
\end{align*}$$
tell us that $(\varphi^{-1})_*$ is the two-sided inverse to $\varphi_*$. Hence $$(\varphi^{-1})_* = (\varphi_*)^{-1}$$ and so $\varphi$ is an isomorphism.  $\square$



>[!proposition] 
>For $n \geq 2$, $\pi_1(S^n)$ is trivial.
>
##### Proof
Choose basepoint $x_0 \in S^n$. Let $f$ be a loop based at $x_0$. 

If there is a hole in the image of $f$, i.e. if $\exists x \in S^n$ such that $x \not \in f(I)$, then because $S^n\setminus\{x\}$ is homeomorphic to $\mathbb{R}^n$ (which is simply-connected), then $f$ is nullhomotopic.

Otherwise, it suffices to show $f$ is homotopic to a non-surjective map. 
Choose $x \neq x_0$, and let $B$ be a small open ball around $x$. Then $f^{-1}(B)$ is open in $[0,1]$ (as it isn't near endpoints of $f$ at $x_0$). So $f^{-1}(B) = \sqcup_i (a_i,b_i)$, a disjoint union of open intervals in $(0,1)$. Now $f^{-1}(x)$ is compact as it is the preimage of a closed set under a continuous map from a compact set $[0,1]$. Therefore $f^{-1}(x) \subseteq \sqcup_{j=1}(a_{ij}, b_{ij})$.

![[Induced Homomorphism-1759662647099.png|200]]


Now define $f_j := f|_{[a_{ij}, b_{ij}]}$. This has image in $\bar{B}$ and endpoints in $\partial B \cong S^{n-1}$. Since $n \geq 2$, we can homotope $f_j$ to $g_j:[a_{ij},b_{ij}] \to \partial \bar{B}$ in $\partial \bar{B}$. Do this for $j=1,...,n$ to get $f'\simeq f$ with $f'$ not surjective. Here,

![[Induced Homomorphism-1759662859493.png|300]]

therefore $x \not \in f'(I)$ and so $f'$ is nullhomotopic $\implies$ $\pi_1(S^n)$ is trivial. $\square$

# Induced Inclusion

>[!proposition]  
>1. If $X$ retracts to subspace $A$ and $x_0 \in A$, then the homomorphism $$i_*: \pi_1(A,x_0) \to \pi_1(X,x_0)$$ induced by the inclusion map is *injective*.
> 2. If $A$ *deformation retracts* to $X$, then $i_*$ is an isomorphism.
##### Proof
###### Part 1
 Let $r:X \to A$ be a retraction. Then $r \circ i= \text{id}_A$, so $r_* \circ i_* = (r \circ i)_* = (\text{id}_A)_* = \text{id}_{\pi_1(A,x_0)}$ by previous results. Since $\text{id}_{\pi_1(A,x_0)}$ is injective, then so is $i_*$.  $\square$

###### Part 2

Suppose $f_t:X\to X$ is a DR from $X \to A$. i.e. $f_0=\text{id}_X$, $f_1(X)=A$, and $f_t|_A = \text{id}_A$, and $(x,t) \mapsto f_t(x)$ is continuous.

Let $[g] \in \pi_1(X,x_0)$ so $g$ is a loop based at $x_0$. Then $f_t \circ g$ is a homotopy from $f_0 \circ g = g$ to $f_1 \circ g$, which is a loop based in $A$ at $x_0$. So $[g] = [f_1 \circ g] = [i \circ f_1 \circ g] = i_*([f_1 \circ g])$
 and therefore $i_*$ is surjective, and hence an isomorphism. $\square$ 

## Examples

1. $\mathbb{R}^2\setminus\{0\}$ DRs to $S^1$. SO $\pi_1(\mathbb{R}^2\setminus\{0\})\cong \pi_1(S^1) = \mathbb{Z}$.
2. For $n\geq 3$, $\mathbb{R}^n \setminus\{0\}$ DRs to $S^{n-1}$ $\implies$ $\pi_1(R^n \setminus \{0\}) \cong \pi_1(S^{n-1}) \cong 1$.


# Induced homotopy equivalence

>[!proposition] 
> If $\varphi:X\to Y$ is a homotopy equivalence, then for all $x_0 \in X$, $\varphi_*:\pi_1(X,x_0) \to\pi_1(Y,\varphi(x_0))$ is an isomorphism.
##### Proof
Assingment 1, Q1.


