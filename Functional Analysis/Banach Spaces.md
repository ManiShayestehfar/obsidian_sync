# Motivation

>[!example]
>$(C([a,b]), \|\cdot\|_\infty)$ and $(C([a,b]), \|\cdot\|_p)$  for $1\leq p < \infty$ are not the same
##### Proof
Need to show there exists $(f_n) \in C([0,1])$ such that:
1. $f_n \to 0$ with $\|\cdot\|_1$
2. $f_n \not\to 0 \in \|\cdot\|_\infty$ 

Consider this example
![[Screenshot 2026-03-02 at 11.32.13 am.png|250]]

$\|f_n - 0 \|_1 = \int_{0}^1 |f_n(x)|dx = \text{Area of } \Delta = \frac{1}{n} \to 0$.
But $\|f_n-0 \|_\infty = \|f_n\|_\infty = 1 \neq 0$ 


# Definition

>[!definition] Banach Space
>A metric space $(X,d)$ is a **Banach Space** if it is *normed* and *complete*.

- A *normed vector space* is Banach if $d(x,y) := \|x-y\|$ is complete
## Examples

1. $(\mathbb{K}, \|\cdot\|)$ is complete $\implies$ It is Banach
2. $(\ell^p, \|\cdot\|_p)$ is Banach for $1 \leq p \leq \infty$
3. $(c, \|\cdot \|_p)$ is Banach for $c = \{(x_n) \in \ell \:|\: \lim_{n\to \infty} x_n \text{ exists}\}$
4. *Non-example:* (Polynomials on $[a,b]$, $\|\cdot\|_\infty$) is NOT complete and hence not Banach


# Theorems

## $\ell^p$ and $\ell^\infty$

>[!theorem] 
>let $X = C([a,b])$ vector space over $\mathbb{K}$.
>1. $(X, \| \cdot \|_\infty)$ is Banach
>2. $(X, \|\cdot \|_p)$ for $1 \leq p < \infty$ is NOT complete

##### Proof

###### 1.
Let $(f_n)$ be a Cauchy sequence in $(X,\|\cdot\|_\infty)$. We need to show that $(f_n)$ converges in $\|\cdot\|_\infty$ to some function $f\in X$.  


Since $(f_n)$ is Cauchy in $\|\cdot\|_\infty$, for every $\varepsilon>0$, there exists $N\in\mathbb N$ such that for all $n,m\geq N$,  $\|f_n-f_m\|_\infty<\varepsilon$.  
Hence, for every $x\in[a,b]$ and all $n,m\geq N$,  $|f_n(x)-f_m(x)|\leq \|f_n-f_m\|_\infty<\varepsilon.$  
Therefore, for each fixed $x\in[a,b]$, the sequence $(f_n(x))$ is Cauchy in $\mathbb K$. Since $\mathbb K$ is complete, there exists a value $f(x)\in\mathbb K$ such that $f_n(x)\to f(x)$.  

Thus we may define $f:[a,b]\to\mathbb K$ by $f(x):=\lim_{n\to\infty} f_n(x)$.  

  
We now show that $f_n\to f$ uniformly. Fix $\varepsilon>0$. Since $(f_n)$ is Cauchy in $\|\cdot\|_\infty$, there exists $N\in\mathbb N$ such that for all $n,m\geq N$, $\|f_n-f_m\|_\infty<\varepsilon$.  
Fix $n\geq N$ and $x\in[a,b]$. Since $f_m(x)\to f(x)$ as $m\to\infty$, and since the absolute value is continuous, we may let $m\to\infty$ in $|f_n(x)-f_m(x)|<\varepsilon$ to obtain $|f_n(x)-f(x)|\leq \varepsilon.$  
Since this holds for *every* $x\in[a,b]$, we get $\|f_n-f\|_\infty\leq \varepsilon$ for all $n\geq N$. Hence $f_n\to f$ *uniformly* on $[a,b]$.  


It remains to prove that $f\in C([a,b])$. Let $x_0\in[a,b]$ and let $\varepsilon>0$. Since $f_n\to f$ uniformly, choose $n\in\mathbb N$ such that $\|f_n-f\|_\infty<\varepsilon/3$.  
Since $f_n$ is continuous at $x_0$, there exists $\delta>0$ such that if $x\in[a,b]$ and $|x-x_0|<\delta$, then $|f_n(x)-f_n(x_0)|<\varepsilon/3$. Therefore, whenever $x\in[a,b]$ and $|x-x_0|<\delta$,  
$$  
|f(x)-f(x_0)|  
\leq  
|f(x)-f_n(x)|  
+  
|f_n(x)-f_n(x_0)|  
+  
|f_n(x_0)-f(x_0)|  
<  
\varepsilon.  
$$
Hence $f$ is continuous at $x_0$. Since $x_0\in[a,b]$ was arbitrary, $f\in C([a,b])$.  
  
