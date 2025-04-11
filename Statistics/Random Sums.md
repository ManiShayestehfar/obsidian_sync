>[!info] Definition 
>Let $X_i$ be iid RVs and let $N$ be an independent $\mathbb{N}-$valued RV. The **random sum** is
>$$T = \sum_{1}^N X_i.$$
>i.e. $T(\omega) = \sum_{1}^{N(\omega)} X_i(\omega)$

# Examples

1. $X_i = 1 \implies T = \sum_{1}^N \: 1 = N$

## Faulty Monitor

$X_i \sim \text{Bernoulli}(p)$ and $N \sim \text{Poisson}(\lambda)$, $T = \sum_1^N X_i$

![[Pasted image 20250411111352.png|600]]

**Goal:** Find $E(T)$ without first finding the distribution of $T$.

$$E\left(\sum_1^n X_i\right) = \sum_1^nE(X_i) = n E(X_i)$$
but it doesn't follow that 
$$E(T) = E\left(\sum_1^N X_i\right)\neq NE(X_i)$$as $N$ is a random variable. 

>[!success] True answer
>$$E(T) = E(N) E(X_i)$$
### Proof

Recall the [[Law of Total Probability]]. We establish an analogous "total expectation law"
$$E(T) = \sum_n E(T|N=n)P(N=n)$$
---
Suppose $X_i$ iid RVs and $N$ an ind. $\mathbb{N}$-valued RV. Let $S_n = \sum_1^n X_i$ and $T = \sum_{1}^N X_i = S_N$. Then for $n \in N(\Omega)$ and $s \in \mathbb{R}$
$$\begin{align*}
P(T=s \:|\: N=n) &= \frac{P(T=s, N=n)}{P(N=n)}\\[4pt]
&= \frac{P(\sum_{1}^N X_i = s\:,\: N=n)}{P(N=n)} \\[4pt]
&= \frac{P(\sum_{1}^n X_i = s\:,\: N=n)}{P(N=n)}\\[4pt]
&= \frac{P(\sum_{1}^N X_i = s)\:P(N=n)}{P(N=n)}\\[4pt]
&= P(S_n = s)
\end{align*}$$

>[!tip] Claim 
>For $n \in N(\Omega)$ the distribution of $T$ given that $N=n$ is the same as the *(unconditional)* distribution of $S_n = \sum_1^n X_i$, and in particular $S_n(\Omega) \subset T(\Omega)$ 

>[!tip] Corollary 
>If $X_i\in L^1$ and $n \in N(\Omega)$, then
>$$E(T|N=n) = nE(X_i).$$
>meaning that the conditional expectation is well-defined and real.
##### Proof

**Qualitative Realisation:** Conditional dist. of $T$ given $N=n$ is the same as $S_n$ so in particular the expectations should match. Alternatively, let $\{s_k\} = T(\Omega)$

$$\begin{align*}
\sum_k |s_k| \:P(T=s_k \:|\: N=n) &= \sum_k |s_k| \:P(S_n = s_k)\\[4pt]
&= E(|S_n|) \tag{$S_n(\Omega) \subset T(\Omega)$} \\[4pt]
&= E\left(\left|\sum_1^n X_i\right|\right) \\[4pt]
&< \infty
\end{align*}$$
$\implies  E(T|N=n)$ is well-defined. Moreover
$$\begin{align*}
\sum_k s_k\:P(T=s_k|N=n) &= \sum_k s_k \:P(S_n=s_k) \\[4pt]
&= E(S_n) \\[4pt]
&= \sum_{1}^n E(X_i) \\[4pt]
&= nE(X_i)

\end{align*}$$