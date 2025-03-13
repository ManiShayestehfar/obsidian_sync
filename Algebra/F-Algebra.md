>[!info] Definition
>A (unital) **$\mathbb{F}$-Algebra** is a [[ring]] $R$ with identity element $1_R$ which is also a $\mathbb{F}$-vector space w.r.t addition in $R$.
>
>--> An $\mathbb{F}$-algebra is a ring with its *coefficients* in $\mathbb{F}$. 
>
>A **finite dimensional $\mathbb{F}$-algebra** is an $\mathbb{F}$-algebra that is finite dimensional as an $\mathbb{F}$-vector space.

# Examples

- $\mathbb{F}G$ is an $\mathbb{F}$-algebra
- So is $\text{Mat}_n(\mathbb{F})$

# $\mathbb{F}$-Algebra Homomorphism

>[!info] Definition
>An $\mathbb{F}$-Algebra **homomorphism** is a [[Vector Space]] homomorphism $\varphi: A \to B$ that is also a ring homomorphism.

- Two algebras are **isomorphic** if there is a bijective algebra homomorphism between them


# $A$-Module

>[!info] Definition
>Let $A$ be an $\mathbb{F}$-algebra. A (left) **$A$-module** is a $\mathbb{F}$-vector space $V$ that is equipped with a unitary bilinear $A$-action.  i.e.
>$$A \times V \to V \quad;\:(a,v) \to av$$
>such that
>1. **Unital:** $1_A v = v$ for all $v \in V$
>2. **Associativity:** $(ab)v = a(bv)$ for all $a,b \in G$ and $v \in V$
>3. **Bilinearity:** $a(\lambda v + \mu w) = \lambda (av) + \mu (aw)$, and $(\lambda a + \mu b)v = \lambda (av) + \mu (bv)$  for all $a,b \in A$, $\lambda_\mu \in \mathbb{F}$, $v,w \in V$. 

## Submodules

- An **$A$- submodule** of an $A$-module $V$ is a vector subspace $W$ such that $aw \in W$ for all $a \in A$ and $w \in W$.

- Similarly, an $A$-module **homomorphism** is a vector space homomorphism $\phi: V \to W$ such that $\varphi(av) = a \varphi(v)$ for all $a \in A$ and $v \in V$.  


>[!tip] Image & Kernel
>Let  $V$ and $W$ be $A$-modules and let $\varphi: V \to W$ be an $A$-module homomorphism. Then
>1. $\ker \varphi = \{v \in V\:|\: \varphi(v) = 0 \}$ is an $A$-submodule of $V$ 
>2. $\text{im }\varphi = \{\phi(v)\:|: v \in V\}$ is an $A$-submodule of $W$.


## Isomorphism Theorems

Suppose $V$ is an $A$-module.

1. Suppose $\varphi:V \to W$ is an $A$-module homomorphism. Then $V/\ker\varphi \cong \text{im }\varphi$ 
2. Suppose $X$ and $Y$ are $A$-submodules of $V$. Then $(X+Y)/Y \cong X/(X\cap Y)$
3. Suppose $U\leq W \leq V$ are $A$-submodules of $V$. Then $V/W \cong (V/U)/(W/U)$
4. Suppose $W$ is a submodule of $V$. Then there is a 1-to-1 inclusion preserving correspondence between the submodules of $V$ that contain $W$ and the submodules of $V/W$.




