AKA **Propagation of Errors**

# Applied to Estimating $E(\tilde{\Theta}_n)$

- See [[Hardy-Weinberg Equilibrium Model]] for context

- We use this to deduce the asymptotic behaviour of 
$$E(\tilde{\Theta}_n) = E\left(\sqrt{\frac{T_3}{n}}\right)$$
	which is hard to compute, from the mean and [[Variance]] of 
	$$\tilde{\Theta}_n^2 = \frac{T_3}{n}$$
---
$T_3 \sim \text{Binomial}(n,\theta^2)$ 

**Mean:**
$$E(\tilde{\Theta}_n^2) = \frac{n\theta^2}{n} = \theta^2$$
**Variance:**
$$V(\tilde{\Theta}_n^2) = \frac{n\theta^2(1-\theta^2)}{n^2} = \frac{\theta^2(1-\theta^2)}{n}$$

Let $X$ be an $L^2$-RV, $g:\mathbb{R}\to \mathbb{R}$ smooth and let $Y = g(X)$.
$$X = \tilde{\Theta}_n^2 = \frac{T_3}{n}\quad\text{and}\quad g(x) = \sqrt{x} \quad \text{so} \quad Y = \sqrt{X} = \tilde{\Theta}_n$$
- We need $E(Y) = E(g(X))$ 
- Consider the second order Taylor expansion of $g$ about $\mu = E(X)$
$$g(X) = g(\mu) + g'(\mu)(x-\mu) + \tfrac{1}{2}g''(\mu)(x-\mu)^2 + TR_2(x)$$
	where $TR_2(x) / (x-\mu)^2 \to 0$ as $x \to \mu$.

- If $X \approx \mu$ and we plug $X$ into $g$ then
$$Y = g(X) \approx g(\mu) + g'(\mu)(X-\mu) + \tfrac{1}{2}g''(\mu)(X-\mu)^2$$
and so
$$E(Y) = g(\mu) + \tfrac{1}{2}g''(\mu)\sigma^2$$


In our case

![[Pasted image 20250405145521.png]]

![[Pasted image 20250405153953.png]]
![[Pasted image 20250405154029.png]]


>[!warning] 
>- Note that this calculation is valid only if $X \approx E(X)$


# Asymptotic Expression for $E(\tilde{\Theta})$

>[!tip] Claim 1
>For $\theta \in (0,1)$,
>$$E(\tilde{\Theta}) = \underbrace{\theta - \frac{1-\theta^2}{8n\theta}}_{\text{same as $\delta$-method}}  + R_n $$
>where $nR_n \underset{n}{\longrightarrow} 0$
##### Proof
Proof in Lecture 16 and 17

>[!tip] Corollary 1
>For $\theta \in (0,1)$,
>$$MSE(\tilde{\Theta}_n) = \underbrace{\frac{1-\theta^2}{4n}}_{\text{same as $\delta$-method}}  + R'_n $$
>where $nR'_n \underset{n}{\longrightarrow} 0$
##### Proof

Recall from [[Hardy-Weinberg Equilibrium Model]],

![[Pasted image 20250405163415.png]]

where $nR'_n = -2\theta\cdot nR_n \underset{n}{\longrightarrow} 0$  


>[!example] Remark 1
>This *rigorously* establishes the consistency of $\tilde{\Theta}$ for $\theta \in (0,1)$:
>$$MSE(\tilde{\Theta}_n) = \frac{1-\theta^2}{4n} + R'_n \underset{n}{\longrightarrow} 0$$

![[Pasted image 20250405163825.png]]

![[Pasted image 20250405163834.png]]