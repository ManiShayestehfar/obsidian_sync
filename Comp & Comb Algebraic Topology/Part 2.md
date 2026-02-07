![[Part 2-1770464474695.png|500]]
# $\varepsilon$-Thickening

Given $\{x_1,...,x_n\}=X$ in a metric space, we can construct $$X^\varepsilon = \bigcup_{x\in X}B(x,\varepsilon)$$
- **Q:** Is it possible to select $\varepsilon >0$ such that $X^\varepsilon \cong \mathcal{M}?$
	- How to compute the homology of $X^\varepsilon$? Yes under assumptions


# Filtrations

## Vietoris-Rips

Let $(M,d)$ be a finite metric space. $VR_\varepsilon(M)$ is defined as follows:

A set $\{x_0,x_2,...,x_k\}\subset M$ forms a $k$-simplex iff $d(x_i,x_j)\leq \varepsilon$ for all $i,j$.

## Cech

$M$ a finite subset of metric space $(Z,d)$. $C_\varepsilon(M)$ is defined as $\{x_0,...,x_k\}$ form a $k$-simplex iff $\exists z \in Z$ such that $d(z,x_i) \leq \varepsilon$.

i.e. $$C_\varepsilon = \left\{\sigma \subseteq X \:|\: \bigcap_{x\in \sigma} B(x,\varepsilon)\neq \varnothing\right\}$$
- This just the nerve of $X^\varepsilon$


>[!theorem]
>$C_\varepsilon \subset VR_{2\varepsilon}\subset C_{2\varepsilon}$