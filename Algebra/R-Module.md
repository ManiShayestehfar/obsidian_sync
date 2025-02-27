
>[!info] Definition 1.1
>Let $R$ be a [[Ring]]. An **R-Module** is an additive abelian [[Group]] $V$ with a ring homomorphism $\Phi: \mathbb{R} \to \text{End}(V)$ or $\Phi: \mathbb{R} \times V \to V$ such that $\Phi(1_R) = 1_V$ is the identity map on $V$.

$$R\text{-Module is a Vector Space} \iff R\text{   is a field  } \mathbb{F}$$


## Subspace

A **subspace** of $V$ is an abelian subgroup $W$ of $V$. I.e. $W$ is a subset that is closed under addition and scalar multiplication (w.r.t $\mathbb{F}$).

>[!tip] Subspace Criterion
>A non-empty subset $U$ of $V$ is a vector subspace if and only if $u - u' \in U$ for $u,u'\in U$.

- if $X$ and $Y$ are subsets of the additive abelian [[group]] $V$, then $$X + Y = \{x+ y \:|\: x \in X \text{ and } y \in Y\}$$is a subspace of $V$




## Coset

If $W$ is a subspace of $V$ and $v \in V$, then the **coset** of $v$ in $W$ is 
$$[v] =v + W = \{v+w \:|\: \omega \in W\}$$

- $v + W = v'+ W \iff v - v' \in W$ 
- $v + W$ is a subspace of $V$ $\iff v \in W$ 
	- $v + W = W = 0 + W$






## Quotient Space

If $W$ is a subspace of $V$ then the **quotient space** 
$$V / W = \{v + W \:|\: v \in V\}$$
then $V / W$ is a $\mathbb{F}-$vector space with
- **Vector Addition:** $(v + W) + (v' + W) = (v + v') + W$ 
- **Scalar Multiplication:** $\lambda(v + W) = (\lambda v) + W$

>[!warning] $V / W$ is an additive abelian [[group]] under vector addition under Definition 1.1. $\Phi: \mathbb{F} \to \text{End}(V / W)$ is simply scalar multiplication.

# Action

For $r \in R$, let $\varphi_{r}= \Phi(r) \in \text{End}(V)$. Then $\varphi_{r}: V\to V$ is a homomorphism. Since $\Phi$ is a [[Ring]] homomorphism
1. $\varphi_{r+s} = \Phi(r+s) = \Phi(r) + \Phi(s) = \varphi_{r}+ \varphi_s$ 
2. $\varphi_{rs} = \Phi(rs) = \varphi_{r}\circ \varphi_{s}\quad$   for $r,s\in R$ 


>[!info] Definition
> The ring homomorphism $\Phi$ defines an **action** of $R$ upon $V$ given by
> $$rv = \varphi_{r(v)}\in V$$

--> Think of this as giving a "scalar multiplication" of $R$ upon $V$ as this definition shows that 
- $(r+s)v = rv + rs$
- $(rs)v = r(sv)$ 

--> $1_{R} v = v$   for all $v \in V$ since  $\varphi_{1_{R}} = \Phi(1_{R})= 1_V$ 







