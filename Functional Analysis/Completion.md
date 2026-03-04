# Motivation

>[!Warning]
>Not all metric spaces are complete. 
>e.g. $(\mathcal{P}([a,b]), \|\cdot\|_\infty)$, $(\ell_F, \|\cdot\|_p)$ for $1 \leq p < \infty$
>

The idea behind completion is that we may have
$(X, \|\cdot\|) \overset{Densely}{\subset} (\hat{X}, \|\cdot\|_1)$, then there exists $\varphi: X \to \hat{X}$ which is an "isometric embedding".
where $\varphi$ is 
1. linear
2. injective
3. *NOT* necessarily surjective
4. $\overline{\text{im }\varphi} = X$ 

Up to isometric isomorphism such $(\hat{X}, \|\cdot\|)$ is *unique*.

# Definition

>[!Definition]
>Let $(X,\|\cdot\|_p)$ be a normed vector space. There is a Banach space $(\hat{X}, \|\cdot\|_1)$ such that $(X, \|\cdot\|)$ is isometrically isomorphic to a *dense* subspace of $(X,\|\cdot\|_1)$. This is called the **completion** of $X$.
>
>Moreover, $(\hat{X}, \|\cdot\|_1)$ is unique up to isometric isomorphism.

## Examples

Let $1 < p \leq \infty$, then $\widehat{(\ell_F, \|\cdot\|_p)} = (\ell^p, \|\cdot\|_p)$ where we recall that $\ell_F$ was the set of sequences with finite support

##### Proof
Take $\varphi: (\ell_F, \|\cdot\|_p) \to (\ell^p, \|\cdot\|_p)$ given by the identity map.
This is clearly an isometric embedding since the norms are the same.

We need to prove $\bar{\ell_F} = \ell^p$.
Take any $x := (x_1,x_2,...,x_n,...) \in \ell^p$, and $y_n = (x_1,x_2,...,x_n,0,0,...) \in \ell_F$ 

clearly $\|x-y\|_p^p = \sum_{k=n+1}^\infty |x_k| \to 0$ as $n \to \infty$. So $y_n \to x \in \ell^p$.
$\therefore \bar{\ell_F} = \ell^p$ 

**Question:** How about the completion of $(\ell_F, \|\cdot\|_\infty)$? Is it $\ell^\infty$?
Take $\mathbb{1} := (1,1,...)\in \ell^\infty$, then $\text{dist}_{\|\cdot\|_\infty}(\mathbb{1}, \ell_F) = \inf_{y \in \ell^\infty}\|\ \mathbb{1} - y\:\|_\infty = 1$. 
Hence $\mathbb{1}$ is far from all elements of $\ell_F$. 
Therefore the completion is **NOT** $\ell^\infty$.

Now take $x = (x_k) \subset \ell^\infty$ satisfying $|x_k| \to 0$ by assumption.
Let $x^{(n)} = (x_1,x_2,...,x_n,0,0,...)\in \ell_F$.
Then $\|x^{(n)} - x\|_\infty = \sup_{k \geq n+1} |x_k| \to 0 \implies x^{(n)} \to x$ .
Therefore $\widehat(\ell_F, \|\cdot\|_\infty) = (c_0, \|\cdot\|_\infty)$ where as a reminder $c_0 = \{(x_n) \in \ell^\infty \:|\: |x_k| \to 0\}$ 