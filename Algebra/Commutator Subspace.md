# Definition

>[!Def]
>Let $A$ be an $\mathbb{F}$-algebra. The **commutator subspace** of $A$ is the vector subspace $[A,A]$ spanned by all elements of the form $[a,b] = ab-ba$, for $a,b \in A$.

- $[A,A]$ is NOT usually a subalgebra or even a ring.

## Lemma

>[!Lemma] Lemma 10J
>1. Let $A_1,...,A_n$ be $\mathbb{F}$-algebra. Then 
>   $$[A_1 \oplus \cdots \oplus A_n, A_1 \oplus \cdots \oplus A_n] = [A_1,A_1]\oplus \cdots \oplus [A_n,A_n].$$
>2. $A = \text{Mat}_d(\mathbb{F})$, then $[A,A]= \{a \in A \:|\: \text{tr}(a) = 0\} = \text{SL}(\mathbb{F})$ and $\dim A / [A,A] = 1$.
>3. $A = \text{Mat}_d(\mathcal{O})$, for division ring $\mathcal{O}$ over $\mathbb{F}$, then $[A,A] = \{a \in A \:|\: \text{tr}(a) = 0\}$ and $\dim A/[A,A] = \dim \mathcal{O}$.
>4. If $\mathcal{O}$ is a *commutative* division ring over $\mathbb{F}$, then $[\text{Mat}_n(\mathcal{O}), \text{Mat}_n(\mathcal{O})] = \text{SL}_n(\mathcal{O})$.
>   Consequently, $\dim A / [A,A] \geq 1$.
##### Proof
Tutorial 8

## Corollary

>[!Corollary]
>If $A$ is semisimple, then 
>$$\# \text{Irr}(A) \leq \dim A /[A,A]$$
>with equality if $A$ is Schurian.
##### Proof
Let $\mathcal{O}_i = \text{End}_A D_i$ for $1 \leq i \leq t$.  By Artin-Wedderburn Theorem
$$A/[A,A] = \left(\bigoplus_{i=1}^t \text{Mat}_{d_i}(\mathcal{O}_i^{op})\right)/[A,A]$$
where $d_i = \frac{\dim D_i}{\dim \mathcal{O}_i}$.
Also
$$
[A,A] = \left[\bigoplus_D \text{Mat}_{a_D}(\mathcal{O}_D)\:,\:\bigoplus_D \text{Mat}_{a_D}(\mathcal{O}_D) \right] = \bigoplus_{i=1}^t \left[\text{Mat}_{a_D}(\mathcal{O}_D)\:,\:\text{Mat}_{a_D}(\mathcal{O}_D) \right].
$$
Hence by Lemma 10J(b), $\dim A/[A/A] \geq t = \text{Irr}(A)$.



