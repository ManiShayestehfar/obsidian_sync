If $W$ is a [[FG-Module|submodule]] of $V$, then we can form a **quotient module** 
$$V/W =\{v+W\:|\:v\in V\}$$
where $v \sim w \iff w-v \in W$ for any $v,w \in V$. 

- We know that $V/W$ is a [[vector space]], but is also a [[FG-Module|G-Module]].

> [!proposition]
> ![[Pasted image 20250306225042.png]]

![[Pasted image 20250306225314.png]]

# First Isomorphism Theorem

Suppose $\varphi: V\to W$ is a $G$-module homomorphism. Then 
$$V / \ker \varphi \cong \text{im }\varphi$$
as $G$-modules.

![[Screenshot 2025-03-07 at 12.58.28 pm.png]]

# Other Isomorphism Theorems
Let $V$ be a $G$-module

2. . Suppose $X$ and $Y$ are submodules of $V$ $\implies (X+Y)/Y \:\cong\: X/(X\cap Y)$ 
3. Suppose $U \leq W \leq V$ are submodules of $V$ $\implies V/W \:\cong\: (V/U)/(W/U)$
4. Suppose $W$ is a submodule of $V$. Then there is a 1-to-1 inclusion preserving correspondence between submodules of $V$ that contain $W$ and the submodules of $V/W$
##### Proof Sketch
###### 2. 
Recap: If $X$ and $Y$ are subspaces of $V$, then $X+Y = \{x + y \:|\: x \in X, y \in Y\}\subseteq V$. 
If we take $x \in X$ and $y \in Y$, then $g(x+y) = gx+gy \in X+Y$ so $X+Y$ is a $G$-submodule of $V$.

Define $\Psi:Y\to (X+Y)/X$  by $\Psi(y) = y+X \in (X+Y)/X$.
By the first isomorphism theorem, $Y/\ker \Psi \cong \text{im }\Psi = (X+Y)/X$ and $\ker \Psi = \{y \in Y \:|\: y + X = 0_{(X+Y)/Y}\} = X \cap Y$ since $y + X = 0 + X \iff y \in X$. $\square$

###### 3.
Define $\Theta: V \to (V/X)/(Y/X)$ by $\Theta(v)= (v+X) + Y/X$ which we can check to be well-defined.
By first isomorphism theorem, $V/\ker \Theta \cong \text{im }\Theta = (V/X)/(Y/X)$ and $\ker \theta = \{v \in V \:|\: v \in Y\} = V \cap Y = Y$. 
Therefore $V/Y \cong (V/X)/(Y/X)$. $\square$

###### 4.
We have a natural map $\pi: V \to V/U$ given by $\pi(v) = v+ U$. 
$\text{im }\pi = V/U$ and $\ker \pi = U$. 
If $W$ is a $G$-submodule of $V$ that contains $U$, then $W/U = \pi(W)$ is a $G$-submodule of $V/U$.

Conversely if $\mathcal{W}$ is a $G$-submodule of $V/U$ then $W = \pi^{-1}(\mathcal{W}) = \{v \in V \:| \pi (v) \in \mathcal{W}\}$ 
is a vector subspace of $V$ (since $\pi$ is linear).
$U \subseteq W$ because if $u \in U$, then $\pi(u) = u + U = 0_{V/U} \in \mathcal{W}$.
Moreover, $W$ is a $G$-submodule because if $g \in G$ and $w \in W$, then $\pi(gw) = g\pi(w) \in \mathcal{W}$ since $\mathcal{W}$ is a $G$-module. 
$\implies gw \in W \implies W$ is a $G$-submodule of $V$ containing $U$. $\square$



