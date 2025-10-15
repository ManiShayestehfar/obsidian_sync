# Degree

>[!lemma] 
>Any group homomorphism $f: \mathbb{Z} \to \mathbb{Z}$ must be $f(z)=dz$  for some $d \in \mathbb{Z}$.
##### Proof
Let $d=f(1)$. Then, $f(n) = nf(1) = dn$ for $n >0$, and $f(-n)=nf(-1)=(-d)n$.  $\square$


>[!def] 
>Let $n>0$. Consider a map $f:S^n\to S^n$. The induced map $f_*:H_n(S^n) \to H_n(S^n)$ must be of the form $f_*(z) = dz$ for some $d \in \mathbb{Z}$. 
>We call $d$ the **degree** of $f$, denoted $\deg f$.

## Properties

1. $\deg \mathbf{1} = 1$
2. If $f$ is not surjective, $\deg f = 0$. 
   **Proof:** $\exists x_0 \in S^n\setminus f(S^n)$ such that 
   ![[Screenshot 2025-10-15 at 3.56.46 pm.png]]
   $\implies f_* =0\implies \deg f = 0$. 