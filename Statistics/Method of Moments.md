# Summary

1. Expressing moments of the distribution in terms of the unknown parameters $\mathbf{\theta} = (\theta_1,...,\theta_r)$
2. Inverting this map to express parameters in terms of moments
$$\begin{align*}
\theta_1 &= f_1(\mu_1,...,\mu_k) \\
\theta_2 &= f_2(\mu_1,...,\mu_k) \\
&\:\:\vdots \\
\theta_r &= f_r(\mu_1,...,\mu_k) \\
\end{align*}$$
	where $k \geq r$ is minimal and $f_i :\mathbb{R}^k \to \mathbb{R}$
3. Plugging the sample moments $\hat{\mu}_k := \frac{1}{n}\sum_i x_i^k$  for the distributional moments:
	$$\hat{\theta}_i = f_i(\hat{\mu}_1,...,\hat{\mu}_k)$$

# Estimate and Estimator

For a particular sample $x_1,...,x_n$ from Bernoulli or Poisson,
$$\mathbf{\bar{x}} = \sum_ix_i \cdot \frac{1}{n}\quad\quad \text{is the \textit{estimate}}$$
but when modelling the sample with iid RVs $X_1,...,X_n$
$$\bar{X} = \sum_iX_i \cdot \frac{1}{n}\quad\quad \text{is the \textit{estimator}\:\:RV}$$


# Estimating $\mu_k$ 

- suppose we have a sample $x_1,...,x_n$ from $\text{Bernoulli}(p)$. We want to estimate $p = E(X_i) = \mu_1$. **How do we do this?**

Sample mean:
$$\hat{\mu}_1= \frac{1}{n}\sum_{i=1}^nx_i = \bar{\mathbf{x}}$$
For $X \in L^k$ we define its **$k$-th moment** as 
$$\mu_k = E(X^k) = \sum_i x_i^k p_X(x_i) \in \mathbb{R}$$

The moments can be estimated from the sample $x_1,...,x_k$ by the *sample moments* defined
$$\hat{\mu}_k= \frac{1}{n}\sum_{i=1}^nx_i^k $$
- Note that the sample moments $\hat{\mu}_k$ are the moments of the *empirical distribution* which is defined by (cumulatively) assigning a probability of $1/n$ to each sample point/observation $x_i$.
- The pmf of the empirical distribution associated with the sample $\{x_i\}^n_1$ is
 ![[Screenshot 2025-03-19 at 3.37.19 pm.png|700]]
 where $x_{(i)}$ are the ordered sample points or *order statistics* defined by 
 $$\{x_{(i)}\}_1^n = \{x_i\}_1^n\quad \text{and}\quad x_{(1)}\leq x_{(2)}\leq \cdots \leq x_{(n)}$$

>[!warning] Summary of Approach
>In method moments we express the parameter $\theta$ as a function of the moments, which yields an estimate of the parameter by replacing the moments with their estimates: the sample moments


## Examples
### Bernoulli
$X_i \sim \text{Bernoulli}(p)$. 
$$p=\mu_1$$
and therefore
$$\hat{p} = \hat{\mu}_1 = \frac{1}{n}\sum_{i=1}^{^n} x_i = \bar{\mathbf{x}}$$
### Binomial
$X_i \sim \text{Binomial}(m,p)$ where we know $m$ but not $p$. 
$$\mu_1 = E(X_i) = mp \quad\implies\quad p=\frac{\mu_1}{m}$$
So 
$$\hat{p} = \frac{\hat{\mu}_1}{m} = \frac{\bar{\mathbf{x}}}{n}$$

>[!tip] Note
>Given a sample $y_1,..,y_m$ from a $\text{Bernoulli}(p)$ distribution, then the estimated $\hat{p}$ from Binomial agrees with Bernoulli with $x_1 = \sum_1^m y_i$. 
>

### Poisson
$X_i \sim \text{Poisson}(\lambda)$ with $\lambda \geq 0$
$$\mu_1 = E(X_i) = \lambda$$
therefore
$$\hat{\lambda} = \hat{\mu_1} = \bar{\mathbf{x}}$$

### Geometric
$x_i \sim \text{Geometric}(p)$ with $p \in [0,1]$
$$\mu_1 = E(X_i)= \frac{1}{p}\quad\implies\quad p = \frac{1}{\mu_1}$$
Therefore
$$\hat{p} = \frac{1}{\mu_1} = \frac{1}{\bar{\mathbf{x}}}$$

### Binomial with unknown $m,p$
$X_1,...,X_n \sim \text{Binomial}(m,p)$ where both $m,p$ are unknown.

- **Example:** Imagine trying to estimate your competitor’s daily production count (m) and  
failure rate (p) by, say, going through their rejects bin.
$$\mu_1 = E(X_i) = mp$$
$$\mu_2 - \mu^2_1 = \sigma^2 = mp(1-p)$$
Hence, $\sigma^2 = \mu_1(1-p) \implies p = \frac{\mu_1 - \sigma^2}{\mu_1}$, and $m = \frac{\mu_1^2}{\mu_1-\sigma^2}$.  

Let $\mu = \mu_1$, then
$$\begin{align*}
\hat{p} &= \frac{\hat{\mu} - \hat{\sigma}^2}{\hat{\mu}}\\[6pt]
\hat{m} &= \frac{\hat{\mu}^2}{\hat{\mu}- \hat{\sigma}^2}
\end{align*}$$
where $\hat{\mu} = \bar{\mathbf{x}}$, and

![[Screenshot 2025-03-26 at 7.57.59 am.png]]



# Continuous RV

![[Method of Moments-1747439832949.png]]


## Examples

### Normal (1 unknown)

$X_1,...,X_n$ is a sample from $N(\theta,1)$. $\theta = E(X_j) = \mu_1$  $\implies \tilde{\theta} = \tilde{\mu}_1 = \bar{x}$ 


### Normal (all unknown)
$X_1,...,X_n \sim N(\mu, \sigma^2)$. 

$\mu = E(X_j) = \mu_1$,   $\sigma^2 = V(X_j) = \mu_2 - \mu_1^2$

$\implies \tilde{\mu} = \tilde{\mu}_1 = \bar{x}$   and $\tilde{\sigma}^2 = \tilde{\mu}_2 - \tilde{\mu}_1^2 = \tfrac{1}{n}\sum_{j}(x_j-\bar{x})^2$

- Note that $\tfrac{1}{n}\sum_{j}(x_j-\bar{x})^2$ is a bias estimator, so we use $1/(n-1)$ to get the unbiased estimator

### Exponential
$X_1,...,X_n \sim \text{Exp}(\theta)$

$E(X_j) = \frac{1}{\theta}$  $\implies \theta = \frac{1}{\mu_1}$   $\implies \tilde{\theta} = \frac{1}{\bar{x}}$

### Scaled Cauchy
$X_1,...,X_n \sim \theta \cdot X$   where $X \sim \text{Cauchy}$ 

So $E(X_j) = E(\theta \cdot X) = \theta E(X)$ but Cauchy does not have a defined expectation so this dist. has no moments!


