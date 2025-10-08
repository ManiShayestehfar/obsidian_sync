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


## Examples

1. $\mathbb{Z} = \langle a \:|\: -\rangle$. Then $\Gamma(\mathbb{Z}, \{a\})$ is 
   
   ![[Screenshot 2025-10-09 at 8.32.51 am.png|400]]
   
2. $F(a,b)= \langle a,b\:|\: -\rangle$. Then $\Gamma(F(a,b), \{a,b\})$ is
   
   ![[Screenshot 2025-10-09 at 8.34.32 am.png|400]]
   
3. $\mathbb{Z}^2 = \langle a,b\:|\: aba^{-1}b^{-1}\rangle$. The Cayley graph is 
   
   ![[Screenshot 2025-10-09 at 8.36.27 am.png|300]]
   
4. $\mathbb{Z}/2\mathbb{Z} = \langle a | a^2 =1\rangle$. The Cayley graph is
   
   ![[Screenshot 2025-10-09 at 8.39.26 am.png|300]]
   

## Properties of Cayley Graphs

1. At each vertex, degree in = degree out = $|S|$
2. $\Gamma(G,S)$ is path-connected as every $g \in G$ is a product of elements of $S\cup S^{-1}$
3. If $w = s_{i_1}s_{i_2}...s_{i_k}$ is a word in $S \cup S^{-1}$ such that $w = 1$ in $G$, then any edge path $(g, gs_{i_1}, gs_{i_1}s_{i_2},...,gw)$ is a *loop* in $\Gamma(G,S)$.
	- In particular, all relators give loops in $\Gamma(G,S)$.


# Cayley Complex

>[!def]
>For $G = \langle S|R\rangle$, the **Cayley Complex** $X_G$ is 
>- 2D cell-complex with 1-skeleton the Cayley graph $\Gamma(G,S)$, and 
>- for every $r \in R$, a 2-cell attached to each loop in $\Gamma(G,S)$ with edges labelled as $r$.
>i.e. one 2-cell for each $(g,r)\in G \times R$.


## Examples

1. $\mathbb{Z}= \langle a | -\rangle$ and $F(a,b) = \langle a,b|-\rangle$ then $X_G = \Gamma(G,S)$ as there are no relators.
2. For $\mathbb{Z}^2$ 
   ![[Screenshot 2025-10-09 at 8.49.29 am.png|500]]
3. For $\mathbb{Z}/2\mathbb{Z}$ 
   ![[Screenshot 2025-10-09 at 8.50.19 am.png|400]]

## Propositions

>[!proposition]
>$\widetilde{X}_G$ is simply-connected and therefore a universal cover of $X_G$
##### Proof

Since $\Gamma(G,S)$ is path-connected, then so it $\widetilde{X}_G$. We give a sketch proof of why $\pi_1(\widetilde{X}_G)\cong 1$. 

Let $[f]\in \pi_1(\widetilde{X}_G)$. Homotope $f$ to lie in the 1-skeleton, $\Gamma(G,S)$. So $f$ gets labeled with the trivial word $w$ in $G$. i.e. $\Pi_{i=1}^k g_ir_ig_i^{-1}$.  Consider the loop labelled $f_i = g_ir_ig_i^{-1}$ in $\Gamma(G,S)$. Then $[f_i]= 1$ in $\pi_1(\widetilde{X}_G)$ because of the 2-cell for $r_i$ and $g_i$. Since $f = f_1\cdot f_2 \cdot ... \cdot f_k$ then we get $[f]=1$ in $\pi_1(\widetilde{X}_G)$.  $\square$ 

![[Screenshot 2025-10-09 at 8.58.17 am.png|300]]



# $K(G,1)$ Spaces

>[!def] 
>Let $G$ be a group. The **$K(G,1)$ Space** is a path-connected space $X$ such that 
>- $\pi_1(X)=G$  
>- $X$ has a contractible universal cover

![[Screenshot 2025-10-09 at 9.05.14 am.png|400]]