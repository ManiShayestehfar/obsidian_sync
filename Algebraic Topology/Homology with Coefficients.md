Till this point we had 
$$C_n(X) = \{\sum_in_i\sigma_i\:|\: \sigma_i:\Delta^n \to X, n_i \in \mathbb{Z}\:\:\forall i\}$$
- Instead of $\mathbb{Z}$, we could get it from any abelian group $(G,+)$.

>[!def] Generalisation of n-chains
>$$C_n(X;G):=\{\sum_i g_i \sigma_i\:|\: \sigma_i: \Delta^n \to X,\:g_i\in G \: \forall i\}$$

- $C_n(X;G)$ is an abelian group
$$\begin{align*}
\sum_i g_i \sigma_i + \sum_i g_i'\sigma_i &= \sum_i(g_i + g_i')\sigma_i \\
&= \sum_i(g_i'+g_i)\sigma_i \\
&= \sum_i g_i'\sigma_i + \sum g_i\sigma_i
\end{align*}$$
- Recall that $\partial$ maps were defined for each $\sigma_i$ and the extended linearly
	- For $C_n(X;G)$, $$\begin{align*}
\partial\left(\sum_i g_i \sigma_i\right)&= \sum_i \partial(g_i \sigma_i) \\
&= \sum_{i,j} (-1)^j g_i \sigma_i|_{[v_0,...,\hat{v}_j,...,v_n]}
\end{align*}$$ So $\sigma_i: \Delta_n \to X$ and the boundary map is $G[\Delta^n] \to X$ e.g. $\mathbb{Z}[\Delta^n]\to X$. Because $\partial$ is the same, it holds the same properties. i.e. $\partial^2 = 0$.


# Homology groups with coefficients in $G$

>[!def] Homology groups with coefficients in $G$
>Can define chain complexes, and **homology groups with coefficients in $G$** $H_n(X;G)$: $$\cdots \overset{}{\longrightarrow}C_n(X;G) \overset{\partial_n}{\longrightarrow}C_{n-1}(X;G)\overset{}{\longrightarrow}\cdots$$
>where $H_n(X;G):= \ker \partial_n/\text{im }\partial_{n+1}$

- To define the reduced homology, require the augmentation map $$\varepsilon : C_0(X;G)\overset{}{\longrightarrow}G \overset{}{\longrightarrow}0$$ via $\sum_i g_i \sigma_i \longmapsto \sum_ig_i$. This gives $H_i(X) \cong \widetilde{H}_i(X) \:\:\forall i \neq 0$ and $H_0(X) \cong \widetilde{H}_0(X) \oplus G$. Relative homology follows through similarly.

- **Note:** for $G = \mathbb{Z}/2\mathbb{Z}$ signs are absent so we can ignore orientation.

## Examples

1. $X = \{\text{point}\}$. Then $$H_n(X;G) = \begin{cases}
G & n =0 \\
0 & \text{otherwise}
\end{cases}$$
2. $X = S^k$. Then $$\widetilde{H}_n(X;G) = \begin{cases}
G & n = k \\
0 & \text{otherwise}
\end{cases}$$


## Theorems

For cellular homology, consider a sequence of $G'$s instead of $\mathbb{Z}$'s.
$$\cdots \overset{}{\longrightarrow}G^{\# \text{ n-cells}} \overset{d_n}{\longrightarrow}G^{\# \text{ (n-1)-cells}}\overset{}{\longrightarrow}\cdots$$

>[!theorem]
>$$H_n^{CW}(X;G) \cong H_n(X;G)$$
>for all $n$

>[!theorem] Cellular boundary map
>$$d_n\left(\sum_\alpha g_\alpha e^n_\alpha\right)= \sum_\alpha(\sum_\beta (d_{\alpha\beta}g_{\alpha})e_\beta^{n-1})$$
>for integers $d_{\alpha\beta}$ which are the degree of the maps $H_*(S^k;G)\overset{}{\longrightarrow}H_*(S^k;G)$
##### Proof

We need the following lemma for the proof

>[!lemma]
>If $f: S^k \to S^k$ has degree $m$, then $f_*:H_*(S^k;G)\overset{}{\longrightarrow}f_*:H_*(S^k;G)$ is multiplication by $m$.

