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
2. $(\ell^p, \|\cdot\|_p)$ is Banach
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
Let $(f_n)\subset (X,\|\cdot\|_\infty)$ be a Cauchy sequence. i.e. $\forall \varepsilon >0$  there exists $n_0 \in \mathbb{N}$ such that $\forall n,m \geq n_0$, $|f_n(x) - f_m(x)| \leq \|f_n - f_m \|_\infty < \varepsilon$.

If we fix $x \in [a,b]$, $(f_n(x))_{n\geq 1}$ is Cauchy in $\mathbb{K}$ which implies that $\lim_{n \to \infty} f_n(x) =: f(x)$. 

We can show this by noting that if $(f_n) \subset C([a,b])$ converges uniformly to $f$, then $f \in C([a,b])$.
$\forall \varepsilon > 0$, $\exists n_0 \in \mathbb{N}$ such that for $n,m \geq n_0$, $|f_n - f_m| \leq \| f_n - f\|_\infty < \varepsilon$ for all $x \in C([a,b])$. This implies that $$|f_n(x)- f(x)| \leq |f_n(x) - f_m(x)| + |f_m(x)- f_n(x)| < 2\varepsilon$$ as $n \to \infty$, then by lemma $f \in C([a,b])$.   $\square$

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
![[desmos-graph (1).png|400]]

For $m>n$, $\|f_n - f_m\|_\infty \geq |f_n(y_n) - f_m(y_n)| = |1-0| = 1$.
Hence $f_n$ is not a Cauchy sequence and in a metric space every convergent sequence is indeed Cauchy. Hence there is no convergent subsequence. Therefore $\bar{B}(0,1)$ is not compact.  $\square$

