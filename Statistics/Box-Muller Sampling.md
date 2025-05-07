
- Suppose we want to sample the $N(0,1)$ dist. 
- If we can compute $\phi^{-1}(p)$ where $\phi(z) = \int_{-\infty}^z \frac{1}{\sqrt{2\pi}}e^{-t^2/2}\:dt$, then with $U \sim U(0,1)$, $\phi^{-1}(U) \sim N(0,1)$. (see [[Continuous RV|here]] for theorem).
- It's costly to compute $\phi^{-1}$, so instead we compute $F_S^{-1}$ for $S \sim \text{Exp}(\lambda)$:

![[Pasted image 20250506230147.png]]

- The **Box-Muller Method** relies on this observation and the previous analysis to efficiently sample a pair of ind. $N(0,1)$ values by:
1. Sampling $\theta \sim U(0,2\pi)$ and $s \sim \text{Exp}(1/2)$
2. Report $x = \sqrt{s}\cos(\theta), y = \sqrt{s}\sin(\theta)$ 
