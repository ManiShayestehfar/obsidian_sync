- Given observations (sample) $x_1,...,x_n$ from a distribution $F(\theta)$, where $\theta$ is an unknown parameter, we want to estimate $\theta$

![[Screenshot 2025-03-19 at 3.10.07 pm.png]]

#### Assumptions
- The sample $x_1,...,x_n$ is a particular realisation of the iid RVs $X_1,...,X_n \sim F(\theta)$
- Each of the sampled values can be a vector. Then the sample $\mathbf{x}_1,\mathbf{x}_2,...,\mathbf{x}_n$ is assumed to be a realisation of the iid random vectors $\mathbf{X}_1,\mathbf{X}_2,...,\mathbf{X}_n$ 
	- For example, there is a sample size $n=1$ from $\text{multinomial}(m;p_1,...,p_r)$ distribution, $\mathbf{x}_1 = (x_1^1,...,x_r^1)$ where $x_i^1$ is the number of times outcome $i$ came up in $m$ trials.


# Comparing Estimators

- To compare estimator meaningfully, we need to consider their performance on all possible samples (and all possible values of the parameters)

- So far we considered: Given a sample $x_1,...,x_n$ from a distribution $F(\theta)$, construct an estimate $\hat{\theta}= \varphi(x_1,...,x_n)$. e.g. $\hat{\theta} = \hat{\mathbf{x}}$

- To consider all possible samples we recall the assumption that the sample $x_1,...,x_n$ is a *particular realisation* of the independent $F(\theta)$-distributed RVs $X_1,...,X_n$, so we define the RV
$$\hat{\Theta} = \varphi(X_1,...,X_n)\tag{estimator}$$

## Assessing an Estimator

- The estimator $\hat{\Theta}$ needs to estimate the unknown $\theta$
- So the error $\hat{\Theta} - \theta$ must be small

### MSE
>[!info] Definition
>The **mean square error (MSE)** of an estimator $\hat{\Theta}$ is 
>$$MSE(\hat{\Theta}) := E_\theta(\hat{\Theta - \theta})^2$$

>[!tip] Claim 1
>$$MSE(\hat{\Theta}) = V(\hat{\Theta}) + [\:\underbrace{E(\hat{\Theta}) - \theta}_{\text{bias}}\:]^2$$
##### Proof
$$\begin{align*}
E_\theta(\hat{\Theta} - \theta)^2 &= V(\hat{\Theta} - \theta) \:+\: E^2(\hat{\Theta} - \theta) \\[6pt]
&= V(\hat{\Theta}) + [\:E(\hat{\Theta}) - \theta\:]^2
\end{align*}$$ $\square$


>[!info] Definition
>An estimator is called **unbiased** if $E_\theta(\hat{\Theta}) = \theta$ (bias $= 0$).
>
>For unbiased estimator $MSE(\hat{\Theta}) = V(\hat{\Theta})$ 


#### Example: Bernoulli$(\theta)$ Estimator

$X_1,...,X_n$ iid  $\text{Bernoulli}(\theta)$ RVs

Recall that the MLE and MoM estimator is
$$\hat{\Theta} = \hat{\Theta}_n = \frac{1}{n}\sum_{i=1}^n X_i$$

**Is it biased?**
$$\begin{align*}
E(\hat{\Theta}) &= E\left(\frac{1}{n}\sum_{i=1}^nX_i\right)\\[6pt]
&= \frac{1}{n}\sum_{i=1}^n E(X_i) \\[6pt]
&= E(X_i) = \theta

\end{align*}$$
