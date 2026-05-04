# Definition

>[!Definition]
>Let $X,Y$ be normed vector spaces.
>An operator $T \in \text{Hom}(X,Y)$ is **compact** if
>$$B\subseteq X \text{ compact } \implies T(B) \text{ is \textbf{relatively compact}}$$
>i.e. $\overline{T(B)}$ is compact in $Y$.


# Propositions

>[!Proposition]
>$$T \text{ compact }\implies T \text{ continuous }$$
##### Proof
Let $B = \{x \in X \:|\: \|x\| \leq 1\}$ be bounded. So $\overline{T(B)}$ is compact and hence bounded.
So $\|Tx\|\leq M$ whenever $\|x\|\leq 1$.
So $T \in \mathcal{L}(X,Y)$ with $\|T\|\leq M$. $\square$

>[!Proposition]
>Let $X,Y$ be normed spaces and $T \in \mathcal{L}(X,Y)$. Then
>$$T \text{ is compact } \iff T(\overline{B(0,1)}) \text{ is relatively compact}$$
##### Proof
NEED TO PROVE

>[!Proposition]
>Let $X$ be a normed space. 
>The identity $I:X \to X$ is compact $\iff$ $\dim(X) < \infty$.
##### Proof
If $I$ is compact,  $\overline{I(\overline{B(0,1)})} = \overline{B}(0,1)$ is compact, so $\dim(X) < \infty$ from before.

