
>[!info] Definition
>The **distribution** of a [[Random Variables| random variable]] $X$, $\mu_x$,is a function defined on *measurable* subsets of $\mathbb{R}$ such that for any *measurable* $A \subset \mathbb{R}$,
>$$\mu_X(A) = P(X \in A).$$ 

# Distributions Summary
## Discrete

| Distribution              | PMF $P(X = k)$                                                                             | Expectation $E[X]$ | Variance $Var(X)$                                                    | Description                                                                                                 |
| ------------------------- | ------------------------------------------------------------------------------------------ | ------------------ | -------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| $\text{Bernoulli}(p)$     | $p^k (1 - p)^{1-k}$<br>$k \in \{0, 1\}$                                                    | $p$                | $p(1 - p)$                                                           | Models a single trial with two outcomes (success or failure).                                               |
| $\text{Binomial}(n,p)$    | $\displaystyle \binom{n}{k} p^k (1 - p)^{n-k}$<br>$k = 0, 1, \ldots, n$                    | $np$               | $np(1 - p)$                                                          | Models the number of successes in $n$ independent Bernoulli trials.                                         |
| $\text{Geometric}(p)$     | $(1 - p)^{k-1} p$<br>$k = 1, 2, \ldots$                                                    | $\frac{1}{p}$      | $\frac{1 - p}{p^2}$                                                  | Models the number of trials until the first success.                                                        |
| $\text{NegBinom}(r,p)$    | $\displaystyle \binom{k-1}{r-1} p^r (1 - p)^{k-r}$<br>$k = r, r+1, \ldots$                 | $\frac{r}{p}$      | $\frac{r(1 - p)}{p^2}$                                               | Generalization of geometric; models trials needed to get $r$ successes.                                     |
| $\text{Poisson}(\lambda)$ | $\displaystyle \frac{e^{-\lambda} \lambda^k}{k!}$<br>$k = 0, 1, 2, \ldots$                 | $\lambda$          | $\lambda$                                                            | Models the number of events in a fixed interval with a known constant rate.                                 |
| $\text{Hyper}(n,r,m)$     | $\displaystyle \frac{\binom{r}{k} \,\binom{n-r}{m-k}}{\binom{n}{m}}$<br>$k = 0, \ldots, n$ | $m \frac{r}{n}$    | $m\frac{r}{n}\left(1-\frac{r}{n}\right)\left(\frac{n-m}{n-1}\right)$ | Models the number of successes without replacement from a finite population of size $N$ with $K$ successes. |
| $\text{Uniform}(a,b)$     | $\displaystyle \frac{1}{b - a + 1}$<br>$k \in \{a, a+1, \dots, b\}$                        | $\frac{a + b}{2}$  | $\frac{(b - a + 1)^2 - 1}{12}$                                       | Models a variable equally likely to take any integer value from $a$ to $b$.                                 |

## Continuous

| Distribution                      | PDF $f(x)$                                                                               | Mean $E[X]$                     | Variance $Var(X)$                                            | Parameters                         | Description                                                                                  |
| --------------------------------- | ---------------------------------------------------------------------------------------- | ------------------------------- | ------------------------------------------------------------ | ---------------------------------- | -------------------------------------------------------------------------------------------- |
| $\text{Exponential}(\lambda)$     | $\lambda e^{-\lambda x}$<br>$x \ge 0$                                                    | $\frac{1}{\lambda}$             | $\frac{1}{\lambda^2}$                                        | $\lambda > 0$                      | Models time between events in a Poisson process.                                             |
| $\Gamma( \alpha,\lambda)$         | $\frac{\lambda^k x^{\alpha-1} e^{-\lambda x}}{\Gamma(\alpha)}$ <br>$x > 0$<br>           | $\frac{\alpha}{\lambda}$        | $\frac{\alpha}{\lambda^2}$                                   | $\alpha > 0$, $\lambda > 0$        | Generalization of exponential; models waiting time for $\alpha$ events in a Poisson process. |
| $\mathcal{N}(\mu,\sigma^2)$       | $\frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x - \mu)^2}{2\sigma^2}}$<br>$x \in \mathbb{R}$ | $\mu$                           | $\sigma^2$                                                   | $\mu \in \mathbb{R}$, $\sigma > 0$ | Models symmetric data around a mean; central in the Central Limit Theorem.                   |
| $\text{Beta}(\alpha,\beta)$       | $\frac{1}{B(\alpha,\beta)} x^{\alpha - 1}(1 - x)^{\beta - 1}$<br>$x \in (0, 1)$          | $\frac{\alpha}{\alpha + \beta}$ | $\frac{\alpha\beta}{(\alpha + \beta)^2(\alpha + \beta + 1)}$ | $\alpha, \beta > 0$                | Models probabilities and proportions bounded between 0 and 1.                                |
| $\text{Cauchy}(x_0,\gamma)$       | $\frac{1}{\pi \gamma [1 + ((x - x_0)/\gamma)^2]}$<br>$x \in \mathbb{R}$                  | undefined                       | undefined                                                    | $x_0 \in \mathbb{R}, \gamma > 0$   | Heavy-tailed distribution; mean and variance do not exist.                                   |
| $U(a,b)$                          | $\frac{1}{b - a}$<br>$x \in [a, b]$                                                      | $\frac{a + b}{2}$               | $\frac{(b - a)^2}{12}$                                       | $a < b, \, a, b \in \mathbb{R}$    | Models equal probability over a fixed interval.                                              |
| $\text{LogNormal}(\mu, \sigma^2)$ | $\frac{1}{x \sigma \sqrt{2\pi}} e^{-\frac{(\ln x - \mu)^2}{2\sigma^2}}$<br>$x > 0$       | $e^{\mu + \sigma^2/2}$          | $(e^{\sigma^2} - 1)e^{2\mu + \sigma^2}$                      | $\mu \in \mathbb{R}, \sigma > 0$   | Models multiplicative growth; log of variable is normally distributed.                       |

