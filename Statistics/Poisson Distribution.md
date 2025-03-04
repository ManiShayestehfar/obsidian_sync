>[!info] Definition
>$$p_X(k) = e^{-\lambda}\frac{\lambda^k}{k!}$$
>for $k \in \mathbb{N}$, and $\lambda > 0$.

- The Poisson distribution models the number of "events/occurrences" that are registered in a certain interval

**Assumptions:**
- The distribution of number of events at any time interval depends only on the interval's length/duration
- The number of events recorded in disjoint time intervals are independent from one another
- No two events are recorded at exactly the same time point

**What is its pmf?**
$$X_{s,t} = \# \:\:\text{of events in the time interval}\:(s,t]\:,\: \text{let}\:X_{t} = X_{0,t}$$
let $f(t):= P(X_t=0)$. Notice,

![[Pasted image 20250304215012.png]]

Solutions of this type: $f(t) = e^{\alpha t}$ for $\alpha \in \mathbb{R}$. This is the ONLY bounded solution as $\forall t > 0, f(t) \in [0,1]$ when $\alpha \leq 0$ so 
$$f(t) = e^{-\lambda t}$$
to find $P(X_1 = j)$ for $j>0$ consider

![[Pasted image 20250304220950.png]]

where $Y_n$ counts the number of successes in $n$ trials, where:
1. The trials are independent
2. The probability of success in the $k$-th trial is

![[Pasted image 20250304221245.png]]

$$\implies Y_n \sim \text{Binomial}(n,p_n=1-e^{\lambda/n})$$


> [!tip] Corollary 1
> $X = X_1\sim \text{Poisson}(\lambda): p_X(k) = e^{-\lambda} \frac{\lambda^k}{k!}$ for $k\in \mathbb{N}$.
##### Proof
For all $k \in \mathbb{N}$
$$P(X_1=k) = \lim_n P(Y_n=k)= e^{-\lambda}\frac{\lambda^k}{k!}$$

> [!tip] Claim 1
> If $Z_n \sim \text{Binomial}(n,p_n)$ such that $np_n \to \lambda > 0$, then for any fixed $k\in\mathbb{N}$,
> $$P(Z_n=k) \underset{n\to\infty}{\longrightarrow} e^{-\lambda}\frac{\lambda^k}{k!}$$ 
##### Proof
![[Pasted image 20250304223804.png]]



## Examples

### Bortkiewicz corp fatalities

![[Pasted image 20250304225050.png]]


### Faulty Monitor

![[Pasted image 20250304225133.png]]

$$N \sim \text{Poisson}(\lambda)$$ ![[Pasted image 20250304225307.png]]
i.e. $X \sim \text{Poisson}(\lambda p)$ 