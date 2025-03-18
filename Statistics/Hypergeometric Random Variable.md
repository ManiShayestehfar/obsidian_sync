
A **Hypergeometric RV** $X$ models the number of red balls in a sample of $m$ balls drawn *without replacement* from a box of $r$ red balls and $n-r$ black balls.



- 3-parameter family $(r,n,m)$

- RV $X(\Omega) \subset \{0,1,...,\min\{r,m\}\}$ where all samples of size $m$ are equally likely

- $|\Omega| = \begin{pmatrix}n \\ m \end{pmatrix}$ 
- For $k \in \{0,1,...,\min\{r,m\}\}$ there are $\begin{pmatrix}r \\ k \end{pmatrix}$ ways to choose $k$ red balls out of $r$
- For each choice of $k$ red balls, there are $\begin{pmatrix}n-r \\ m-k \end{pmatrix}$ ways to choose black balls.
$$\implies P(X=k) = \frac{\begin{pmatrix}r \\ k \end{pmatrix} \begin{pmatrix}n-r \\ m-k \end{pmatrix}}{ \begin{pmatrix}n \\ m \end{pmatrix}}$$

### Example: Convicted Twins

![[convicted_twins.png|450]]

> *Is there evidence of a genetic link, or is the sibling more likely to be convicted if their convicted twin is identical?*

- 13 red balls (monozygotic twins)
- 17 black balls (dizygotic twins)
- We randomly sample 12 balls

$X \sim HG(r=13, n=30,m=12)$

$$\begin{align*} P(X \geq 10) &= \sum_{k=10}^{12} P(X=k) \\[6pt] &= \sum_{k=10}^{12} \frac{\begin{pmatrix}13 \\ k \end{pmatrix} \begin{pmatrix}17 \\ 12-k \end{pmatrix}}{ \begin{pmatrix}30 \\ 12 \end{pmatrix}} \\ &\approx 0.000465\\ \end{align*}$$


# Expectation and Variance of Hypergeometric

Let $X = \#$ of red balls in a sample of $m$ balls from an urn with $r$ red balls and $n-r$ black balls. 
- $X \sim \text{Hyper}(r,n,m)$

For $i=1,2,...,m\leq n$, let$X_i = 1_{\text{ith drawn ball is red}}$, otherwise $0$.
- This is a  $X_i \sim \text{Bernoulli}(p)$ where

![[Pasted image 20250312225737.png|600]]

Clearly $X = \sum_{i=1}^n X_i$. 
- Note that $X_i$'s are not *independent*. Taking a ball out affects the odds of the next ball drawn.
$$E(X) = \sum_{i=1}^m E(X_i) = m\frac{r}{n}$$
$$V(X) = \sum_{i=1}^{n}V(X_i) + \sum_{i\neq j}\text{Cov}(X_i,X_j)$$
where 
$$\begin{align*}
V(X_i) &= p(1-p) \\[7pt]
&= \frac{r}{n}\left(1- \frac{r}{n}\right)
\end{align*}$$
Notice then that 
$$\text{Cov}(X_i,X_j) = E(X_iX_j) - E(X_i)E(X_j) = E(X_iX_j) - (r/n)^2$$
where
$$\begin{align*}
E(X_iX_j) &= 1 \cdot P(X_i=1, X_j=1) \\[5pt]
  &= \frac{\binom{r}{2}}{\binom{n}{2}} = \frac{r(r-1)}{n(n-1)} 
\end{align*}$$

Hence
![[Screenshot 2025-03-19 at 9.30.30 am.png|700]]
*Answer:* Yes as $\text{Cov} < \text{Var}$, and that the variables are negatively correlated.


Finally 
$$\text{Var}(X) =  m\frac{r}{n} \left(1 - \frac{r}{n}\right)\left(1-\frac{m-1}{n-1}\right)$$


# Comparison with Sampling with Replacement

>[!note]
>If the balls are drawn ***with*** replacement, then the RV is described as 
>$$Y \sim \text{Binomial}\left(m,p=\frac{r}{n}\right)$$
>

so $$E(Y) = m\frac{r}{n}.$$
Let $X \sim \text{Hyper}(r,n,m)$. Then 
$$V(Y) = m\frac{r}{n}\left(1-\frac{r}{n}\right) \geq V(X)$$
with equality when $m=1$.

For $m$ fixed and $n \to \infty$  such that $\frac{r_n}{n}\to p$, then
$$V(X_n) =  m\frac{r_n}{n} \left(1 - \frac{r_n}{n}\right)\left(1-\frac{m-1}{n-1}\right) \to mp(1-p)$$
and 
$$V(Y_n) = m\frac{r_n}{n} \left(1 - \frac{r_n}{n}\right) \to mp(1-p)$$



