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
Let $y \in \mathcal{H}_2$ and $\varphi \in \mathcal{H}_1^*$ given by $\varphi(x) := \langle Tx, y \rangle_2$ $\forall x \in \mathcal{H}_1$.
Since $|\varphi(x)|= |\langle Tx, y \rangle_2| \overset{C.S}{\leq} \|Tx\|\|y\| \leq \|T\|\|x\|\|y\|$, then $\varphi \in \mathcal{H}_1'$.

So by the Riesz Representation Theorem, $\exists !$ $T^*y \in \mathcal{H}_1$ such that $\varphi(x) = \langle x, T^* y \rangle_1$ $\forall x \in \mathcal{H}_1$.

###### Linearity of $T^*$ 
Let $y_1,y_2 \in \mathcal{H_2}$ and define $\varphi_i(x) := \langle Tx, y_i \rangle_2 = \langle x, T^* y_i \rangle_1$ 
Then $\varphi_1(x) + \varphi_2(x) = \langle Tx, y_1 + y_2 \rangle_2 = \langle x, T^*(y_1+y_2)\rangle_1 = \langle x, T^* y_1 + T^* y_2 \rangle_1$
$\implies T^*(y_1 +y_2) = T^* y_1 + T^* y_2$.  $\therefore$ linear

###### Uniqueness of $T^*$
If $\exists T^*, W^*$ satisfying $\langle Ax, y \rangle_2 = \langle x, A^*y \rangle_1$ for $A = T^*, W^*$,
Suppose $\exists y \in \mathcal{H}_2$ such that $T^* y = W^* y$.
Then $\forall x \in H_1$: $\langle x, T^* y \rangle_1 = \langle x, W^* y \rangle_1$.  By Isometry in Riesz's Theorem, $T^* = W^*$ which is a contradiction. Hence $T^*$ must be unique.

###### Continuity of $T^*$

$\|T^* y\|^2 = \langle T^* y, T^* y \rangle_1 = \langle T T^* y, y \rangle_2 \le \|T T^* y\| \, \|y\| \le \|T\| \, \|T^* y\| \, \|y\| \quad (\text{since } T \text{ is continuous})$
$\implies \|T^* y\| \le \|T\| \, \|y\|$
$\implies T^* \text{ is continuous and } \|T^*\| \le \|T\|$.

Similarly
$\|T x\|^2 = \langle T x, T x \rangle_2 = \langle x, T^* T x \rangle_1 \le \|x\| \, \|T^* T x\| \le \|x\| \, \|T^*\| \, \|T x\| \quad (\text{as } T^* \text{ is continuous})$
$\implies \|T x\| \le \|T^*\| \, \|x\| \quad \implies \quad \|T\| \le \|T^*\|$

$\therefore \|T\| = \|T^*\|$

Now
$\|T^* T x\| \le \|T^*\| \, \|T\| \, \|x\| = \|T\|^2 \, \|x\|$
$\implies \|T^* T\| \le \|T\|^2$

But we showed that 
$\|T x\|^2 \le \|T^* T x\| \, \|x\| \le \|T^* T\| \, \|x\|^2$
$\implies \|T\|^2 \le \|T^* T\|$

$\therefore \|T^* T\| = \|T\|^2$
$\square$

