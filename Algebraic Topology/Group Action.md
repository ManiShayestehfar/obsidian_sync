>[!def] Group action
>An **action** of a group $G$ on a set $X$ is a homomorphism $\rho:G \to \text{Sym}(X)$.
>i.e. $\forall g \in G$ we have a bijection $\rho(g):X \to X$ such that $\rho(g_1g_2)(x) = \rho(g_1)(\rho(g_2)(x))$ and $\rho(1) = \text{id}_X$.
>- Write $g\cdot x$ or $gx$ for short

## Examples

1. $\mathbb{Z}$ acts on $\mathbb{R}$ by translation $mx = x+m$
2. $\mathbb{Z}/2\mathbb{Z}$ acts on $S^n$ by $ax=-x$


>[!def] Faithful action
>Action of $G$ on $X$ is **faithful** if $\{g \in G \:|\: gx =x\:\:\:\forall x \in X\}=\{1_G\}$ 
>- This is the kernel of the action and is a normal subgroup
>- Equivalently the map $\rho$ is injective



