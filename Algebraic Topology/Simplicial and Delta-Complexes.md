
**Convex Hull:** The smallest convex polygon or polyhedron that completely encloses a given set of points

# N-simplex

>[!def]
>An **n-simplex** in $\mathbb{R}^m$ for $m\geq n + 1$ is the convex hull of $n+1$ ordered points $v_0,v_1,...,v_n$ in $\mathbb{R}^m$ such that the vectors $v_1-v_0, v_2-v_0, ... , v_n - v_0$ are linearly independent. 
>Call $v_0,...,v_n$ the **vertices** and write $[v_0,...,v_n]$ for the (ordered) simplex.
 
# $\Delta^n$ 

>[!def] 
>For $n \geq 0$, the standard $n$-simplex $\Delta^n$ is the subset of $\mathbb{R}^{n+1}$ given by 
>$$\Delta^n = \{(t_0,t_1,...,t_n)\in \mathbb{{R}}^{n+1}\:\:|\:\: \sum_{i=0}^n t_i = 1\:\:\text{and}\:\: t_i \in [0,1] \:\:\forall i\}$$

- $\Delta^n$ has $n+1$ vertices, unit vectors in each coordinate of $\mathbb{R}^{n+1}$. $\Delta^n$ is the convex hull of its vertices i.e. the linear combinations of vertices where coefficients sum to 1, and are non-negative.
## Examples

![[Screenshot 2025-10-09 at 2.29.26 pm.png|400]] 


# Face

>[!def] 
>A **face** of an n-simplex $[v_0,...,v_n]$ is a simplex with vertex set any non-empty subset of $\{v_0,...,v_n\}$ with the same ordering.

## Example

![[Screenshot 2025-10-09 at 2.38.11 pm.png|]]


# Canonical Linear Homomorphism

>[!def] 
>$\forall n \geq 0$, and any n-simplex $[v_0,...,v_n]$, the **canonical linear homomorphism** is $L_n:\Delta^n \to [v_0,...,v_n]$ given by $(t_0,...,t_n)\mapsto t_0v_0 + ... + t_n v_n$

