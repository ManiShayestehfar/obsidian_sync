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
Recap: If $X$ and $Y$ are subspaces of $V$, then $X+Y = \{x + y \:|\: x \in X, y \in Y\}\subseteq V$  

