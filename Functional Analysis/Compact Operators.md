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
Forward direction is trivial since $\overline{B}$ is bounded.

Assume 

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
i.e. $\mathcal{K}(X,Y) :=\{T\in \mathcal{L}(X,Y) \:|\: T \text{ is compact }\}$ is a normed space.
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


# Hilbert-Schmidt Operators

>[!Proposition]
>Let $k  \in L^2([a,b]\times[a,b])$. The **Hilbert-Schmidt operator** given by $T: [a,b] \to [a,b]$ given by
>$$Tf(x) = \int_a^b K(x,y)f(y)\:dy$$
>is compact.
##### Proof
First note
$$\begin{align*}
\|Tf\|_2^2 &= \int_a^b |Tf(x)|^2\: dx \\
&= \int_a^b \left|\int_a^b K(x,y)f(y)\: dy \right|^2\:dx \\
&\overset{C.S}{\leq} \int_a^b \left(\int_a^b |K(x,y)|^2\: dy \right) \left(\int_a^b |f(y)|^2 \: dy\right)\:dx \\
&= \left(\int_a^b \int_a^b |K(x,y)|^2\: dy\:dx\right)\|f\|_2^2 \\
&= \|K\|^2 \|f\|_2^2
\end{align*}$$
So $T \in \mathcal{L}([a,b], [a,b])$, and $\|T\| \leq \|K\|_2$.

Using the step function, there are $\alpha_i,\beta_j \in L^2([a,b])$ such that
$$K_n(x,y) = \sum_{i=1}^n \sum_{j=1}^n \alpha_i(x) \alpha_j(y)$$
with $\|K-K_n\|_2 \to 0$. 
Then define 
$$T_nf(x) = \int_a^b K_n(x,y) f(y)\:dy.$$
We have 
$$T_nf(x)= \sum_{i=1}^n \left(\int_a^b \sum_{j=1}^n \beta_j(y)\:f(y)\:dy\right) \alpha_j(x),$$
and so $T_nf \in \text{span}\{\alpha_1,...,\alpha_n\}$ and we have $T_n$ is finite rank, hence $T_n$ is compact since $\|T-T_n \| \leq \|K-K_n\|$ means that $T_n \to T$. So by the identification of compact operators, $T$ is compact.  $\square$


# Further on $\mathcal{K}(X,Y)$

>[!Proposition]
>Let $X,Y,Z$ be normed vector spaces.
>1. $T \in \mathcal{K}(X,Y)$, $S \in \mathcal{L}(Y,Z) \implies ST \in \mathcal{K}(X,Z)$.
>2. $T \in \mathcal{L}(X,Y), S \in \mathcal{K}(Y,Z) \implies ST \in \mathcal{K}(X,Z)$.
##### Proof
###### 1. 
Let $(x_n)$ be bounded in $X$. 
Then $(Tx_n)$ has a convergent subsequence $(Tx_{n_k})$ such that $S(Tx_{n_k})$ converges in $Z$ as $S$ is continuous, so $ST$ is compact.
###### 2.
Let $B \subseteq X$ be bounded. Since $T$ is continuous (hence bounded), $T(B) \subseteq Y$ is bounded. 
Hence $S(T(B))$ is relatively compact (as $S$ is compact). So $ST$ is compact.
$\square$

## Applications

>[!Corollary]
>Let $X$ be a normed space. Then $\mathcal{K}(X) := \mathcal{K}(X,X)$ is a two-sided ideal of the algebra $\mathcal{L}(X)$.

>[!Proposition]
>Let $X$ be Banach over $\mathbb{C}$. If $\dim X = \infty$, then $0 \in \sigma(T)$ for all $T \in \mathcal{K}(X)$.
##### Proof
If $0 \not \in \sigma(T)$, then $T$ is invertible. By the bounded inverse theorem, $T^{-1}$ is continuous.
So $T^{-1}T =I$ is compact. But the identity map is not compact so $0 \in \sigma(T)$. $\square$


>[!warning] Remark
>For $T \in \mathcal{K}(X)$ with $\dim X = \infty$, it is possible for $0$ to be in *any part* of the spectrum.

