# Covering Space

>[!def] 
>A **covering space** of $X$ is a space $\widetilde{X}$ together with a continuous map $p: \widetilde{X} \to X$ such that 
>1. $\exists$ open cover $\{U_\alpha\}$ of $X$ such that
>2. $\forall \alpha,\:\:p^{-1}(U_\alpha)$ is a disjoint union of open sets in $\widetilde{X}$, each homeomorphically mapped onto $U_\alpha$ by $p$.
>   
>   ![[Covering Space-1759723390379.png|170]]
>   

## Examples

1. $X=S^1,\widetilde{X} =\mathbb{R}$, $p=\mathbb{R} \to S^1$ by $t \mapsto (\cos 2\pi t,\:\sin 2\pi t)$.

![[Covering Space-1759723584644.png|200]]

Take $\{U_\alpha\}$ the smallest collection of open arcs in $S^1$ that cover $S^1$. Then $p^{-1}(U_\alpha)$ is a disjoint union of collection of open intervals in $\mathbb{R}$, with restriction of $p$ to each such interval being a homeomorphism to $U_\alpha$.

2. $X=S^1$, $\widetilde{X} = S^1$ both 