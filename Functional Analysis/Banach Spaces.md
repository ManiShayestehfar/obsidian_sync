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
By the Cauchy property of $(f_n)$, we showed that $\|f_n-f_m\| < \varepsilon$. Fix $x \in [a,b]$. Since $|f_n(x)-f_m(x)|< \varepsilon$, then taking $m \to \infty$ (which we can do since the absolute value is continuous), then $|f_n(x) - f(x)| \leq \varepsilon$. Since the choice of $x$ was arbitrary, then $\|f_n-f\|\leq \varepsilon$. Thus $f_n \to f$ uniformly on $[a,b]$.

Now fix $x_0 \in [a,b]$ and let $\varepsilon >0$. Choose $n$ large enough such that $\|f_n - f\|< \varepsilon/3$. Since $f_n$ is continuous at $x_0$, then we can choose $\delta >0$ such that $|x-x_0|<\delta \implies |f(x) - f(x_0)|< \varepsilon/3$. Hence
$$|f(x) - f(x_0)|\leq |f(x) - f_n(x)| + |f_n(x) - f_n(x_0)| + |f_n(x_0) - f(x_0)| \leq \varepsilon$$
The first and last term follow from uniform convergence, and the middle term as per above.
So $f$ is continuous at $x_0$, and since $x_0$ was arbitrary, then $f \in C[a,b]$.  $\square$


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

