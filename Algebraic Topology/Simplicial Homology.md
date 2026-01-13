Let $X$ be a $\Delta$-complex

# n-Chain

>[!def] 
>For $n \geq 0$, an **n-chain** is a finite formal sum $\sum_\alpha k_\alpha e_\alpha^n$ where $k_\alpha \in \mathbb{Z}$ and each $e_\alpha^n$ is an open n-simplex in $X$. 
>- Write $\Delta_n(X)$ for the set of all n-chains.

- Equivalently we can write n-chains as the finite formal sums of character maps $\sum_\alpha k_\alpha \sigma_\alpha$.

## Examples

![[Screenshot 2025-10-09 at 3.32.29 pm.png|500]]


## n-chains as Free $\mathbb{Z}$-mod  

>[!lemma] 
>$\Delta_n(X)$ is a free $\mathbb{Z}$-module (i.e. a free abelian group) with addition as group operation.

- A basis for $\Delta_n(X)$ is set of all open n-simplices, or equivalently, their characteristic maps 


# Boundary of an n-Simples

**Notation:** write $[v_0,...,\hat{v}_i,...,v_n]$ for the face obtained by deleting the vertex $v_i$ from the n-simplex

>[!Def] 
>The **boundary of an n-simplex** $[v_0,...,v_n]$ in $X$ is the $(n-1)$-chain given by $$\partial_n([v_0,...,v_n]) = \sum_{i=0}^n (-1)^i [v_0,...,\hat{v}_i,...,v_n] \in \Delta_{n-1}(X)$$ 

## Examples

![[Simplicial and Delta-Complexes-1760071315731.png|600]]

## Boundary Homomorphism

>[!Def] 
>For $X$ a $\Delta$-complex, the **boundary homomorphism** $\partial_n:\Delta_n(X) \to \Delta_{n-1}(X)$ is defined on basis elements $\sigma_\alpha$ by $\partial_n \sigma_\alpha = \sum_{i=0}^n (-1)^i \:\sigma_\alpha|_{[v_0,...,\hat{v_i},...,v_n]}$ where $[v_0,...,v_n]=\Delta^n$ is the standard n-simplex.
>
### Examples

$\partial_1([v_0,v_1]+[v_1,v_2]-[v_0,v_2]) = [v_1]-[v_0] + [v_2]-[v_1]-[v_2]+[v_0] = 0 = \partial_1\circ \partial_2([v_0,v_1,v_2])$ 

**Takeaway lemma**
>[!lemma]
>The composition $\Delta_n(X)\overset{\partial_n}{\longrightarrow}\Delta_n(X) \overset{\partial_{n-1}}{\longrightarrow}\Delta_{n-2}(X)$ is zero.
>i.e. $\partial_{n-1}\circ \partial_n$ is the zero map.
>i.e. $\text{im }\partial_n \subseteq \ker \partial_{n-1}$
>

*Proof:*
Coefficients of $\sigma_\alpha|_{[v_0,...,\hat{v}_i,...,\hat{v_j},...,v_n]}$ is $(-1)^{i}(-1)^{j-1} + (-1)^i(-1)^j = 0$. This holds for all $0 < i < j\leq n$ and $\forall \alpha$.  $\square$ 



# Chain Complex

Let $\partial_0:\Delta_0(X) \to 0$ be the zero map. We have a sequence of $\mathbb{Z}$-modules. $$\cdots\:\overset{\partial_{n+2}}{\longrightarrow} \Delta_{n+1} \overset{\partial_{n+1}}{\longrightarrow}\Delta_{n} \overset{\partial_{n}}{\longrightarrow}\Delta_{n-1} \overset{\partial_{n-1}}{\longrightarrow}\cdots \Delta_{1} \overset{\partial_{1}}{\longrightarrow}\Delta_{0} \overset{\partial_{0}}{\longrightarrow}0$$ such that $\partial_n \circ \partial_{n+1} = 0$ for all $n \geq 0$. i.e. $\text{im }\partial_{n+1}\subseteq \ker \partial_n$.

>[!Def] 
>A **chain complex** is a sequence of $\mathbb{Z}$-modules and homomorphisms
>$$\cdots\:\overset{\partial_{n+2}}{\longrightarrow} C_{n+1} \overset{\partial_{n+1}}{\longrightarrow}C_{n} \overset{\partial_{n}}{\longrightarrow}C_{n-1} \overset{\partial_{n-1}}{\longrightarrow}\cdots C_{1} \overset{\partial_{1}}{\longrightarrow}C_{0} \overset{\partial_{0}}{\longrightarrow}0$$
>- For $n \geq 0$, the elements of $\ker \partial_n$ are called **n-cycles** and the elements of $\text{im }\partial_{n+1}\subseteq C_n$ are **n-boundaries**.


# $n$-th Simplicial Homology Group

>[!def] 
>The **n-th simplicial homology group** of a $\Delta$-complex $X$ is $$H_n^\Delta(X) = \ker \partial_n/\text{im }\partial_{n+1} = \text{n-cycles}/\text{n-boundaries}$$

## Examples

![[Simplicial Homology-1760085452835.png]]
![[Simplicial Homology-1760085683526.png]]

![[Simplicial Homology-1760085706291.png]]
![[Simplicial Homology-1760085721844.png]]
![[Simplicial Homology-1760085739497.png]]

