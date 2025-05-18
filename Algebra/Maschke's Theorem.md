
>[!tip] Maschke's Theorem
> - $\mathbb{F}$ be a field of characteristic $p$,
> - $G$ a finite group of order *not* divisible by $p \geq 0$.  
> - Let $V$ be a $G$-module, and $W$ a $G$-submodule of $V$. 
> 
> Then there exists a $G$-module $U$ of $V$ such that $V = U \oplus W$ as [[FG-Module|G-module]]. 
> When $U$ exists, it is called the **complement** of $W$ in $V$.
##### Proof
- It should be clear that as a [[vector space]] we can find a subspace $U'$ of $V$ such that $V = U' \oplus W$. The problem is making sure $U'$ is a $G$-module.

We can define a [[vector space]] homomorphism that is a projection map corresponding to the decomposition $V = U' \oplus W$ as $\pi: V \to W$. That is, $\pi(u+w) = w$ for $u \in U'$, $w \in W$. 

**IDEA:** $\pi$ is a $G$-module homomorphism by "averaging" over elements of $G$. i.e.
$$\pi_G(v) = \frac{1}{|G|}\sum_{x\in G}x\pi(x^{-1}v)$$
for $v \in V$. $\frac{1}{|G|}$ is well-defined in $\mathbb{F}$ as $p \nmid |G|$.  

>[!tip] Sub-claim 1
>$\pi_G$ is a $G-$module homomorphism
###### Sub-Proof
1. $\pi_G$ is linear by construction
2. Need to check $\pi_G(gv) = g\pi_G(v)$ for $v \in V$ and $g \in G$. So
$$\pi_G(gv) = \frac{1}{|G|}\sum_{x\in G}x\pi(x^{-1}gv) = \frac{1}{|G|}\sum_{y=g^{-1}x\:\in\: G}gy\pi(y^{-1}v) = g\pi_G(v)$$
	as needed.

>[!tip] Sub-claim 2
>$\pi_G$ is the identity map on $W$.
##### Sub-Proof
By definition $\text{im }\pi = W$ which is a $G$-module of $V$, so $\text{im }\pi_G$ is contained in $W$. For $w\in W$ and $w' := x^{-1}w\in W$ with $\pi(w') = w'$ for all $w' \in W$,
$$\pi_G(w) = \frac{1}{|G|}\sum_{x\in G}x\pi(x^{-1}w) = \frac{1}{|G|}\sum_{x\in G}x\omega' = \frac{1}{|G|}\sum_{x\in G}x(x^{-1}w) = w$$
Therefore 
$$W = \text{im }\pi_G \cong V / \ker \pi_G$$
with isomorphism coming from the [[Quotient Module|First Isomorphism Theorem]].  

>[!tip] Sub-claim 3
>$$V = \text{im } \pi_G \oplus \ker \pi_G$$
##### Sub-Proof

- This is the last step as we already know that $W = \text{im }\pi_G$. 

if $v \in V$, then $v = \pi_G(v) + (v - \pi_G(v))$, and as before $\pi_G \in W= \text{im }\pi_G$. On the other hand
$$\pi_G(v - \pi_G(v)) = \pi_G(v) - \pi_G(\pi_G(v)) = 0$$
as $\pi_G(v) \in \text{im }\pi_G = W$ and $\pi_G(w) = w$. 

Hence $V = W + \ker \pi_G$. But from the previous proof via the [[Quotient Module|First Isomorphism Theorem]], $\ker \pi_G \cap W = 0$ and so consequently $V = W \oplus \ker \pi_G$. Since $\ker \pi_G$ is a $G$-module this completes the proof.   $\square$ 

## Another Definition

>[!success] Maschke's Theorem in the language of irreducibles
>Suppose that $\mathbb{F}$ is a field of characteristic $p$ and that $G$ is a finite group of order not divisible by $p$. 
>
>Then every $G$-module is [[FG-Module|completely reducible]].



