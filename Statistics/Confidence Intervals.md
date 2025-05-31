
# Context
[[Estimation|Estimation:]] Given a sample $x_1,...,x_n \sim F_\theta$ find $\theta$. For example, $X_i \sim N(\theta,1)\implies \hat{\Theta} = \bar{X}$ (MLE moments). But *how close are we to $\theta$?*   
$$\begin{align*}
\sum_{i=1}^n X_i &\sim N(n\theta, n) \\[2pt]
\implies \quad \hat{\Theta} = \bar{X} &\sim N\left(\theta,\frac{1}{n}\right)
\end{align*}$$
and in particular, $P_{\theta_p = \theta}(\hat{\Theta}= \theta)=0$ as $\hat{\Theta}$ has a continuous distribution.

- One way to measure how well the estimator is doing is the MSE. However, MSE depends on $\theta$ and it's not easy to interpret beyond comparing estimators or studying asymptotic properties.
- We cannot know how well the estimator $\hat{\Theta}$ is doing on any given sample, however, it would be useful to give a bound on the probability that $\hat{\Theta}$ deviates significantly from $\theta$ for a *randomly drawn* sample.

# Example
## General
$$\begin{align*}
P_{\theta_p=\theta} (|\hat{\Theta} - \theta| \geq \varepsilon) &= P(|\hat{\Theta} - \theta|^2 \geq \varepsilon^2) \\[4pt]
&\leq \frac{E_{\theta_p=\theta}(\hat{\Theta} - \theta)^2}{\varepsilon^2} \\[4pt]
&= \frac{MSE(\hat{\Theta})}{\varepsilon^2}
\end{align*}$$
If a sample is from $N(\theta,1)$, then
$$\begin{align*}
P_{\theta_p=\theta}(|\hat{\Theta}-\theta| \geq \varepsilon) &\leq \frac{V_{\theta_p=\theta}(\hat{\Theta})}{\varepsilon^2} \\[3pt]
&= \frac{1}{n\varepsilon^2}
\end{align*}$$

![[Confidence Intervals-1748610926070.png|650]]

>[!info]
>That is, the **random interval** $(\bar{X}-\varepsilon,\bar{X}+\varepsilon)$ contains the *unknown* value at $\theta_p$ with probability $\geq 1 - \frac{1}{n\varepsilon^2}$.
>
>We say that $(\bar{X}-\varepsilon,\bar{X}+\varepsilon)$ is a $100\times (1-\frac{1}{n\varepsilon^2})\%$ **confidence interval** for $\theta_p$.  

>[!warning]
>![[Confidence Intervals-1748611162909.png|600]]
>![[Confidence Intervals-1748611197319.png|600]]


**How can we improve the CI in our example?**

![[Confidence Intervals-1748611402359.png|600]]

![[Confidence Intervals-1748611729897.png|600]]


# Definition

>[!info] Definition
>An interval-valued function 
>$$I_\alpha^{(n)} : \mathbb{R}^n \to \{[a,b] : a<b\}\quad \alpha \in (0,1)$$
>defined a $100(a-\alpha)\%$ **confidence interval** for $\theta_p$ if $\forall \theta$ and $X_1,...,X_n$ ind. $F_{\theta_p = \theta}$-distributed RVs
>$$P_{\theta_p=\theta}(\theta\in I^{(n)}_\alpha(X_1,...,X_n)) \geq 1 - \alpha$$
>Equivalently, $P_{\theta_p=\theta}(\theta\not\in I^{(n)}_\alpha(X_1,...,X_n)) \leq  \alpha$.
>

We can get problems in two types
1. Verify a given interval-valued function $I_\alpha$ is a valid CI
2. Construct an appropriate $I_\alpha$

## Example for (1)

![[Confidence Intervals-1748612855300.png|650]]

>[!tip] Claim
>$I_\alpha(X_1,...,X_n)$ is a $(1-\alpha)\cdot100\%$ CI for $\theta$
##### Proof

![[Confidence Intervals-1748613084927.png|650]]