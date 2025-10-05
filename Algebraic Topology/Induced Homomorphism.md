**Notation:** If $x_0\in X, y_0 \in Y$, then for $\varphi:X \to Y$ with $\varphi(x_0) = y_0$, write $\varphi: (X,x_0) \to (Y,y_0)$.

>[!lemma] 
>Any continuous map $\varphi:(X,x_0)\to (Y,y_0)$ induces a homomorphism $\varphi_*:\pi_1(X,x_0) \to \pi_1(Y,y_0)$ given by $\varphi_*([f]) = [\varphi \circ f]$.
>If $\varphi$ is already a homeomorphism then $\varphi_*$ is an isomorphism.
##### Proof

*Well-defined:* If $f_t$ is a homotopy of loops based at $x_0$ in $X$, then $\varphi \circ f_t$ is a homotopy of loops based at $y_0$ in $Y$. So $\varphi_*([f_0]) = [\varphi \circ f_0] = [\varphi \circ f_1] = \varphi_*([f_1])$.

*Homomorphism:* $\varphi \circ(f\cdot g) = (\varphi \circ f) \cdot (\varphi \circ g)$ from the definition of composition of paths. So $$\begin{align*}
\varphi_*([f][g]) &= \varphi_*([f\cdot g]) \\
&= [\varphi \circ (f \cdot g) ] \\
&= [(\varphi \circ f) \cdot (\varphi \circ g)] \\
&= [\varphi \circ f][\varphi \circ g] \\
&= \varphi_*([f])\varphi_*([g])
\end{align*}$$
*Isomorphism from Homeo:* If $\varphi$ is a homeomorphism, then $\exists\: \varphi^{-1}:Y \to X$ that is continuous.
Consider two compositions $\varphi^{-1} \circ\varphi = \text{id}_X$, and $\varphi \circ\varphi^{-1}= \text{id}_Y$. Then the induced homomorphism
$$\begin{align*}
(\varphi^{-1}\circ \varphi)_* &= (\varphi^{-1})_* \circ\varphi_* = (\text{id}_X)_* = \text{id}_{\pi_1(X,x_0)} \\
(\varphi\circ \varphi^{-1})_* &= \varphi_* \circ (\varphi^{-1})_* = (\text{id}_Y)_* = \text{id}_{\pi_1(Y,y_0)}
\end{align*}$$
tell us that $(\varphi^{-1})_*$ is the two-sided inverse to $\varphi_*$. Hence $$(\varphi^{-1})_* = (\varphi_*)^{-1}$$ and so $\varphi$ is an isomorphism.  $\square$




