Given a presentation $G=\langle S|R\rangle$ we can construct a 2D cell complex $X_\alpha$ with $\pi_1(X_G)\cong G$ by 
- one vertex $X_G^0=\{v\}$, $X_G^1=\bigvee_{S_\alpha\in S} S_\alpha^1$  (a bouquet of circles)
- Attach a 2-cell $e_r^2$ for each relator $r \in R$.

e.g. $G =\langle a,b\:|\:aba^{-1}b^{-1}\rangle \cong \mathbb{Z}^2$, then

![[Cayley Graphs-1759926332743.png|350]]

# Cayley Graph

>[!def]
>The **Cayley Graph** of $G$ w.r.t a generating set $S$, denoted $\Gamma(G,S)$ is the directed graph with 
>- vertex set $G$
>- and edge $g \longrightarrow gs$  for all $g \in G$ and $s \in S$.


