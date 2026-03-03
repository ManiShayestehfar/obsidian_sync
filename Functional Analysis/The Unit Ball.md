Let $(X,\|\cdot\|)$ be a [[Normed Spaces|normed vector space]] over $\mathbb{K}$.
Closed ball: $\bar{B}(0,1) = \{x \in X \:|\: \|x\| < 1\}$.

>[!Theorem]
>$\dim X < \infty \iff \bar{B}(0,1)$ is compact.
##### Proof
###### $(\Rightarrow)$ 
Using generalised Heine-Borel Theorem, $\bar{B}$ is bounded and closed and therefore it is compact.

###### $(\Leftarrow)$

>[!Lemma] Riesz's Lemma
>$(X,\|\cdot\|)$ a normed vector space. Let $Y \subsetneq X$ be *closed*. Then:
>$\forall 0<\theta<1$, $\exists x \in X$ with $\|x\|=1$ with $\text{dist}(x,Y) = \inf_{y \in Y}\|x-y\| \geq \theta$
>![[desmos-graph (3).png|250]]


>

>

