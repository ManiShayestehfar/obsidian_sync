**Idea:** Given a sample $x_1,...,x_n$ from a distribution with pmf $f_\theta(x)$, we want to estimate $\theta$.

>[!info] Definition
>The **likelihood function** gives the probability of the observed sample, *assuming* the sample was generated using $f_\theta$, where $\theta$ is known:
>$$L(\theta) := P_\theta(X_1=x_1,...,X_n=x_n)$$
>
>-> $L(\theta)$ is NOT the probability of $\theta$. 
>

- When the sample is modeled as *iid*
$$L(\theta) = \prod_1^n f_\theta(x_i)$$

# Examples

## Bernoulli
$X_i \sim \text{Bernoulli}(\theta)$, and $f_\theta(x) =  \begin{cases} 1- \theta & x=0  \\ \theta & x=1 \\ 0 & \text{otherwise}\end{cases}$ . 

- Simplify $f_\theta(x)$ pmf as
	$$f_\theta(x) = \theta^x(1-\theta)^{1-x} \cdot \mathbf{1}_{\{0,1\}(x)}$$
Then 
$$\begin{align*}
L(\theta) &= \prod_{i=1}^n \theta^{x_i}(1-\theta)^{1-x_i} \\[6pt]
&= \theta^{\sum x_i} (1-\theta)^{\sum (1-x_i)} \\[6pt]
&= \theta^{\sum x_i} (1-\theta)^{n-\sum x_i}
\end{align*}$$
![[Pasted image 20250322133319.png]]

The MLE is defined as the value of $\theta$ that maximises $L(\theta)$, or
$$\hat{\theta}:= \text{argmax}_\theta L(\theta)$$
- $\log$ is a monotonic increasing function with *log likelihood function* defined
$$\ell(\theta) := \log L(\theta) = \sum_1^n \log f_\theta(x_i)$$
and $\hat{\theta}:= \text{argmax}_\theta \:\:\ell(\theta)$.



Let $s = \sum_1^n x_i \in [0,n]$. Then
$$\ell(\theta) = s \cdot \log \theta + (n-s)\log(1-\theta)$$

**How to maximise $\ell(\theta)$?** Differentiate $\ell(\theta)$
 
![[Screenshot 2025-03-22 134100.png]]

![[Pasted image 20250322134526.png|600]]


- Therefore $\theta = \mathbf{\hat{x}} = s/n$ is a unique critical point in $(0,1)$ and it is a global maximum in $(0,1)$
- Still need that $\theta \in \{0,1\}$, but for $\mathbf{\hat{x}} \in (0,1) \iff s,n-s > 0$ so the maximum cannot be attained for $\theta \in \{0,1\}$  

Therefore for all cases the MLE is $\hat{\theta} = \mathbf{\bar{x}}$ .

- Now for $s \in [0,N]$ for $N>0$
$$\text{argmax}_{\theta\in[0,1]}\:\: s\log \theta + (N-s)\log(1-\theta) = \text{argmax}_{\theta \in [0,1]} \:\:\theta^s(1-\theta)^{N-s} = \frac{1}{N}s$$

## Poisson
$X_i \sim \text{Poisson}(\lambda)$ 

$$\begin{align*}
\ell(\lambda) &= \sum_{i=1}^n \log \left(e^{-\lambda} \frac{\lambda^{x_i}}{x_i!} \right) \\
&= -n\lambda +\left(\sum_{i=1}^n x_i\right)\log\lambda - \sum_{i=1}^n\log(x_i!) 
\end{align*}$$
![[Screenshot 2025-03-22 141232.png]]

so for $\mathbf{\bar{x}}> 0, \lambda =\mathbf{\bar{x}}$ is a unique critical point of $\ell$ and a global maximum for $\lambda >0$

- Still need to check $\lambda = 0$, but $\mathbf{\bar{x}} > 0 \iff \sum_{i=1}^n x_i >0$ so the maximum cannot be attained for $\lambda = 0$. 

Therefore $\lambda =\mathbf{\bar{x}}$ is always the MLE

## Binomial$(m,p)$, $m$ is known
$X_i \text{Binomial}(m,p)$ where $m$ is known but $p$ is not.

$$\begin{align*}
L(p) &= \prod_{i=1}^n \binom{m}{x_i}p^{x_i}(1-p)^{m-x_i}\\[7pt]
&= p^{\sum x_i} (1-p)^{mn - \sum {x_i}} \prod_1^n \binom{m}{x_i}
\end{align*}$$

- Let $N = mn$ (total number of iid Bernoulli trials) and $s = \sum_{i=1}^n x_i$. Then $s \in [0,N]$ and 
	$$L(p) = \text{constant}(m;x_1,...,x_n) \cdot p^s(1-p)^{N-s}$$

Ignoring the constant, $L(p)$ is similar to the Bernoulli case, and so the MLE is 

$$\hat{p} = \frac{1}{N}s = \frac{1}{N}\sum_{i=1}^n x_i = \frac{1}{m n}\sum_{i=1}^n x_i = \frac{\mathbf{\bar{x}}}{m}$$
## Binomial$(m,p)$

![[Pasted image 20250322143801.png]]
and $\tilde{m}\tilde{p} = \mathbf{\bar{x}}$ 

- If $m$ is known the the MLE is similar to previous case as $\hat{p} =\frac{\mathbf{\bar{x}}}{m}$. 

Generally if
$$\ell(p,m) = \sum_{i=1}^n \log \left[\binom{m}{x_i} p^{x_i}(1-p)^{m-x_i}\right]$$
then 
$$\text{argmax}_{p} \:\:\ell(p,m) = \frac{\mathbf{\bar{x}}}{m} =: \hat{p}(m)$$ for fixed $m$.

Hence if $\max_{p,m} \ell(p,m)$ exists then 
![[Pasted image 20250322144158.png]]
(no closed form solution)

Instead for each value $m = \max\{x_i\},  \max\{x_i\}+1,  \max\{x_i\}+2,...$ 
where in reality there is no upper bound to $m$.

So we can only compute an *approximate* MLE.



# Continuous RV

The only difference here is that the pdf which is the continuous analogy to the pmf gives $P_\theta(X=x) = 0$ so instead we use
$$\ell(\theta;x) = \log f_{X,\theta}(x) \overset{i.i.d}{=} \sum_j \log f_{X,\theta}(x_j)$$

## Example

### Normal

$x_1,...,x_n$ drawn from $N(\theta,1);\:\:f_\theta(X) = \frac{1}{\sqrt{2\pi}} e^{-(x-\theta)^2/2}$ 
$$\ell(\theta;x) = \sum_{j=1}^n \left[ \log \frac{1}{\sqrt{2\pi}} + \left(-\frac{(x_j-\theta)^2}{2}\right)\right]$$
![[Maximum Likelihood Estimation-1747441034749.png|600]]
