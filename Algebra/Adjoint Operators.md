Recall, the adjoint of an $n\times n$ matrix $A$ over $\mathbb{K}$ is: $A^* = \overline{A^T}$ 
In terms of the inner product on $\mathbb{K}^n$, the adjoint relation is $$\langle Ax, y \rangle= \langle x, A^*y \rangle \qquad \forall x,y \in \mathbb{K}^n$$

>[!Theorem]
>Let $\mathcal{H}_1, \mathcal{H}_2$ be Hilbert spaces and $T \in \mathcal{L}(\mathcal{H}_1, \mathcal{H}_2)$. Then the equation $$\langle Tx, y \rangle_2 = \langle x, T^* y \rangle_1 \qquad \forall \:x\in \mathcal{H_1}, y \in \mathcal{H}_2$$
>defines a unique continuous linear operator $T^* \in \mathcal{L}(\mathcal{H}_2, \mathcal{H}_1)$ called the **adjoint**. 
>Moreover: 
>1. $\|T^*\| = \|T\|$,
>2. $\|T^*T\| = \|T\|^2$
>3. $(T\circ S)^* = S^*\circ T^*$ 
##### Proof
Let $y \in \mathcal{H}_2$ and $\varphi \in \mathcal{H}_1^*$ by $\varphi(x) := \langle Tx, y \rangle_2$ $\forall x \in \mathcal{H}_1$.
Since $|\varphi(x)|= |\langle Tx, y \rangle_2| \overset{C.S}{\leq} \|Tx\|\|y\| \leq \|T\|\|x\|\|y\|$, the $\varphi \in \mathcal{H}_1'$.

So by Riesz's Theorem, $\exists !$ $T^*y \in \mathcal{H}_1$ such that $\varphi(x) = \langle x, T^* y \rangle_1$ $\forall x \in \mathcal{H}_1$.