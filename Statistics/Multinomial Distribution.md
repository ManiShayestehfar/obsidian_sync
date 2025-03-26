- The multinomial [[Distributions|distribution]] models an experiment with $n$ iid trials. 
- Each trial has $r$ possible outcomes, where outcome $i$ has probability $p$ so that $\sum p_i = 1$

# Examples

- Roll a die $n$ times and record $n$ outcomes. The multinomial random vector $\mathbf{N} = (N_1,...,N_r)$ yields the number of trials each outcome came up.

- For a sequence of $n=15$ rolls that yielded $3,6,2,2,1,6,6,3,4,1,1,5,4,3,6$ we have
$$\mathbf{N} = (3,2,3,2,1,4)$$
	**GOAL:** find the pmf $p_{\mathbf{N}}(\mathbf{n}) = P_{\mathbf{N}}(n_1,...,n_r) = P(N_1=n_1,...,N_r = n_r)$ 
	- $p_\mathbf{N}(\mathbf{n}) = 0$ unless $n_i \in \mathbb{N}$ and $\sum_{i=1}^r n_i = n$  
	- One particular configuration is
	 ![[Screenshot 2025-03-19 at 2.14.47 pm.png|300]]
	where the probability of this configuration is $p_1^{n_1}\cdot p_2^{n_3}\cdot ... \cdot p_r^{n_r}$.
	- Notice that this is *order invariant*

## Multinomial Coefficient

![[Screenshot 2025-03-19 at 2.18.27 pm.png]]

## PMF
$$p_{\mathbf{N}}(n_1,...,n_r) = \binom{n}{n_1\:...\:n_r}\:p_1^{n_1}\cdots p_r^{n_r}$$
- Proof in Lecture 11


# MLE

 Suppose a sample size $n=1$
 $$\mathbf{x} = (x_1,...,x_r)$$
 is drawn from a $\text{Multinomial}(m;p_1,...,p_r)$ where $m$ is known $(m = \sum_{i=1}^n x_i)$ but $\mathbf{\theta}:=(p_1,...,p_r)$ is not known.

- i.e. in $m=1000$, rolls of a die we observe $\mathbf{x} = (105,207,253,152,182,101)$.

**How to estimate $p_i$ using moments?** With MLE

$$\begin{align*}
L(\mathbf{\theta}) &= P_\theta(X_1=x_1,...,X_r=x_r) \\[8pt]
&= \binom{m}{x_1,...,x_r}\prod_{i=1}^r \theta_i^{x_i}
\end{align*}$$
$$\ell(\mathbf{\theta}) = \log \binom{m}{x_1,...,x_r} \:+\: \sum_{i=1}^r x_i \log \theta_i$$
Let $g(\mathbf{\theta}) = \sum_{i=1}^r x_i \log \theta_i$
