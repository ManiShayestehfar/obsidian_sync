Let $(X,\tau)$ be a topological space pair, and $A \subseteq X$.

# Retraction

>[!def] Retraction
>A **retraction** of $X$ onto $A$ is a continuous function $r:X \to X$ (or equiv. $r: X\to A$) such that $r(X)=A$, or $r \circ i = \text{id}_A$.

## Examples

1. $x_0 \in X$, $r:X \to X, \: x \mapsto x_0$ (the constant map) is a retraction of $X$ to $A.$
2. $S$ a circle, the map that folds it in half is a retraction
3. $X = S^1 \times [0,1]$ (cylinder), $A = S^1 \times \{0\}$, and so $r:X \to X$ via $(x,t) \mapsto (x,0)$.


# Deformation Retraction

>[!def] Deformation Retraction
>A **deformation retraction** of a space $X$ onto a subspace $A$ is a family of continuous functions $f_t:X \to X$ for $t \in [0,1]=:I$ such that:
>1. $f_0(x)=x$
>2. $f_1(x)\in A$
>3. $f_t(a)=a$
>4. map $F:X \times I \to X$ via $(x,t) \mapsto f_t(x)$ is continuous (w.r.t product topology)

- A DR is a homotopy between $\text{id}_X$ and a retraction $r:X\to X$ such that points in $A$ stay fixed.

## Examples

1. $X = [0,1]$, $A= \{0\}$, then $f_t(x) = (1-t)x$ is a DR
2. $X = S^1 \times I$, $A = S^1\times \{0\}$, then $f_t(x,s) = (x,(1-t)s)$ is a DR
3. Mobius strip to its core circle is DR
4. Disc with two holes
```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2025.9.27 - 20.32pm.drawing",
	"width": 420,
	"aspectRatio": 2.677772426039567
}
```
5. $T^2\backslash\{p\}$ DR on figure 8.

>[!remark] 
>If $X$ DRs to a point $x_0$, then this gives a path from any point $x \in X$ to $x_0$. i.e. $p_x:[0,1]\to 1$ is continuous with $p_x(0) = x$, $p_x(1)=x_0$ given by $p_x(t)=f_t(x)$.
>Hence if $x$ DRs to a point, then $x$ is path connected. 
>*converse is not true:* for example $S^1$.


# Homotopy

>[!def] Homotopy
>A **homotopy** from $X \to Y$ is a family of continuous maps $f_t:X \to Y$ such that $F:X\to Y$ via $(x,t) \mapsto f_t(X)$ is continuous

## Examples

1. A DR from $X\to A \subseteq X$ is a homotopy $X\to X$.
2. $A \subseteq X$, $f_t(a)=a$ (inclusion map) $\forall t \in I$ and $\forall a \in A$ is a homotopy $A \to X$.
3. $\text{id}_X$ is a homotopy $X \to X$.


>[!def] Homotopic
>$g,h: X \to Y$ are **homotopic** if there exists a homotopy $f_t:X\to Y$ such that $f_0 = g$ and $f_1 = h$. Write $g \simeq h$

## Examples

1. Suppose we have DR $X \to A \subseteq X$ with $f_t(x):X \to X$. Then $\text{id}_X = f_0$ is homotopic to the retraction $f_1$.
2. Paths $g,h\in I \to X$
```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2025.9.27 - 20.47pm.drawing",
	"width": 706,
	"aspectRatio": 4.706666666666667
}
```

>[!def] Homotopy Equivalence
>map $f:X\to Y$ is a homotopy equivalence if there is a continuous map $g:Y \to X$ such that $g \circ f \simeq \text{id}_X$ and $f \circ g \simeq \text{id}_Y$.
```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2025.9.27 - 20.52pm.drawing",
	"width": 768,
	"aspectRatio": 5.12
}
```
## Examples

1. A homeomorphism is a homotopy equiv. i.e. $X \cong Y \iff X \simeq Y$
2. If $X$ DRs to $A \subseteq X$, then $X$ and $A$ are homotopy equivalent
```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2025.9.27 - 20.56pm (2).drawing",
	"width": 606,
	"aspectRatio": 3.282476083643647
}
```
can see $f_1 \circ i \simeq \text{id}_A$, and check that $i \circ f_1 \simeq \text{id}_X$. Also $f_0 = \text{id}_X$, $f_1(x) = i \circ f(x)$ for all $x \in X$, so the DR $f_t:X \to X$ gives a homotopy from $\text{id}_X$ to $i \circ f_1$

3. Spaces
```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2025.9.27 - 21.03pm.drawing",
	"width": 710,
	"aspectRatio": 4.733333333333333
}
```
are homotopy equivalent but *not* DR of each other.


# Contractible

>[!def] Contractible
>$X$ is **contractible** if it is homotopy equivalent to a point, i.e. $X \simeq \{x_0\}$. 
>If $X$ DRs to a point, then $X$ is contractible. 
>- Converse not true.

>[!def] Nullhomotopic
>A continuous map $f:X\to X$ is **nullhomotopic** if it is homotopic to a constant map $X \to \{p\}$

$$X \:\:\text{contractible} \iff \text{id}_X\:\:\text{is nullhomotopic} $$

