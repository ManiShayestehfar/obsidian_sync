# n-Simples, n-Chain, boundary homomorphism

>[!def]
>A **singular n-simplex** is a continuous map $\sigma:\Delta^n \to X$

>[!Def]
>A **singular n-chain** is a finite formal sum $\sum_\alpha k_\alpha \sigma_\alpha$ for $k_\alpha \in \mathbb{Z}$, $\sigma_\alpha$ a singular n-simplex. Write $C_n(X)$ for the set of all singular **n-chains**.

- $C_n(X)$ is a **free $\mathbb{Z}$-module** with basis the set of all singular n-simplices $\sigma:\Delta^n \to X$.

>[!Def] 
>The **singular chain complex** for $X$ is $$\cdots\:\overset{\partial_{n+2}}{\longrightarrow} C_{n+1} \overset{\partial_{n+1}}{\longrightarrow}C_{n} \overset{\partial_{n}}{\longrightarrow}C_{n-1} \overset{\partial_{n-1}}{\longrightarrow}\cdots C_{1} \overset{\partial_{1}}{\longrightarrow}C_{0} \overset{\partial_{0}}{\longrightarrow}0.$$
>Similarly the **nth-singular homology group** of $X$ is $H_n(X) = \ker \partial_{n}/\text{im }\partial_{n+1}$

- If $f:X\to Y$ is a homomorphism, then $H_n(X) \cong H_n(Y)$  $\forall n \geq 0$