# Covering Space

>[!def] 
>A **covering space** of $X$ is a space $\widetilde{X}$ together with a continuous map $p: \widetilde{X} \to X$ such that 
>1. $\exists$ open cover $\{U_\alpha\}$ of $X$ such that
>2. $\forall \alpha,\:\:p^{-1}(U_\alpha)$ is a disjoint union of open sets in $\widetilde{X}$, each homeomorphically mapped onto $U_\alpha$ by $p$.
>   
>   ![[Covering Space-1759723390379.png|170]]
>   

## Examples

1. $X=S^1,\widetilde{X} =\mathbb{R}$, $p=\mathbb{R} \to S^1$ by $t \mapsto (\cos 2\pi t,\:\sin 2\pi t)$.

![[Covering Space-1759723584644.png|200]]

Take $\{U_\alpha\}$ the smallest collection of open arcs in $S^1$ that cover $S^1$. Then $p^{-1}(U_\alpha)$ is a disjoint union of collection of open intervals in $\mathbb{R}$, with restriction of $p$ to each such interval being a homeomorphism to $U_\alpha$.

2. $X=S^1$, $\widetilde{X} = S^1$ both $\{z \in \mathbb{C}\:|\: |z| = 1\}$. Define $p_n: \widetilde{X}\to X$ by $z \mapsto z^n$ i.e. $p_n(e^{i\theta}) = e^{in\theta}$. i.e. $p_n$ wraps $S^1$ around itself $n$-times. 
   ![[Covering Space-1759726596906.png|300]]
3. $X = S^1 \vee S^1$ 
   ![[Covering Space-1759726695434.png|400]]
    are all covering spaces of $X$. And so is this infinite Cayley graph of $F(a,b)$ 
   ![[Covering Space-1759726810707.png|200]]


# Lifting Properties

>[!def] Lift
>$p: \widetilde{X} \to X$ a cover of $X.$ Let $f:Y \to X$ be a continuous map. A **lift** of $f$ is a continuous map $\widetilde{f}: Y \to \widetilde{X}$ such that $p \circ \widetilde{f}= f$. i.e. TFDC
>![[Covering Space-1759736222346.png|160]]
>

>[!proposition]
>$p$ a covering map. Let $F: Y \times I \to X$ be a homotopy with $F(y,t) = f_t(y).$ 
>Then for every lift $\widetilde{f}_0$ of $f_0$ there exists a <span style="color:rgb(146, 208, 80)">unique</span> homotopy $\widetilde{F}: Y \times I \to \widetilde{X}$ such that $\widetilde{F}(y,t)=\widetilde{f}_t(y)$ a lift of $f_t$.
>
##### Proof
Note that $F|_{Y \times \{0\}} = f_0(y)$.
*we show:* There is a unique continuous $\widetilde{F}$ such that $F|_{Y \times \{0\}} = f_0(y)$, and $\widetilde{F}$ lifts $F$. i.e.
![[Covering Space-1759737524546.png|200]]
commutes.

Let $\{U_\alpha\}$ be an open cover of $X$ such that $p^{-1}(U_\alpha)$ is a disjoint union of open subsets of $\widetilde{X}$, each mapped homeomorphically onto $U_\alpha$ by $p$ for each $\alpha.$ 

For each $(y,t) \in Y \times I$, $F(y,t)\in U_\alpha$ for some $\alpha$, so $(y,t) \in F^{-1}(U_\alpha)$. Since $F$ is continuous, $F^{-1}(U_\alpha)$ is open so there exists an open rectangle $N_{y,t} \times V_{y,t} \subseteq F^{-1}(U_\alpha)$ containing $(y,t)$, and thus $F(N_{y,t} \times V_{y,t})\subseteq U_\alpha$. WLoG assume $F(N_{y,t} \times \overline{V}_{y,t})\subseteq U_\alpha$ as well.

Fix $y_0 \in Y$. Then $\{y_0\}\times I$ is compact, so finitely many of $N_{y,t}\times V_{y,t}$ cover $\{y_0\}\times I$. 

We can show that there exists a neighbourhood of $y_0$ in $Y$ and a partition $0=t_0<t_1<...<t_{m-1}<t_m =1$ of $I$ such that for $0 \leq i \leq m$, there exists $U_i = U_{\alpha_i}$ such that $F(N \times [t_i,t_{i+1}]) \subseteq U_i$.  We can induct on $i$ to construct $\widetilde{F}$ on $N \times I$.

*Base case:* $i=0$, put $\widetilde{F}|_{N \times \{0\}} = \widetilde{f}_0|_N$.
*Inductive assumption:* Assume we have constructed $\widetilde{F}$ on $N \times [0,t_i]$. Now there exists an open $\widetilde{U}_i \subseteq \widetilde{X}$ such that $p|_{\widetilde{U}_i}$ is a homeomorphism onto $U_i$, and $\widetilde{U}_i$ contains $\widetilde{F}(y_0,t_i)$. We may assume $\widetilde{U}_i$ contains $\widetilde{F}(N \times \{t_i\})$.

Now define $\widetilde{F}|_{N\times [t_i,t_{i+1}]} = (p|_{U_i})^{-1} \circ F|_{N \times [t_i,t_{i+1}]}$. Then TFDC:
![[Covering Space-1759739264000.png|400]]After finitely many repetitions, get lift $\widetilde{F}: N \times I\to \widetilde{X}$ for some neighbourhood of $y$.


*Uniqueness:* First consider the special case $Y = \{y_0\}$. i.e. $F:\{y_0\}\times I \to X$. Suppressing $Y$ from notation, then $F:I \to X$ is a path in $X$.

Suppose $\widetilde{F}:I \to \widetilde{X}$, $\widetilde{F}':I \to \widetilde{X}$ are lifts of $F:I \to X$ such that $\widetilde{F}(0) = \widetilde{F}'(0)$. Consider partition $0=t_0<t_1<...<t_m = 1$ such that for all $0\leq i\leq m$, $F([t_i,t_{i+1}])\subseteq U_i$. 
Assume inductively that $\widetilde{F}=\widetilde{F}'$ on $[0,t_i]$. Since $[t_i,t_{i+1}]$ is connected and $\widetilde{F},\widetilde{F}'$ are continuous and $\widetilde{F}([t_i,t_{i+1}])$ and $\widetilde{F}'([t_i,t_{i+1}])$ are each contained in a single open set from the disjoint union $$