For example, 
1. $T: \ell^2 \to \ell^2$, $Tx = (x_1/1,x_2/2,x_3/3,...)$, then $0 \in \sigma_c(T)$.
2. $T: \ell^2 \to \ell^2$, $Tx = (0, x_2/2,x_3/3,...)$, then $0 \in \sigma_p(T)$.
3. $T: \ell^2 \to \ell^2$, $Tx = (0, x_1/1, x_2/2,...)$, then $0 \in \sigma_r(T)$.

>[!Warning] Remark
>Note that neither $R: \ell^2 \to \ell^2$ or $L: \ell^2 \to \ell^2$ are compact as $I = LR$ which is not compact for in $\ell^2$.


# Approximation Property

>[!Proposition]
>Let $\mathcal{H}$ be a Hilbert space. Then 
>$$T \in \mathcal{L}(\mathcal{H}) \text{ is compact} \iff T \text{ is a limit of finite rank operators}$$
##### Proof
###### $(\Leftarrow)$
Obvious from before
###### $(\Rightarrow)$

>[!Claim]
>$Y := \text{im }T$ is separable

To show this, notice that $\mathcal{H} = \bigcup_{n=0}^\infty B(0,n)$. So $Y = \bigcup_{n=1}^\infty T(B(0,n))$.
Each $\overline{T(B(0,n))}$ is compact and hence separable since compact metric spaces are separable.
So $Y$ is a countable union of separable things, and so is separable.
Subsequently, $\overline{Y}$ is a separable Hilbert space. (End of claim proof)



Let $S=\{e_n \::\: n \geq 1\}$ be a Hilbert basis (countable).
Let $P_n$ be the projection of $\mathcal{H}$ onto $M_n = \text{span}\{e_1,...,e_n\}$.

>[!Claim]
>$P_n T \to T$ as $n \to \infty$. 

Note that $P_nT$ is finite rank with $\text{im }P_nT = M_n$.
Let $\epsilon >0$. Since $\overline{T(\overline{B(0,1)})}$ is compact, it is totally bounded. Hence there exists a finite points $z_1,...,z_N \in \overline{T(\overline{B(0,1)})}$ with sets $B(z_j,\epsilon/3) \subseteq \overline{T(\overline{B(0,1)})}$ covering it.
If $x \in \overline{B(0,1)}$ , then $Tx \in B(z_j, \epsilon/3)$ for some $j$. So
$$\begin{align*}
\|P_nTx - Tx\| &\leq \|P_nTx - P_n z_j\| + \|P_nz_j - z_j\| + \|z_j - Tx\| \\[4pt]
&\leq \|P_n\|\|Tx - z_j\| + \|P_nz_j - z_j\| + \|z_j - Tx\| \tag{$\|P_n\|=1$}\\[4pt]
&= 2\|Tx-z_j\| + \|P_nz_j - z_j\|.
\end{align*}$$
Since $z_j \in \overline{Y}$, then $P_n z_j \to z_j$, so there is $n_0>0$ with $\|P_n z_j-z_j\|<\epsilon/3$ for all $j$ and all $n > n_0$.
Since $Tx \in B(z_j, \epsilon/3)$, $\|P_nTx - Tx\| \leq 2 \epsilon/3 + \epsilon/3 < \epsilon$.
So $P_nT \to T$ as required. $\square$
 


# Compact Operators on Banach Spaces 

##  Theorem

>[!Theorem]
>Let $X$ be infinite dimensional [[Banach Spaces|Banach space]] over $\mathbb{C}$, and $T \in \mathcal{L}(X)$ be compact. Then
>1. $0 \in \sigma(T)$
>2. $\sigma(T) \setminus \{0\} = \sigma_p(T) \setminus \{0\}$
>3. $\sigma_p(T)$ is either finite (possibly empty) or is a countable sequence of complex numbers converging to zero
>4. If $\lambda \in \sigma(T) \setminus \{0\}$, then the eigenspace $\ker (\lambda I - T)$ is finite dimensional.
#### Proof
##### 1.
If $0 \not \in \sigma(T)$, then $T$ is invertible. By the bounded inverse theorem, $T^{-1}$ is continuous.
So $T^{-1}T =I$ is compact. But the identity map is not compact so $0 \in \sigma(T)$. 