# Distribution of a sum of random variables

- AKA **arithmetic of RVs**

If $X$ and $Y$ are [[Joint Distribution|jointly-distributed]] $\mathbb{N}$-valued RVs then $Z = X+Y$ is also a  $\mathbb{N}$-valued RV, and for $n \in \mathbb{N}$

![[Screenshot 2025-03-05 at 11.08.21 am.png|375]]

- If $X$ and $Y$ are independent, then
$$p_z(n) = \sum_{k=0}^n p_X(k)\:p_Y(n-k)\quad \forall n \in \mathbb{B}$$
- $p_Z$ is called the [[Convolution]] of $p_X$ and $p_Y$ as $p_Z \equiv p_X \star p_Y$   

## Examples
### Sum of independent binomial random variables with same $p$ 

- $X \sim \text{Binomial}(m,p)$ is independent of $Y \sim \text{Binomial}(n-m,p)$ 
- $Z = X+Y$ 
- So $Z \sim \text{Binomial}(n,p)$ (same $p$) 
	-  Formally, $\ell \in \{0,1,...,n\}$ 

![[Screenshot 2025-03-05 at 11.14.39 am.png|650]]

where the sum gives $\begin{pmatrix} n \\ \ell \end{pmatrix}$. So finally
$$P(Z=\ell) = \begin{pmatrix} n \\ \ell \end{pmatrix} p^\ell (1-p)^{n-\ell}$$ i.e. $Z \sim \text{Binomial}(n,p)$. 

### Sum of independent Poisson random variables

- $X \sim \text{Poisson}(\lambda)$ independent of $Y \sim \text{Poisson}(\gamma)$.
- What is the distribution of $Z = X+Y$ 
- For $n \in \mathbb{N}$

	![[Screenshot 2025-03-05 at 11.20.06 am.png|400]]
	- i.e $Z \sim \text{Poisson}(\lambda + \gamma)$ 


# Conditional Distribution of the Summand Given Total

## Binomial Sum

Let $X \sim \text{Binomial}(m,p)$, and  $Y \sim \text{Binomial}(n-m,p)$

- We know that $Z = X+Y \sim \text{Binomial}(n,p)$

> *What is the conditional distribution of $X$ given $Z =r$?*

![[Screenshot 2025-03-05 at 3.58.15 pm.png]]
**NOTE:** This is conditional on $Z = X+Y =r$. 

This is conditional probability is described by a [[Hypergeometric Random Variable]] $\text{Hyper}(m,n,r)$

![[Screenshot 2025-03-05 at 4.04.58 pm.png|500]]

> [!quote]  How to think of this?
> This described by [[Hypergeometric Random Variable]] because the conditional probability is like asking: From $n$ trials, I have had $r$ successes. What is the probability that $k$ of them are $X$-coloured from a total of $m$-many $X$-coloured balls?

- Here for $r$ with $P(Z=r)>0$, we can define **conditional[[Probability Mass Function | pmf]]** of $X$ given $Z=r$ as 
$$p_{X|Z}(k|r) := P(X=k \:|\: Z=r)$$


## Poisson Sum

Let $X \sim \text{Poisson}(\lambda)$, and  $Y \sim \text{Poisson}(\gamma)$ 

- Consider the *conditional pmf* of $X$ given $Z=X+Y = n\in\mathbb{N}$ 
- Since $Y\geq 0$, and $Z=n$, then $X = k \in \{0,1,...,n\}$

![[Screenshot 2025-03-05 at 4.18.26 pm.png|500]]

$\implies$ The conditional distribution of $X$, given $X+Y=n$ is $\text{Binomial}(n, p=1- \frac{\lambda}{\lambda+\gamma})$  

> [!quote] How to think of this?
> Imagine two sources emitting particles at rates $\lambda,\gamma$
> Each of the observed particles can be independently attributed to the first source with a fixed probability related to its relative intensity/rate.