Therefore every Cauchy sequence in $(X,\|\cdot\|_\infty)$ converges to an element of $X$. Hence $(X,\|\cdot\|_\infty)$ is Banach. $\square$



###### 2.
We can rescale and reshape so assume $a=0,b=1$.
Consider the graph of $f_n$

![[desmos-graph.png|300]]

where $$\|f_n\|_p = \left(\int_0^1 |f_n(x)|^p\:dx\right)^{1/p} \leq 1$$
>[!claim]
$(f_n) \subset (X, \|\cdot\|_p)$ is Cauchy.

**Proof:** 
$\|f_m-f_n\|_p \leq \|g_n\|_p$ for $m>n$ where $g_n$ is defined as the graph of $f_m-f_n$.
So $|f_m(x) - f_n(x)| \leq |g_n(x)| = \left(\int_{1/2}^{1/2+1/n} 1^p\: dx \right)^{1/p} = 1/n^{1/p} \to 0$ as $n \to \infty$. 
So $(f_n)$ is indeed Cauchy. $\square$

>[!Claim]
>$(f_n)$ does not have a limit in $C([a,b])$

**Proof:**
Assume by contradiction that it does have a limit. Then $\|f_n-f\|_p \to 0$ as $n \to \infty$. Then
$$\begin{align*}
0\longleftarrow \int_{0}^1|f_n(x) - f(x)|^p\:dx &\geq \int_0^{1/2}|f_n(x)-f(x)|^p\:dx \\
&= \int_{0}^{1/2}|1 - f(x)|^p\:dx
\end{align*}$$
So $f(x) = 1$ for $x \in [0,1/2]$. Similarly $f(x)=0$ for $x \in [1/2,1]$. But such $f$ is not continuous. So this is a contradiction. $\square$





## Banach $\not \Rightarrow$ Compact

$\bar{B}(0,1) = \{f \in C([0,1]) \:|\: \|f\|_\infty < 1\}$ is a Banach space.
We show that it is NOT compact.

We show that for the following graph of sequence $(f_n)$ there is not convergent subsequence.


For $m>n$, $\|f_n - f_m\|_\infty \geq |f_n(y_n) - f_m(y_n)| = |1-0| = 1$.
Hence $f_n$ is not a Cauchy sequence and in a metric space every convergent sequence is indeed Cauchy. Hence there is no convergent subsequence. Therefore $\bar{B}(0,1)$ is not compact.  $\square$


## Banach $\nRightarrow$ Compact

Let $X:=C([0,1])$ with $\|f\|_\infty:=\sup_{x\in[0,1]} |f(x)|$.
Since $C([0,1])$ is complete with respect to $\|\cdot\|_\infty$, it is a Banach space.
We show that the closed unit ball $\overline B(0,1):=\{f\in C([0,1]):\|f\|_\infty\leq 1\}$ is not compact.


For each $n\in\mathbb N$, define $f_n\in C([0,1])$ to be the triangular function supported on $\left[\frac{1}{n+1},\frac{1}{n}\right]$, with peak value $1$ at some point $y_n\in\left(\frac{1}{n+1},\frac{1}{n}\right)$. In particular, $\|f_n\|_\infty=1$, so $f_n\in\overline B(0,1)$ for every $n\in\mathbb N$.

![[desmos-graph (1).png|400]]

>[!Claim ]
 $(f_n)$ has no convergent subsequence in $\overline B(0,1)$.

Let $(f_{n_k})$ be an arbitrary subsequence of $(f_n)$, where $n_1<n_2<\cdots$. If $j>k$, then $n_j>n_k$, so the support of $f_{n_j}$ lies to the left of the point $y_{n_k}$. Hence $f_{n_j}(y_{n_k})=0$, while $f_{n_k}(y_{n_k})=1$.

Therefore, $\|f_{n_k}-f_{n_j}\|_\infty \geq |f_{n_k}(y_{n_k})-f_{n_j}(y_{n_k})| = |1-0| = 1$.

Thus every subsequence $(f_{n_k})$ fails to be Cauchy. Since every convergent sequence in a metric space is Cauchy, no subsequence of $(f_n)$ can converge.

Therefore $\overline B(0,1)$ contains a sequence with no convergent subsequence. Since compactness implies sequential compactness in metric spaces, $\overline B(0,1)$ is not compact.

Hence being Banach does not imply being compact. $\square$