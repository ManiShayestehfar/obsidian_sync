# Free Product

>[!def] Free product
>Let $\{G_i \:|\: i \in I\}$ bet a collection of groups. Let $G$ be a group, and for each $i \in I$, let $\varphi_i: G_i \to G$ be a homomorphism.
>Say $G$ is the **free product** of $G_i$ w.r.t. $\varphi_i$ if for any group $H$ and for any collection of homs. $\psi_i:G_i \to H$, there exists a *unique* homom. $f:G \to H$ such that $\forall i \in I$  TFDC:
>
>![[Free Product of Groups-1758979777566.png|200]]

- Denote this by $G = \ast_{i \in I} G_i$
- Uniqueness follows from the same proof as [[Free Product of Groups]]


# Word

>[!def] Word
>A **word** in groups $G_i$ is a finite sequence $(x_1,...,x_n)$ such that
>1. each $x_i$ is a nontrivial elements of some $G_j$
>2. $x_i,x_{i+1}$ belong to distinct $G_j$
>- A word is **empty** if the sequence is $()$.

>[!def] Actions on words
>$W$ the set of all words in $G_i$. We define an action of each $G_i$ on $W_i$. Let $g \in G_i$. Then:
>1. If $g=1,\quad g\cdot(x_1,...,x_n)= (x_1,...,x_n)$ and $g\cdot() = ()$
>2. If $g\neq 1,\quad g\cdot () = (g)$
>3. If $g \neq 1, \quad x_1\not\in G_i,$ then $g\cdot(x_1,...,x_n) = (g_,x_1,...,x_n)$
>4. If $g \neq 1,\quad x_1 \in G_i$, then $g\cdot(x_1,...,x_n) = (gx_1,...,x_n)$
>5. If $g \neq 1$, and $x_1 = g^{-1} \in G_i$, then $g\cdot(x_1,...,x_n) = (x_2,...,x_n)$ 

