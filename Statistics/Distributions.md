
>[!info] Definition
>The **distribution** of a [[Random Variables| random variable]] $X$, $\mu_x$,is a function defined on *measurable* subsets of $\mathbb{R}$ such that for any *measurable* $A \subset \mathbb{R}$,
>$$\mu_X(A) = P(X \in A).$$ 


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