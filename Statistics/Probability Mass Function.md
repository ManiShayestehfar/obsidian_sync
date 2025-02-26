>[!info] Definition
>The **probability mass function (pmf)** of a random variable $X$ is defined as:
>$$p_X(x) := P(X=x) = P(\{\omega : X(\omega) = x\})\quad \forall x \in \mathbb{R}$$ 
>**What does it mean?** A pmf tells us the probability that a random variable $X$ is exactly equal to some value $x$.
>


>[!tip] Claim 1
> If $X$ is a discrete random variable with distinct $\{x_i\} = X(\Omega)$ and pmf $p_X$ then 
> 1. $\forall x \in \mathbb{R}\backslash X(\Omega)\quad p_X(x) = 0$
> 2. $\sum_i p_X(x_i)=1$
> 3. $p_X(x) \geq 0\quad \forall x\in \mathbb{R}$

>[!tip] Claim 2
>The distribution of a discrete random variable is completely specified by its pmf
##### Proof
$\forall A \subset \mathbb{R}$, $X\in A$ $\iff X = x_i$ . Then
$$\begin{align*} P(X\in A) &= P\left(\bigcup_{i:x_i\in A} \{X = x_i\} \right) \\[4pt] &= \sum_{i:x_i\in A} P(X=x_i) \\[4pt] &= \sum_{i:x_i\in A} p_X(x_i)\end{align*}$$

## Examples

### Bernoulli
A $\text{Bernoulli}(p)$ Random Variable is defined by the pmf
$$p(x) = \begin{cases} 1-p & x=0 \\ p & x=1 \\ 0 & x \not\in\{0,1\} \end{cases}$$
- Clear that $\sum_i p(x_i) = 1$ 

### Heads-Tails
$\Omega = \{H,T\}$, $P(\{H\}) = p$.
$$X(\omega) = 1_{\{H\}}(\omega) = \begin{cases} 1 & \omega = H \\ 0 & \omega \neq H \end{cases}$$

### Binomial
A Binomial random variable $S_n$ models the number of successes in $n$ independent identically distributed success/failure (or Bernoulli) trials

- A 2-parameter family of distributions $(n,p) = (\#\:\text{of trials, probability of success in each trial}).$

The range of $S_n$ is: $S_n(\Omega)= \{0,1,2,...,n\}$. 

**What is its pmf?**
Suppose $k \in \{0,1,2,...,n\}$. and consider $S_n=k$. i.e from $n$ many trials, we have $k$ many successes and $n-k$ many failures.  Then for $\alpha_1, \alpha_2,...,\alpha_n$ where $\alpha_i \in \{s,f\}$,
$$P(s...sf...f) = p^k(1-p)^{n-k}$$

To account for all configurations:
$$P(S_n = k) = \begin{pmatrix}n \\ k \end{pmatrix} p^k(1-p)^{n-k}\quad k \in S_n(\Omega).$$

### Geometric
A geometric random variable $X$ models the number of independent and identically distributed $\text{Bernoulli}(p)$ trials it takes until the first success. 
- A 1-parameter family $(p)$
$$X(\Omega) = \{1,2,3,...\}\cup \{\infty\}$$
**What is its pmf?**
For $k \in \mathbb{N}_1 :=\{1,2,...\}$, $X=k$ if and only if the outcome of the Bernoulli sequence of trials is $k-1$ many fails and one success. Hence
$$P(X=k) = (1-p)^{k-1}p$$

### Negative Binomial
A negative binomial random variable $X^r$, where $r \in \mathbb{N}_1$ is a fixed parameter, models the number of independent and identically distributed $\text{Bernoulli}(p)$ trials until the $r^{th}$ success. 
- A 2-parameter family $(r,p)$.
$$X^r(\Omega)= \{r,r+1,...\} \cup \{\infty\}$$

**What is its pmf?**
Fix $k \in \{k, k+1,...\}$ and consider configuration for which $X^r = k$. That is $k-r$ many fails and $r$ many successes. Probability of each configuration is 
$$(1-p)^{k-1}p^r$$

How many configurations are there for which $X^r = k$?

![[Pasted image 20250226225134.png|400]]

$$\implies P(X^r = k) = \begin{pmatrix} k-1 \\ r-1\end{pmatrix} p^r(1-p)^{k-r}\quad\quad k \in \{r,r+1,...\}$$