Conversely if $\dim(X)<\infty$, Then $\overline{B}(0,1)= \overline{I(\overline{B(0,1)})}$ is compact by [[Main Definitions|Fish's Heine-Borel]], so $I$ is compact by the previous proposition. $\square$



# Characterisation of Compact Operators

>[!Theorem]
>Let $X,Y$ be normed spaces and $T \in \mathcal{L}(X,Y)$. Then the following are equivalent.
>1. $T$ is compact
>2. If $(x_n)_{n\geq1}$ is bounded in $X$, then $(Tx_n)_{n\geq 1}$ has a convergent subsequence in $Y$.
##### Proof
###### 1 -> 2
Let $(x_n)_{n\geq 1}$ be bounded in $X$. Then $B = \{x_n \:|\: n\geq 1\}$ is bounded and so $\overline{T(B)}$ is compact, hence sequentially compact, so $(Tx_n)$ has a convergent subsequence.
###### 2 -> 1
Let $B \subseteq X$ be bounded. Let $(y_n)$ be a sequence in $T(B)$. 
So $y_n=Tx_n$ for $x_n \in B$, and $(x_n)$ is bounded in $X$ (by assumption). 
So $(Tx_n)$ has a convergent subsequence in $Y$.

This shows that every sequence in $T(B)$ has a convergent subsequence. 
This implies that every sequence in $\overline{T(B)}$ has a convergent subsequence so $\overline{T(B)}$ is compact.
$\square$


## Application

>[!Corollary]
>Let $X,Y$ be normed spaces. 
>If $T_1,T_2 \in \mathcal{L}(X,Y)$ are compact, and $\lambda,\mu \in \mathbb{K}$, then $\lambda T_1+\mu T_2$ is compact.
>
i.e. $\mathcal{K}(X,Y) =\{T\in \mathcal{L}(X,Y) \:|\: T \text{ is compact }\}$ is a normed space.
##### Proof
Using previous characterisation, let $(x_n)$ be a bounded sequence in $X$.
Since $T_1$ is compact, $(T_1x_n)$ has a convergent subsequence $(T_1x_n')$ where $(x_n')$ is a subsequence of $(x_n)$.
Since $(x_n')$ is bounded and $T_2$ is compact, there is a subsequence $(x_n'')$ of $(x_n')$ such that $(T_2x_n'')$ converses and so $((\lambda T_1+\mu T_2)x_n'')$ converges.
Thus $\lambda T_1+\mu T_2$ is compact. $\square$


# Identifying Compact Operators

We need an approach to prove a given operator is compact.

>[!Theorem]
>Let $X$ be a normed space, and $Y$ a *Banach* space.
>If each $T_n \in \mathcal{L}(X,Y)$ is compact and $T_n \to T$ in $\mathcal{L}(X,Y)$, then $T$ is compact.

- So $\mathcal{K}(X,Y)$ is a *closed* subspace of $\mathcal{L}(X,Y)$ and hence is a Banach space as $Y$ complete implies $\mathcal{L}(X,Y)$ is complete.
##### Proof
Let $(x_m)$ be a bounded sequence in $X$.
**Aim:** construct a sequence $(x_m')$ such that $(Tx_m')$ converges in $Y$.

- Since $T_1$ is compact, $(x_m)$ has a subsequence $(x_m^{(1)})$ such that $(T_1x_m^{(1)})$ converges.
- Since $T_2$ is compact, $(x_m^{(1)})$ has a subsequence $(x_m^{(2)})$ such that $(T_2x_m^{(2)})$ converges.
- Continuing, $(x_m^{(k-1)})$ has a subsequence $(x_m^{(k)})$ such that $T_j(x_m^{(k)})$ converges for all $j \leq k$.
Consider $x_m'=x_m^{(m)}$ (a subsequence of $(x_m)$).
By construction, $(x_m')$ is a subsequence of $(x_m^{(k)})$ and so for each fixed $k$, $(T_kx_m')$ is convergent.

>[!Claim]
>$(Tx_m')$ is Cauchy in $Y$, and hence converges as $Y$ is complete (Banach).
###### Proof
Since $(x_m)$ is bounded, $\|x_m'\|\leq M$ for all $m \geq 1$. Then
$$\begin{align*}
\|T x_m' - T x_n'\|
&\le \|T x_m' - T_k x_m'\| + \|T_k x_m' - T_k x_n'\| + \|T_k x_n' - T x_n'\| \\[3pt]
&\le \|T - T_k\| \,\|x_m'\| + \|T_k x_m' - T_k x_n'\| + \|T_k - T\| \,\|x_n'\| \\[3pt]
&\le 2M \|T - T_k\| + \|T_k x_m' - T_k x_n'\|.
\end{align*}$$
Let $\epsilon >0$. Since $T_k \to T$,  there is $k_0>0$ such that $\|T-T_k\|< \frac{\epsilon}{3M}$ for $k \geq k_0$. So
$$\|Tx_m' - Tx_n'\|\leq \frac{2}{3}\epsilon + \|T_{k_0}x_m' - T_{k_0}x_n'\|.$$
Since $(T_{k_0}x_n')$ converges, there is $n_0>0$ so that 
$$\|T_{k_0}x_m' - T_{k_0}x_n'\| < \frac{\epsilon}{3}\qquad \forall m,n \geq n_0.$$
So $\|Tx_m'-Tx_n'\|\leq \frac{2}{3}\varepsilon + \frac{1}{3}\varepsilon = \varepsilon$ when $m,n \geq n_0$.  $\square$


## Finite Rank

>[!Definition]
>$T \in \mathcal{L}(X,Y)$ is **finite rank** if $\dim (\text{im }T)< \infty$.

>[!Proposition]
>Let $X,Y$ be normed vector spaces. 
>If $T \in \mathcal{L}(X,Y)$ has finite rank, the $T$ is compact.
##### Proof
NEED TO PROVE

### Example
The operator $T:\ell^1\to\ell^1$ with $T_x= (\frac{x_1}{1},\frac{x_2}{2},...)$ is compact.
To see this: define $T_n:\ell^1\to\ell^1$ as 
$$T_nx= \left(\frac{x_1}{1},\frac{x_2}{2},...,\frac{x_n}{n},0,0,...\right)$$
So $T_n$ is compact (finite rank).
Also $T_n \to T$ because
$$\begin{align*}
\|(T - T_n)x\|_1
&= \left\| \big(0, \ldots, 0, \tfrac{x_{n+1}}{n+1}, \tfrac{x_{n+2}}{n+2}, \ldots \big) \right\|_1 \\
&= \sum_{k=n+1}^{\infty} \frac{|x_k|}{k} \\
&\le \frac{1}{n+1} \|x\|_1.
\end{align*}$$
so $\|T-T_n\|\leq \frac{1}{n+1} \to 0$ so $T_n \to T$. $\square$

