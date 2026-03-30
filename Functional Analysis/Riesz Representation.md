The dual $\mathcal{H}'$ of a Hilbert space can be explicitly described, without needing Hahn-Banach or Axiom of Choice. The Key point is that the inner product already gives lots of continuous linear functionals.

# Riesz Representation Theorem

>[!Lemma]
>$\mathcal{H}$ a Hilbert Space. For each $y \in \mathcal{H}$, the function $\varphi_y: \mathcal{H} \to \mathbb{K}$, given by $x \mapsto \langle x,y \rangle$ is a continuous linear functional $(\varphi_y \in \mathcal{H}')$ with $\|\varphi_y\| = \|y\|$.
##### Proof
$$|\varphi_y(x)| = |\langle x,y \rangle | \overset{C.S}{\leq} \|x\|\|y\|$$
so $\varphi_y \in \mathcal{H}$ with $\|\varphi_y\| \leq \|y\|$. But also $\varphi_y(y) = \langle y,y \rangle = \|y\|\|y\|$. So $\|\varphi_y\| = \|y\|$. $\square$


>[!Theorem]
>$\mathcal{H}$ a Hilbert space. The map $\Theta:\mathcal{H} \to \mathcal{H}'$ given by $y \mapsto \varphi(y) := \langle x,y\rangle$ is
>1. Isometric
>2. Conjugate linear
>3. Bijective
>   
>In particular, $\mathcal{H}' = \{\varphi_y \:|\: y \in \mathcal{H}'\}$
##### Proof
###### Conjugate-Linearity
This follows from conjugate linearity of inner product w.r.t the second input $\langle x,-\rangle$.
###### Isometry
$|\varphi_y(y)| = |\langle y,y \rangle|= \|y\|^2 = \|y\| \|y\| \implies \|y\|$ using the lemma, then $\|\varphi_y\| = \|y\|$.
###### Injectivity
Follows from the fact that the map is an isometry.
###### Surjectivity
Let $\varphi \in \mathcal{H}'$
If $\varphi \equiv 0$, then for $y=0$, $\varphi_y(x) = 0 = \varphi(x)$.
Assume $\varphi \not\equiv 0$. Then $\exists z \in \mathcal{H}$ such that $\varphi (z) \neq 0$. 
Let $M = \ker \varphi \leq \mathcal{H}$ which is closed, since $\varphi$ is continuous and $\ker \varphi = \varphi^{-1}(\{0\})$. i.e. preimage of a closed set.
If $M \subset \mathcal{H}$ is a proper closed subspace, then $M^\perp \neq \{0\}$.
Let $0 \neq z \in M^{\perp} \implies \varphi(z) \neq 0$ since $z \not\in \mathcal{M} = \ker \varphi$.

Now for each $x \in \mathcal{H}$, consider $x - \frac{\varphi(x)}{\varphi(z)}z \in \ker \varphi = M$. Hence 
$$\begin{align*}
0 &= \left \langle x - \frac{\varphi(x)}{\varphi(z)}z, z \right \rangle \\
&= \langle x,z \rangle - \frac{\varphi(x)}{\varphi(z)} \|z\|^2 \\
\implies \varphi(x) &= \frac{\varphi(z)}{\|z\|^2}\langle x,z \rangle = \left \langle x, \underbrace{\frac{\overline{\varphi}(z)}{\|z\|^2}z}_{=: y} \right \rangle
\end{align*}$$
and thus $\varphi = \varphi_y$. $\square$

