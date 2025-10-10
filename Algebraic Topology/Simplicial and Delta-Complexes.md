
**Convex Hull:** The smallest convex polygon or polyhedron that completely encloses a given set of points

# N-simplex

>[!Def]
>An **n-simplex** in $\mathbb{R}^m$ for $m\geq n + 1$ is the convex hull of $n+1$ ordered points $v_0,v_1,...,v_n$ in $\mathbb{R}^m$ such that the vectors $v_1-v_0, v_2-v_0, ... , v_n - v_0$ are linearly independent. 
>Call $v_0,...,v_n$ the **vertices** and write $[v_0,...,v_n]$ for the (ordered) simplex.

## Open n-Simplex

>[!Def] 
>An **open n-simplex** in $X$ is an n-simplex of $X$, say $e_\alpha^n$, with all its proper faces deleted.
>Open $0$-simplices are just the vertices themselves.

# $\Delta^n$ 

>[!Def] 
>For $n \geq 0$, the standard $n$-simplex $\Delta^n$ is the subset of $\mathbb{R}^{n+1}$ given by 
>$$\Delta^n = \{(t_0,t_1,...,t_n)\in \mathbb{{R}}^{n+1}\:\:|\:\: \sum_{i=0}^n t_i = 1\:\:\text{and}\:\: t_i \in [0,1] \:\:\forall i\}$$

- $\Delta^n$ has $n+1$ vertices, unit vectors in each coordinate of $\mathbb{R}^{n+1}$. $\Delta^n$ is the convex hull of its vertices i.e. the linear combinations of vertices where coefficients sum to 1, and are non-negative.
## Examples

![[Screenshot 2025-10-09 at 2.29.26 pm.png|400]] 


# Face

>[!Def] 
>A **face** of an n-simplex $[v_0,...,v_n]$ is a simplex with vertex set any non-empty subset of $\{v_0,...,v_n\}$ with the same ordering.

## Example

![[Screenshot 2025-10-09 at 2.38.11 pm.png|]]


# Canonical Linear Homomorphism

>[!Def] 
>$\forall n \geq 0$, and any n-simplex $[v_0,...,v_n]$, the **canonical linear homomorphism** is $L_n:\Delta^n \to [v_0,...,v_n]$ given by $(t_0,...,t_n)\mapsto t_0v_0 \:+\: ... \:+\: t_n v_n$

## Characteristic Map

The map $\sigma_\alpha:\Delta^n \to X$ that restricts to a homomorphism from the interior of $\Delta^n$ to the open n-simplex $e_\alpha^n$ is called the **characteristic map** for $e_\alpha^n$.

### Example

![[Simplicial and Delta-Complexes-1760070999254.png|300]]

# $\Delta$-Complex

>[!Def] 
>A **$\Delta$-complex** is a space $X$ constructed a follow:
>1. Start with a collection $\{\Delta_\alpha^{n_\alpha}\}$ of disjoint simplices together with collections of faces $\{\mathcal{F}_i\}$ such that all faces in each $\mathcal{F}_i$ have the same dimension.
>2. From the quotient space of $\sqcup_\alpha \Delta_\alpha^{n_\alpha}$ by identifying all elements of each $\mathcal{F}_i$ to a single simplex via the canonical linear homomorphism.

## Examples

![[Screenshot 2025-10-09 at 3.08.45 pm.png]]


# Simplicial Complex

>[!Def] 
>A **simplicial complex** is a $\Delta$-complex where each simplex is determined uniquely by its vertex set.

- In the example above $X$ is not simplicial. e.g. $\{v_0\}$ is the vertex set for both $[u_0]$, $[u_0,u_0]$ 

- **Fact:** Every $\Delta$-complex can be subdivided into a simplicial complex
## Examples 

1. $S^1$ has $\Delta$-complex structures ![[Screenshot 2025-10-09 at 3.11.32 pm.png|100]] 
   but neither are simplicial. A simplicial complex structure for $S^1$ is ![[Screenshot 2025-10-09 at 3.12.08 pm.png|60]] .

2. ![[Screenshot 2025-10-09 at 3.12.44 pm.png]]


