- Given observations (sample) $x_1,...,x_n$ from a distribution $F(\theta)$, where $\theta$ is an unknown parameter, we want to estimate $\theta$

![[Screenshot 2025-03-19 at 3.10.07 pm.png]]

#### Assumptions
- The sample $x_1,...,x_n$ is a particular realisation of the idd RVs $X_1,...,X_n \sim F(\theta)$
- Each of the sampled values can be a vector. Then the sample $\mathbf{x}_1,\mathbf{x}_2,...,\mathbf{x}_n$ is assumed to be a realisation of the iid random vectors $\mathbf{X}_1,\mathbf{X}_2,...,\mathbf{X}_n$ 
	- For example, there is a sample size $n=1$ from $\text{multinomial}(m;p_1,...,p_r)$ distribution, $\mathbf{x}_1 = (x_1^1,...,x_r^1)$ where $x_i^1$ is the number of times outcome $i$ came up in $m$ trials.

