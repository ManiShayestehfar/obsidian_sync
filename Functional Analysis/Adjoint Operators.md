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
###### Existence
Fix $y\in \mathcal H_2$. Define $\varphi_y:\mathcal H_1\to K$ by $\varphi_y(x):=\langle Tx,y\rangle_2.$ (NOT NECESSARILY BOUNDED)
Since
$$
|\varphi_y(x)|
=
|\langle Tx,y\rangle_2|
\overset{C.S}{\leq}
\|Tx\|\,\|y\|
\leq
\|T\|\,\|x\|\,\|y\|,
$$
$\varphi_y$ is a bounded linear functional on $\mathcal H_1$.

By the Riesz Representation Theorem, there exists a unique vector $T^*y\in \mathcal H_1$ such that
$$
\varphi_y(x)
=
\langle x,T^*y\rangle_1
\qquad \forall x\in\mathcal H_1.
$$
Hence $\langle Tx,y\rangle_2 = \langle x,T^*y\rangle_1 \qquad \forall x\in\mathcal H_1,\; y\in\mathcal H_2$.

###### Linearity of $T^*$
Let $y_1,y_2\in\mathcal H_2$. Then for every $x\in\mathcal H_1$,
$$
\begin{aligned}
\langle x,T^*(y_1+y_2)\rangle_1
&=
\langle Tx,y_1+y_2\rangle_2 \\
&=
\langle Tx,y_1\rangle_2+\langle Tx,y_2\rangle_2 \\
&=
\langle x,T^*y_1\rangle_1+\langle x,T^*y_2\rangle_1 \\
&=
\langle x,T^*y_1+T^*y_2\rangle_1.
\end{aligned}
$$
By uniqueness in the Riesz Representation Theorem, $T^*(y_1+y_2)=T^*y_1+T^*y_2$.
Similarly, for $\lambda\in K$,
$$
\langle x,T^*(\lambda y)\rangle_1
=
\langle Tx,\lambda y\rangle_2
=
\lambda \langle Tx,y\rangle_2
=
\langle x,\lambda T^*y\rangle_1,
$$
so $T^*(\lambda y)=\lambda T^*y$.
Therefore $T^*$ is linear.

###### Uniqueness of $T^*$
Suppose $A,B\in\mathcal L(\mathcal H_2,\mathcal H_1)$ both satisfy $\langle Tx,y\rangle_2 = \langle x,Ay\rangle_1 = \langle x,By\rangle_1$ for all $x\in\mathcal H_1$ and $y\in\mathcal H_2$.
Then $\langle x,Ay-By\rangle_1=0 \qquad \forall x\in\mathcal H_1.$

Taking $x=Ay-By$ gives $\|Ay-By\|^2=0,$ hence $Ay=By$.
Since this holds for every $y\in\mathcal H_2$, we conclude that $A=B$. Thus $T^*$ is unique.

###### Continuity and Norm Equality
For $y\in\mathcal H_2$,
$$
\|T^*y\|^2
=
\langle T^*y,T^*y\rangle_1
=
\langle TT^*y,y\rangle_2
\overset{C.S}{\leq}
\|TT^*y\|\,\|y\|
\leq
\|T\|\,\|T^*y\|\,\|y\|.
$$
If $T^*y\neq 0$, dividing by $\|T^*y\|$ yields $\|T^*y\| \leq \|T\|\,\|y\|$.
Hence $T^*$ is bounded and $\|T^*\|\leq \|T\|$.

Conversely, for $x\in\mathcal H_1$,
$$
\|Tx\|^2
=
\langle Tx,Tx\rangle_2
=
\langle x,T^*Tx\rangle_1
\overset{C.S}{\leq}
\|x\|\,\|T^*Tx\|
\leq
\|x\|\,\|T^*\|\,\|Tx\|.
$$
If $Tx\neq 0$, dividing by $\|Tx\|$ gives $\|Tx\| \leq \|T^*\|\,\|x\|$.
Therefore $\|T\| \leq \|T^*\|$.

Combining the two inequalities gives $\|T^*\|=\|T\|$.

###### Proof that $\|T^*T\|=\|T\|^2$
Since operator norms are submultiplicative,
$$
\|T^*T\|
\leq
\|T^*\|\,\|T\|
=
\|T\|^2.
$$
On the other hand,
$$
\|Tx\|^2
=
\langle x,T^*Tx\rangle_1
\overset{C.S}{\leq}
\|x\|\,\|T^*Tx\|
\leq
\|T^*T\|\,\|x\|^2.
$$
Hence
$$
\frac{\|Tx\|^2}{\|x\|^2}
\leq
\|T^*T\|
\qquad (x\neq 0).
$$
Taking the supremum over all non-zero $x$ gives $\|T\|^2 \leq \|T^*T\|$.
Therefore $\|T^*T\|=\|T\|^2$.

###### Proof that $(T\circ S)^*=S^*\circ T^*$
Let $S\in\mathcal L(\mathcal H_0,\mathcal H_1)$ and $T\in\mathcal L(\mathcal H_1,\mathcal H_2)$.
For $x\in\mathcal H_0$ and $y\in\mathcal H_2$,
$$
\begin{aligned}
\langle (T\circ S)x,y\rangle_2
&=
\langle T(Sx),y\rangle_2 \\
&=
\langle Sx,T^*y\rangle_1 \\
&=
\langle x,S^*(T^*y)\rangle_0 \\
&=
\langle x,(S^*\circ T^*)y\rangle_0.
\end{aligned}
$$
By uniqueness of the adjoint, $(T\circ S)^*=S^*\circ T^*$.
$\square$