##### 3. 
We can show that for each $N > 0$:    $\# \{\lambda \in \sigma_p(T) \:|\: |\lambda |\geq N \} < \infty$.
Suppose there is $N >0$ such that the number is infinite. So there are distinct eigenvalues $\lambda_1,\lambda_2,...$ of $T$ for which $|\lambda_j| \geq N$. 
Choose nonzero $\lambda_n$-eigenvectors $x_n$ such that $Tx_n = \lambda_n x_n$.
Let $X_n = \text{span}\{x_1,...,x_n\}$. Since $\{x_1,...,x_n\}$ is linearly independent we have 
$$X_1 \subsetneq X_2 \subsetneq X_3 \subsetneq \cdots$$
Since each $X_n$ is finite-dimensional, they are closed. So by [[The Unit Ball| Riesz's Lemma]], there is $x_n' \in X_n$ such that $\|x_n'\|=1$ with $\|x_n'-x\| \geq \frac{1}{2}$ for all $x \in X_{n-1}$.
Thus $(x_n')_{n\geq1}$ is a bounded sequence.

>[!Claim] 
>$(Tx_n')_{n\geq 1}$ has no convergent subsequence, hence $T$ is not compact.
>
###### Proof
$Tx_n' \in X_n$ since $x_n' = \sum_{k=1}^n a_k x_k$. So 
$$Tx_n' = \sum_{k=1}^n a_k Tx_k = \sum_{k=1}^n \lambda_k a_k x_k \in X_n.$$
Also $\lambda_n x_n' - Tx_n' = \sum_{k=1}^{n-1} a_k(\lambda_n - \lambda_k)x_k \in X_{n-1}$.
So if $m > n$, then we have 
$$\begin{align*}
\|Tx_m' - Tx_n'\| &= \| \lambda_m x_m' - (\underbrace{\lambda_mx_m' - Tx_m'}_{\in X_{m-1}}) + \underbrace{Tx_n'}_{\in X_n \subseteq X_{m-1}}\| \\
&= |\lambda_m| \left\|x_m' - \frac{1}{\lambda_m} \underbrace{((\lambda_mx_m' - Tx_m') + Tx_n')}_{\in X_{m-1}}\right\| \\
&\geq \frac{1}{2}|\lambda_m| \geq \frac{1}{2}N
\end{align*}$$
So there is no convergent subsequence $\square$

Thus we must have that $\# \{\lambda \in \sigma_p(T) \:|\: |\lambda |\geq N \} < \infty$.

##### 4. 
Let $\lambda \in \sigma_p(T)\setminus \{0\}$. Let $K : = \ker(\lambda I -T) \subseteq X$ which is a *closed subspace*. Therefore $K$ is a Banach space.
The closed unit ball in $K$ is:
$$\begin{align*}
\{x \in K \:|\: \|x\| \leq 1\} &= \{x \in K \:|\: Tx = \lambda x, \|x\|\leq 1\} \\
&= \{\lambda^{-1}Tx \:|\: \|x\| \leq 1 \} \\
&\subseteq \lambda^{-1} \overline{T(\overline{B}(0,1))}.
\end{align*}$$
which is compact since $T$ is compact. So $\dim K < \infty$ (its closed unit ball is compact).

##### 2. 
We need to show that if $\lambda \neq 0$, then $\lambda I -T$ is injective $\iff$ $\lambda I -T$ is surjective.

>[!Lemma]
>$X$ a Banach space, and $T \in \mathcal{L}(X)$ compact.  If $\lambda \neq 0$, then $\text{im }(\lambda I -T)$ is closed.
###### Proof
Suppose $(\lambda I - T)x_n \to y$. We need to show that $y \in \text{im }(\lambda I-T)$.
Let $K = \ker \lambda I -T$. For $x \in X$ let $\text{dist}(x,K):= \inf_{z \in K} \|x-z\|$.
By definition of infimum, there is $(z_n) \subseteq K$ with $\|x_n - z_n\| \leq 2\: \text{dist}(x_n, K)$.

>[!Claim]
>$(x_n-z_n)_{n\geq1}$ is a bounded sequence.
###### Proof
Suppose it is not bounded. Then we can assume that $\|x_n-z_n\| > n$ for all $n \geq 1$. 
Let $v_n = \frac{x_n-z_n}{\|x_n-z_n\|}$.

We will show that $(v_n)_{n\geq1}$ has convergent subsequence $v_{n_k}\to v$.
To see this, since $(v_n)_{n\geq1}$ is bounded and $T$ is compact, there is $(v_{n_k})_{k\geq1}$ so that $Tv_{n_k} \to w$. Then
$$(\lambda I-T)v_{n_k} = \frac{(\lambda I -T)(x_{n_k}-z_{n_k})}{\| x_{n_k} - z_{n_k}\|} \tag{$z_{n_k} \in K$} \longrightarrow 0$$
since the denominator $\to \infty$. 
So $\lambda v_{n_k} = (\lambda I - T)v_{n_k} + Tv_{n_k}\to 0 +w$. Thus $v_{n_k} \to v := \frac{1}{\lambda}w$  $(\lambda \neq 0)$.

Note that $v \in K$, because $w = \lambda v \longleftarrow Tv_{n_k} \longrightarrow Tv$. Hence $Tv = \lambda v$. So $v \in K$.

Let $u_{n_k} = z_{n_k} + \|x_{n_k} - z_{n_k}\|v \in K$ from above. Then
$$\begin{align*}
\text{dist}(x_{n_k}, K) &\leq \|x_{n_k} - u_{n_k}\| \\[2pt]
&= \|x_{n_k} - z_{n_k} - \|x_{n_k} - z_{n_k}\|v \| \\[2pt]
&= \|\|x_{n_k}- z_{n_k}\|v_{n_k} - \|x_{n_k} - z_{n_k}\|v\| \tag{by def. of $v_n$}\\[2pt]
&= \|x_{n_k}-z_{n_k}\| \|v_{n_k}-v\|\\[3pt]
&\leq 2\text{dist}(x_{n_k},K) \|v_{n_k}-v\|
\end{align*}$$
since $n < \|x_n-z_n\| \leq 2 \text{dist}(x_n,K)$.
$\text{dist}(x_{n_k},K)\neq 0$, hence dividing gives $\|v_{n_k}-v\|\geq \frac{1}{2}$, contradicting $v_{n_k} \to v$. $\square$


So we showed that there is a subsequence $(x_{n_k} - z_{n_k})_{k \geq 1}$ for which $T(x_{n_k}-z_{n_k})$ converges. Then
$$\begin{align*}
\lambda(x_{n_k}-z_{n_k}) &= (\lambda I -T)(x_{n_k}-z_{n_k}) + T(x_{n_k}-z_{n_k}) \\
&= \underbrace{(\lambda I-T) x_{n_k}}_{\text{converges to $y$ by assumption}} \:+\: \underbrace{T(x_{n_k}-z_{n_k})}_{\text{converges}} \\
\to \lambda x
\end{align*}$$
So $x_{n_k} - z_{n_k} \to x$. Then 
$$y \longleftarrow (\lambda I -T)x_{n_k} = (\lambda I -T)(x_{n_k}-z_{n_k}) \overset{\text{continuity}}{\longrightarrow} (\lambda I-T)x$$
So $y = (\lambda I - T)x$, so $y \in \text{im }(\lambda I -T)$ as required 
$\square$
(END OF PROOF OF LEMMA)



If $\lambda \in \sigma(T) \setminus \{0\}$ is not an eigenvalue, then $\lambda I -T$ is injective but *not* surjective.
Let $Y_n = \text{im }(\lambda I -T)^n$. 
Since $\lambda I - T$ is injective, we have 
$$Y_1 \supsetneq Y_2 \supsetneq Y_3 \supsetneq \cdots$$
and by the lemma, each $Y_n$ is closed.
Using Riesz's lemma, pick $y_n \in Y_n$ with $\|y_n\|=1$ and $\|y_n-y\|\geq \frac{1}{2}$ for all $y \in Y_{n+1}$.

>[!Claim] 
>$(Ty_n)_{n\geq 1}$ has no convergent subsequence, and hence $T$ is not compact.
###### Proof
For $m >n$ 
$$\begin{align*}
\|Ty_n - Ty_m\| &= \|\underbrace{(\lambda I - T)y_n - (\lambda I -T)y_m +\lambda y_m}_{\in Y_{n+1}} - \lambda y_n\| \\
&= |\lambda| \|y_n - (\text{something in } Y_{n+1})\| \\
&\geq \frac{|\lambda|}{2}
\end{align*}$$
So there is no convergent subsequence. $\square$

Thus since $T$ is not compact otherwise, we need $\lambda I -T$ to be injective and surjective. $\square$