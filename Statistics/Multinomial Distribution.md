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
$$\hat{\mathbf{\theta}}_{MLE} = \text{argmax}\{g(\mathbf{\theta})\::\: \mathbf{\theta} \in \mathbb{R}^r, \theta_i \geq 0, \sum_{i=1}^r \theta_i = 1\}$$
<mark style="background: #FFB86CA6;">This is a constrained optimisation problem</mark>. *Lagrange multipliers*, or *ad-hoc*

## Ad-Hoc Optimisation

Consider 
$$\mathbf{x} = (10,0,0) \implies g(\mathbf{\theta}) = 10\log\theta_1\implies \hat{\mathbf{\theta}} = (1,0,0)$$
Similarly
$$\mathbf{x} = (4,6,0) \implies g(\mathbf{\theta}) =  4\log\theta_1 + 4\log\theta_2\implies \hat{\mathbf{\theta}} = (*,*,0)$$

We need to optimise $\mathbf{\theta}\in \mathbb{R}^r$ with $\sum_{i=1}^r \theta_i = 1$. Therefore for those $\mathbf{\theta}$ 
$$g(\theta_1,...,\theta_r) = g\left(\theta_1,...,\theta_{r-1}, 1 - \sum_{i=1}^{r-1}\theta_i\right)$$
Define
$$\begin{align*}
h(\theta_1,...,\theta_{r-1}) &:= g\left(\theta_1,...,\theta_{r-1}, 1 - \sum_{i=1}^{r-1}\theta_i\right) \\[6pt]
&= \sum_{i=1}^{r-1} x_i \log\theta_i \:+\: x_r\log\left(1 - \sum_{i=1}^{r-1}\theta_i\right)
\end{align*}
$$

And so the problem becomes
$$\hat{\mathbf{\theta}}_{MLE} = \text{argmax}\{h(\theta_1,...,\theta_{r-1})\::\: \mathbf{\theta} \in \mathbb{R}^{r-1}, \theta_i \geq 0, \sum_{i=1}^r \theta_i \leq 1\}$$
which is an <mark style="background: #BBFABBA6;">unconstrained optimisation </mark>


### Example

![[Pasted image 20250327084005.png]]

- Generally the maximum of $h$ on the given simplex is either on the boundary $\theta_i =0$, or at critical point
$$\frac{\partial h}{\partial \theta_i} = 0 \quad\quad i =1,2,...,r-1$$
- In this case boundary does not give the maximum since for $\theta_i = 0$, $\log \theta_i \to -\infty$ 

At the critical point

![[Screenshot 2025-03-27 085407.png]]

Hence at a critical point
$$\theta_k = \frac{x_k}{c} = \frac{x_k}{m}\quad\quad \text{for }k=1,2,...,r$$
The critical point is *unique* and because $h \to -\infty$ near boundary, the critical point has to be a global maximum. 

Therefore the MLE is
$$\hat{\theta}_k = \frac{x_k}{m}\quad\quad k=1,...,r $$