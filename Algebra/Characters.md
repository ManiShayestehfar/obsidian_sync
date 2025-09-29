>[!def] Character
>$V$ a $\mathbb{C}G$-module and fix basis $\{e_1,...,e_n\}$ of $V$. For each element $g$ of $G$, let $\mathbf{g} = (g_{ij})$ be the matrix given by $g e_j = \sum_{i=1}^n g_{ij} e_i$. 
>The **character** $\chi_V$ of $V$ is the map $\chi_V: G \to \mathbb{C}$ given by $\chi(V) = \textrm{tr}(\mathbf{g}) = \sum_{i=1}^n g_{ii}$.
>

>[!proposition]
>Let $V,W$ be $\mathbb{C}G$-modules and $\chi_V,\chi_W$ their characters. Then
>1. $\chi_V$ is independent of the choice of basis
>2. $\chi_V(1) = \dim V$ 
>3. If $g,h$ are conjugate in $G$, then $\chi_V(g)=\chi_V(h)$
>4. $V \cong W \iff \chi_V = \chi_W$
>5. $\chi_{V \oplus W} = \chi_V + \chi_W$ 

>[!def] Inner product
>![[Screenshot 2025-09-28 at 10.50.10 pm.png]]
- This is not Hermitian, i.e.e $\langle u,v \rangle \neq \overline{\langle u,v\rangle}$ so this is not really an inner product in the usual sense.
