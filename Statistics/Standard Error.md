
>[!info] Definition
>The **standard deviation** of an $L^2$-RV $X$ is 
>$$\sigma_X = \sqrt{V(X)}$$
>
>The **standard error** of an estimator $\hat{\Theta}$ is its standard deviation
>$$\sigma_{\hat{\Theta}} = \sqrt{V(\hat{\Theta})}$$


# Examples

## Bernoulli

For $\text{Bernoulli}(\theta)$ the estimator $\hat{\Theta} = \bar{\mathbf{X}}$ 
$$\sigma_{\hat{\Theta}}= \sqrt{V(\hat{\Theta})} = \sqrt{\frac{\theta(1-\theta)}{n}}$$
- We often discuss standard error as *estimated standard error* as the theoretical value is not always known.

The estimated standard error is
$$\widehat{\sigma}_{\hat{\Theta}} = \sqrt{\frac{\bar{\mathbf{x}}(1-\bar{\mathbf{x}})}{n}}$$

## Poisson
$$\sigma_{\hat{\Theta}} = \sqrt{V(\hat{\Theta})} = \sqrt{\frac{\theta}{n}}$$
and the estimated standard error is 
$$\widehat{\sigma}_{\hat{\Theta}} = \sqrt{\frac{\bar{\mathbf{x}}}{n}}$$