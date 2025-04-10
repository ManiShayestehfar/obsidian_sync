
# Motivating Example

![[Pasted image 20250406144307.png]]

- Which estimator is better? This is difficult to answer analytically
- **Numerically?** Possible yet still difficult but if we know $(m,p)$, how can we estimate bias, variance, MSE of $(\hat{M}_n, \hat{P}_n)$?

- **Bias:** $E(\hat{M}) - m$ 
- Assume we know $\mathbf{\theta} = (m,p)$. How to estimate $E(\hat{M})$

-> Draw a large sample $N$ from the distribution of $\hat{M}$ and average those

**Procedure:**
1. Draw $N$ samples of size $n$ from a $\text{Binomial}(n,p)$ distribution
	$$\mathbf{x}^i = (x_1^i,...,x_n^i)\quad\quad i=1,...,N$$
2. For each, compute $\hat{m}^i = \hat{m}(\mathbf{x}^i)$ and $\hat{p}^i = \hat{p}(\mathbf{x}^i)$
3. Empirically estimate the bias, variance, MSE from the sample $\{(\hat{m}^i, \hat{p}^i)\: : \: i=1,2,...,N \}$
	![[Pasted image 20250406155839.png]]

- Realistically we don't know $\Theta = (m,p)$ though

- Similar to the case in a [[Estimation|previous example of Bernoulli]] with $\hat{\theta} = \hat{\mathbf{x}}$
	$$MSE(\hat{\Theta}_n) = \frac{\theta(1-\theta)}{n}$$
	but $\theta$ is unknown so we estimate it instead
	$$\widehat{MSE}(\hat{\Theta}_n)= \frac{\hat{\theta}(1-\hat{\theta})}{n} = \frac{\hat{\mathbf{x}}(1-\hat{\mathbf{x}})}{n}$$

# Main Definition

>[!info] Definition
>In **parametric bootstrapping**, we execute Monte Carlo simulations above, with $\mathbf{\hat{\theta}} = (\hat{m}, \hat{p})$ instead of $(m,p)$

## Recipe

1. Draw $N$ independent bootstrap samples of size $n$ from distribution $F(\mathbf{\theta} = \hat{\mathbf{\theta}}(x_1,...,x_n))$:
$$\mathbf{x}^{*i} = (x^{*i}_1,...,x^{*i}_n)\quad\quad i = 1,...,N$$
2. For each, compute the estimate $\hat{\mathbf{\theta}}^{*i} = \hat{\mathbf{\theta}}(\mathbf{x}^{*i})$
3. Empirically estimate the bias, variance, or MSE from the samples $\{\mathbf{\hat{\theta}}^{*i}\: : \: i=1,...,N\}$
	![[Pasted image 20250406160838.png]]


# Hardy-Weinberg Equilibrium Example

- See [[Hardy-Weinberg Equilibrium Model]] for context
- **Summary:**

![[Pasted image 20250406161000.png|650]]

## Non-Bootstrap Approach

We can estimate the bias of $\tilde{\Theta}$
$$\text{Bias:}\quad\sum_{k=0}^n \sqrt{\frac{k}{n}} \cdot \binom{n}{k} (\tilde{\theta}^2)^k(1-\tilde{\theta}^2)^{n-k} \quad - \quad \tilde{\theta}$$
![[Pasted image 20250406161518.png]]

## Bootstrap Approach

![[Pasted image 20250406161557.png]]