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

Suppose $X$ is finite dimensional, then $X = X^n$ for some $n$. Then we have that $H_k(X^n) = 0$ if $k > n = \dim X$. 

###### 3)
TODO


# Cellular Chain Complex

>[!def] 
>Let $X$ be a CW-complex. We have the following commuting diagram:
>
>![[Screenshot 2025-10-16 at 9.40.31 am.png]]
>where we construct $d_i := j_{i-1} \circ \partial_i$.

- $d_n$'s form a chain complex. So $$d_n \circ d_{n+1} = j_{n-1}\circ \partial_n \circ j_n \circ \partial_{n+1} = 0$$
- The given sequence of $d_n$'s is called the **cellular chain complex** of $X$.
- The **cellular homology groups** of $X$ are $$H_n^{CW}(X) := \ker d_n / \text{im }{d_{n+1}}$$
## Equivalence of Cellular and Simplicial Homology Groups

>[!Theorem] H Thm 2.35
>$X$ a CW-complex, then $$H_n^{CW}(X) \cong H_n(X)$$
>for all $n$.
##### Proof
1. $H_n(X) \cong H_n(X^{n+1})\cong H_n^\Delta (X^n) / \ker f \cong H_n(X^n)/\text{im }\partial_{n+1}$  where the last equivalence comes from exactness and the fact that $\ker f = \text{im }\partial_{n+1}$.

2. Injectiveness of $j_n \implies$ Then $\text{im }\partial_{n+1} \cong \text{im }(j_n \circ \partial_{n+1}) = \text{im }(d_{n+1})$
3. Injectiveness of $j_n \implies$ $H_n(X^n)/ \ker j_n \cong H^n(X_n) \cong \text{im }(j_n) \cong \ker(\partial_n)$  by exactness in the end.
4. $j_{n-1}$ injective $\implies \ker \partial_n = \ker d_n$.

Hence
$$H_n(X) \overset{(1)}{\cong} H_n(X^n)/\text{im }\partial_{n+1} \overset{(2)}{\cong} H_n(X^n)/\text{im }d_{n+1} \overset{(3)}{\cong} \ker \partial_n / \text{im }d_{n+1} \overset{(4)}{\cong} \ker d_n/\text{im }d_{n+1} \cong H_n^{CW}(X)$$
$\square$ 




