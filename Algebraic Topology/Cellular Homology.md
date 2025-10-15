# Little summary

| Homology       | Complex                | Gluing                                                            |
| -------------- | ---------------------- | ----------------------------------------------------------------- |
| **Singular**   | CW Complex             | Maps are continuous                                               |
| **Simplicial** | $\Delta$-Complex       | Require faces of $k$-simplex to be an $(n-1)$-simplex from before |
| **Cellular**   | Cellular chain complex | "Homology squared" Complex                                        |

>[!lemma] H lemma 2.34
>Let $X$ be a CW-complex.
>1. $H_n(X^k, X^{k-1}) =0$ for $k \neq n$.
>   For $k=n$, this is a free abelian group with basis in 1:1 correspondence with the n-cells of $X$.
> 2. $H_k(X^k)=0$ for $k > n$.
>    If $X$ is finite-dimensional, $H_k(X)=0$ for $k > \dim X?$
> 3. We have $X^n \hookrightarrow X$, and the induced map $H_k(X^n) \to H_k(X)$.
>    For $k < n$, the induced map is an isomorphism, and surjective if $k=n$.
##### Proof
###### 1)
Let $(X^n,X^{n-1})$ be a good pair. 
Then $X^n/X^{n-1} \cong \sqcup_\alpha e_\alpha^n$. Therefore 
$$H_k(X^{n},X^{n-1}) \overset{\text{prop 2.22}}{\cong} H_k(X^n/X^{n-1}) \cong \oplus_\alpha \:H_k(e_\alpha^n) \cong \oplus_\alpha \: \mathbb{Z} \cong \mathbb{Z}^{\#\text{n-cells}}$$
for $k=n$, and $0$ otherwise. $\square$ 

###### 2) 
Need to show that $H_k(X^n) = 0$ for $k > n$. 

![[Screenshot 2025-10-16 at 8.50.24 am.png]]

If $k > n$, $H_k(X^{n-1}) \overset{\cong}{\longrightarrow}H_k(X^n)$, and we get the sequence
$$H_k(X^0) \overset{\cong}{\longrightarrow}H_k(X^1) \overset{\cong}{\longrightarrow}\cdots \overset{\cong}{\longrightarrow}H_k(X^{k-1})\hookrightarrow H_k(X^k) \overset{}{\longrightarrow} H_k(X^{k+1}) \overset{}{\longrightarrow}\cdots$$
Hence, $H_k(X^n) \cong H_k(X^0) = 0$ if $k > 0$. $\square$ 