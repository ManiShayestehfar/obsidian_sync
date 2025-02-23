
>[!info] Definition
>Let $R$ be a [[Ring]]. An **R-Module** is an additive abelian [[Group]] $V$ with a ring homomorphism $\Phi: \mathbb{R} \to \text{End}(V)$ or $\Phi: \mathbb{R} \times V \to V$ such that $\Phi(1_R) = 1_V$ is the identity map on $V$.


# Action

For $r \in R$, let $\varphi_{r}= \Phi(r) \in \text{End}(V)$. Then $\varphi_{r}: V\to V$ is a homomorphism. Since $\Phi$ is a ring homomorphism
1. $\varphi_{r+s} = \Phi(r+s) = \Phi(r) + \Phi(s) = \varphi_{r}+ \varphi_s$ 
2. $\varphi_{rs} = \Phi(rs) = \varphi_{r}\circ \varphi_{s}\quad$   for $r,s\in R$ 


>[!info] Definition
> The ring homomorphism $\Phi$ defines an **action** of $R$ upon $V$ given by
> $$rv = \varphi_{r(v)}\in V$$

--> Think of this as giving a "scalar multiplication" of $R$ upon $V$ as this definition shows that 
- $(r+s)v = rv + rs$
- $(rs)v = r(sv)$ 

--> $1_{R} v = v$   for all $v \in V$ since  $\varphi_{1_{R}} = \Phi(1_{R})= 1_V$ 







