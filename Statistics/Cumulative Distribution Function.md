>[!info] Definition
>The **Cumulative Distribution Function (CDF)** of an RV $X$ is defined as:
>$$F_X(x) := P(X\leq x)$$

>[!tip] Claim
>If $F$ is a CDF if an RV $X$ with $P(X \in \mathbb{R}) = 1$, then:
>i. $F$ is non-decreasing
>ii. $F$ is right-continuous: $\lim_{x \to x_0^+} F(x) = F(x_0)$
>iii. $\lim_{x \to \infty} F(x) = 1$ and $\lim_{x \to -\infty} F(x) = 0$
>   
>   Conversely, if $F$ satisfies 1-3 then $F$ is the CDF of some RV $X$ with $P(X \in \mathbb{R})=1$.
##### Proof
###### (i)
$a\leq b \implies \{X \leq a\} \subset \{X \leq b\}$. So
$$F(a) = P(X\leq a) \leq P(X\leq b) = F(b) \quad \quad \square$$

##### (ii)
>[!tip] Lemma (Continuity if the probability measure)
>1. If the events $A_n$ are increasing, i.e. if $A_n \subset A_{n+1}$, then $P\left(\bigcup_n A_n \right) = \lim_{n \to \infty} P(A_n)$
>2. If $A_n$ are decreasing, i.e. if $A_{n+1}\subset A_n$, then $P\left(\bigcap_n A_n\right) = \lim_{n \to \infty} P(A_n)$
##### Proof


