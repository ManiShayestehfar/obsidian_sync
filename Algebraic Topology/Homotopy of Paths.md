# Homotopy of paths

- Want to consider paths in $X$ with some endpoints $x_0,x_1$. Then the definition of $f,g$ being homotopic is not great.
	- Every path $f$ from $x_0$ to $x_1$ is homotopic to the constant path at either end points. e.g.
		$$f_t(s) = \begin{cases}
f(s) & s \leq t  \\[3pt]
f(t) & s > t
\end{cases}$$
		for $f(0)$.
	- Every constant path is homotopic to every other constant path if the two point have a path between them.
	- In path-connected $X$, *all* paths are homotopic to each other! so not a useful definition of homotopy.


>[!def] Homotopy of paths
>$x_0,x_1 \in X$, and let $f,g : I \to X$ be paths from $x_0$ to $x_1$. A **homotopy of paths** is a family of continuous functions $f_t:I \to X$ such that 
>1. $f_t(0) = x_0$, $f_t(1)=x_1$  $\forall t\in I$
>2. $f_0 = f$, $f_1=g$, and
>3. functions $F:I \times I \to X$ via $(x,t) \mapsto f_t(x)$ is continuous.

>[!def] Straight-line homotopy (also called linear homotopy
>from $f_0$ to $f_1$ is $f_t:I \to \mathbb{R}^n$ for all $t \in I$ such that 
>$$f_t(s) = (1-t)f_0(s) + tf_1(s)$$
```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2025.9.28 - 20.37pm.drawing",
	"width": 794,
	"aspectRatio": 3.862192921626531
}
```


>[!proposition] Prop 1.2 Hatcher
>$x_0 \in X$. Then the relation of homotopy on the set of all paths from $x_0$ to $x_1$in $X$ is an equivalence relation
##### Proof
Reflexivity and symmetry are obvious.
If $f \simeq g$, $g \simeq h$ via $f_t,g_t$. Define $h_t:I \to X$ by 
$$h_t(s) = \begin{cases}
f_{2t}(s) & s \in [0,1/2] \\[4pt] 
g_{2t-1}(s) & s \in [1/2,1]
\end{cases}$$
where we note that $f_1(s) =g_0(s)$ for all $s \in I$. Define $F:(s,t) \to f_t(s)$, $G:(s,t)\to g_t(s)$, $H:(s,t) \to h_t(s)$ where we know $F,G$ are continuous.

Using [[Pasting Lemma]], $H$ is also continuous for $A = I \times [0,1/2], \:\:B=I\times [1/2,1]$. In particular, continuous on $A$
 since $f_1(s)=g_0(s)$ for all $s \in I$. $\therefore f \simeq h$.   $\square$


# Homotopy Class
