# Complex

>[!def] CW Complex
>A cell complex for a **CW Complex** is a topological space $X$ constructed as follows:
>1. Start with a discrete set $X^0$, whose point are $0-$cells
>2. Inductively, form the **$n$-skeleton** $X^n$ from $X^{n-1}$ by attaching $n$-cells $e^n_\alpha$ via maps $\varphi_\alpha:S^{n-1} \to X^{n-1}$. This means that $X^n$ is the quotient space of the disjoint union $X^{n-1} \sqcup_\alpha D^n_\alpha$ of $X^{n-1}$ with a collection of $n$-discs $D^n_\alpha$ under the identifications $x \sim \varphi_\alpha(x)$ for $x \in \partial D_\alpha^n$. Thus as a set $X^n= X^{n-1} \sqcup_\alpha e_\alpha^n$ where each $e_\alpha^n$ is an open $n$-disc.
>3. Can either stop this inductive process at a finite stage, setting $X = X^n$ for some $n<\infty$, or one can continue indefinitely, setting $X=\cup _n X^n$. In the latter case $X$ is given the weak topology: A set $A \subset X$ is open (or closed) if and only if $A \cap X^n$ is open (or closed) in $X^n$ for each $n$.

- **CW** stands for "Closure-Finite", weak topology
	- Any compact subset of $X$ intersects with the interior of only finitely many cells. So does the boundary of any cell. 

## Examples

1. A 1-dim CW complex is a topological graph
2. $S^1$ is a 1-cell and a 0-cell. $S^2$ is a 0-cell and a 2-cell. 
		So $S^n = (e^0 \sqcup e^n)/\sim$

3. 
```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2025.9.27 - 22.16pm.drawing",
	"width": 854,
	"aspectRatio": 3.8920802327970874
}
```
Add two discs to $S^n$ to get $S^{n+1}$ , each with boundary attaching to the whole of $S^n$. $S^\infty = \cup_{n=0}^\infty S^n$ by continuing this.

4. Real projective space $\mathbb{R}P^n$ for $n \geq 0$ defined as:
	- Lines through the origin $\mathbb{R}^{n+1}$
	- Quotient of $\mathbb{R}^{n+1}\backslash\{0\}$ under $x \sim \lambda x$ $\forall x \in \mathbb{R}^{n+1}\backslash\{0\}$ $\forall \lambda \neq 0$.
	- Quotient of $S^n$ under $x \sim -x$ $\forall x \in S^n$ (identify antipodal points)
	- Quotient of $D^1$ under $x \sim -x$ $\forall x \in \partial D^n=S^{n-1}$.

	We can get $\mathbb{R}P^n$ from $\mathbb{R}P^{n-1}$ by attaching a single $n$-cell via the quotient $S^{n-1}\to \mathbb{R}P^{n-1}$ so $\mathbb{R}P^n = e^0 \cup e^1 \cup \cdots \cup e^{n-1} \cup e^{n} = \mathbb{R}P^{n-1} \cup e^n$.
	 Define $\mathbb{R}P^\infty := \cup_{n=0}^\infty \mathbb{R}P^n$. Quotient $S^\infty\to\mathbb{R}P^\infty$ induced by $x \sim -x$. 

5. Real Line: 0-cell $= \mathbb{Z}$, 1-cell $e^1_\alpha$ for $\alpha \in \mathbb{Z}$ with $\varphi_\alpha(0) = \alpha$. $\varphi_\alpha(1) = \alpha+1$



## Subcomplex

>[!def] Subcomplex
>A **subcomplex** of a cell complex $X$ is a closed subspace $A \subseteq X$ which is a union of cells of $X$.
>- It is a cell complex on its own

