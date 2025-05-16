> [!abstract] **What does it mean?**
> The expected value of a function $g(X)$ of an RV $X$ can be expressed as
> $$E[g(X)] = \sum_xg(x)p_X(x)$$

# Expectation of a Function of a RV

- Let $X$ be a discrete RV with range $X(\Omega)=\{x_k\}$, and let $g:\mathbb{R} \to \mathbb{R}$. 
- Then $Y  = g(X)$ is a discrete RV with pmf $p_Y$

![[Pasted image 20250305233446.png]]


# Continuous RV Analogy

If $X$ is a cont. RV and $g: \mathbb{R}\to\mathbb{R}$ (measurable) then $Y = g(X)$ is *not necessarily a cont. RV*, nevertheless
$$Y \in L^1 \iff \int_\mathbb{R}|g(x)| \:f_X(x) \:dx < \infty$$
and if $Y \in L^1$ (or $Y\geq 0$ or $Y \leq 0$) then 
$$E(Y) = \int_\mathbb{R}g(x)f_X(x)\:dx$$