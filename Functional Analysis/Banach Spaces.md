# Motivation

>[!example]
>$(C([a,b]), \|\cdot\|_\infty)$ and $(C([a,b]), \|\cdot\|_\infty)_p$  for $1\leq p < \infty$ are not the same
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
3. $(C, \|\cdot \|_p)$ is Banach for $C = \{(x_n) \in \ell \:|\: \lim_{n\to \infty} x_n \text{ exists}\}$
4. *Non-example:* (Polynomials on $[a,b]$, $\|\cdot\|_\infty$) is NOT complete and hence not Banach


# Theorems

## $\ell^p$ and $\ell^\infty$

>[!theorem] 
>let $X = C([a,b])$ vector space over $\mathbb{K}$.
>1. $(X, \| \cdot \|_\infty)$ is Banach
>2. $(X, \|\cdot \|_p)$ for $1 \leq p < \infty$ is NOT complete

##### Proof
###### 1.
Let $(f_n)\subset (X,\|\cdot\|_\infty)$ be a Cauchy sequence. 
Therefore $\forall \varepsilon >0$  there exists $n_0 \in \mathbb{N}$ such that $\forall n,m \geq n_0$, $|f_n(x) - f_m(x)| = |\|f_n - f_m \| < \varepsilon$.
If we fix $f(x) \in [a,b]$, $(f_n(x))_{n\geq 1}$ is Cauchy in $\mathbb{K}$ which implies that $\lim_{n \to \infty} f_n(x) = f(x)$. 

We can show this by noting that if $(f_n) \subset C([a,b])$ converges uniformly to $f$, then $f \in C([a,b])$.
$\forall \varepsilon > 0$, $\exists n_0 \in \mathbb{N}$ such that for $n,m \geq n_0$, $\| f_n - f\|_\infty < \varepsilon$ for all $x \in C([a,b])$. This implies that $$|f_n(x)- f(x)| \leq |f_n(x) - f_m(x)| + |f_m(x)- f_n(x)| < 2\varepsilon$$ as $n \to \infty$, then by lemma $f \in C([a,b])$.   $\square$

###### 2.
We can rescale and reshape so assume $a=0,b=1$.

Consider 





