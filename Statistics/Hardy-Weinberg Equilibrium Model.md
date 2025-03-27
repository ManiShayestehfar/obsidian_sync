>[!example] Context
>A certain gene has two variants in the population: a major allele (variant) “$A$” and a minor allele “$a$”. 
>
>Each individual carries two copies of the gene in their genome so their genotype is therefore one of: $AA, Aa,$ or $aa$.
>
>Under the Hardy-Weinberg equilibrium assumption the gene frequencies are at an equilibrium and it follows that $AA, Aa, aa$ occur in the population with corresponding frequencies $(1 − \theta)^2$ , $2\theta(1 − \theta)$, $\theta^2$ where $\theta$ is the frequency of the minor allele $a$.

If the population is entirely homogeneous then we can imagine artificially creating an embryo by randomly drawing individual chromosomes or alleles from the population:

![[Pasted image 20250327091943.png]]
$$\begin{align*}
P(M\to a, F\to a) &= \theta \cdot \theta = \theta^2 \\[5pt]
 
P(M\to a, F\to A) + P(M\to A, F\to a) &= \theta(1-\theta) + \theta(1-\theta) = 2\theta(1-\theta)
\end{align*}$$


# Estimating $\theta$

- Analyse a sample from population of Hong Kong
- The sample surveyed the genotype of the $MN$ blood group producing two types of antigens in red blood cells.
- This gene is made of two “co-dominant alleles”, i.e., genotype = phenotype, or "What You See Is What You Get".

![[Pasted image 20250327092509.png]]

![[Pasted image 20250327092524.png]]

## Method of Moments

**What is the distribution of $T_3$?**
$$T_3 \sim \text{Binomial}(n, \theta^2)$$
So 
$$E(T_3) = n\theta^2 \implies \theta = \sqrt{\frac{E(T_3)}{n}}$$
and 
$$\tilde{\theta} = \sqrt{\frac{\tilde{\mathbf{t}}_3}{n}} \overset{\text{sample size = 1}}{=} \sqrt{\frac{t_3}{n}} = \sqrt{\frac{187}{1029}} \approx 0.4263$$
but this method only takes into account the $T_3$ population and not all of the data. So we should be able to do better

**-> Consider the portion of $''a''$ alleles in the sample**

Replace the observed sample $\mathbf{t} = (t_1,t_2,t_3)$  with a random sample $\mathbf{T} = (T_1,T_2,T_3) \sim \text{Multinomial}(n,\mathbf{p})$ with $\mathbf{p}$ as before
$$E\left[\frac{T_1 \cdot 0 + T_2 \cdot 1 + T_3 \cdot 2}{2n}\right] = \frac{1}{2n}[E(T_2) + 2E(T_3)]$$

and so we can have a second moment estimate
$$\hat{\theta} = \frac{t_2 + 2t_3}{2n} = \frac{500 + 2 \cdot 187}{2 \cdot 1029} \approx 0.4247$$


- Both $\tilde{\theta}, \hat{\theta}$ are *1st order moment estimators* of $\theta$
- Intuitively $\hat{\theta}$ is better as it uses *all* of the data

## MLE

$$p_{\mathbf{N}}(n_1,...,n_r) = \binom{n}{n_1\cdots n_r}p_1^{n_1}...p_r^{n_r}$$
In our case $\mathbf{p} = ((1-\theta)^2\:,\: 2\theta(1-\theta)\:,\: \theta^2)$. Hence

![[Screenshot 2025-03-27 at 4.13.19 pm.png]]

- If $(t_2+2t_3)/2n = 0$ then $t_1=n$ and $\text{argmax}\ell(\theta)= 0 = (t_2+2t_3)/2n$
- But for $(t_2+2t_3)/2n \in (0,1)$ and for $\theta \in (0,1)$

![[Screenshot 2025-03-27 at 4.15.45 pm.png|550]]

Therefore $\theta = (t_2+2t_3)/2n$ maximises $\ell(\theta)$ in $(0,1)$. So
$$\hat{\theta}_{MLE} = \frac{t_2+2t_3}{2n}$$
