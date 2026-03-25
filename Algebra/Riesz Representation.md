The dual $\mathcal{H}'$ of a Hilbert space can be explicitly described, without needing Hahn-Banach or Axiom of Choice. The Key point is that the inner product already gives lots of continuous linear functionals.

# Riesz Representation Theorem

>[!Lemma]
>$\mathcal{H}$ a Hilbert Space. For each $y \in \mathcal{H}$, the function $\varphi_y: \mathcal{H} \to \mathbb{K}$, given by $x \mapsto \langle x,y \rangle$ is a continuous linear functional $(\varphi_y \in \mathcal{H}')$ with $\|\varphi_y\| = \|y\|$.
##### Proof
$$|\varphi_y(x)| = |\langle x,y \rangle | \overset{C.S}{\leq} \|x\|\|y\|$$
so $\varphi_y \in \mathcal{H}$ with $\|\varphi_y\| \leq \|y\|$. But also $\varphi_y(y) = \langle y,y \rangle = \|y\|\|y\|$. So $\|\varphi_y\| = \|y\|$. $\square$


>[!Theorem]
>$\mathcal{H}$ a Hilbert space. The map $\Theta:\mathcal{H} \to \mathcal{H}'$ given by $y \mapsto \varphi(y) := \langle x,y\rangle$ is
>1. isometric
>2. Conjugate linear
>3. Bijective
>   
>In particular, $\mathcal{H}' = \{\varphi_y \:|\: y \in \mathcal{H}'\}$
##### Proof
###### Conjugate-Linearity
This follows from 