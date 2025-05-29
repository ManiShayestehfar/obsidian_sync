>[!example] CLT
>Suppose $X_i$ are i.i.d RVs with $\sigma^2=V(X_i)  < \infty$ and $\mu = E(X_i)$. Let $S_n = \sum_{i=1}^n X_i$ then (given $E(S_n) = n\mu, \:V(S_n) = n\sigma^2$)   $\forall x \in \mathbb{R}$
$$P\left(\frac{S_n - n\mu}{\sqrt{n}\sigma} \leq x\right)\underset{n\to \infty}{\longrightarrow} \phi(x) = \int_{-\infty}^x \frac{1}{\sqrt{2\pi}} e^{-\tfrac{t^2}{2}}\:dt.$$
Let $Y_n = \frac{S_n - n\mu}{\sqrt{n}\sigma}$ and $Z\sim N(0,1)$ then the CLT states that 
$$F_{Y_N}(x) \underset{n\to \infty}{\longrightarrow} F_Z(x)\quad\quad \forall x \in \mathbb{R}.$$
Since $\phi \equiv F_Z$ is cont. everywhere this is equivalent to 
$$\frac{S_n - n\mu}{\sqrt{n}\sigma} = Y_n \underset{n\to \infty}{\longrightarrow} Z\quad\text{in distribution}$$
##### Proof (special case where $M_{X_i}$ exists)

![[Central Limit Theorem-1748437137659.png|650]]
![[Central Limit Theorem-1748437160558.png|650]]
![[Central Limit Theorem-1748437325336.png|650]]
![[Central Limit Theorem-1748437901072.png|650]]







