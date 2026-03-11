# Definition

>[!Definition]
>Let $X$ be a normed vector space. Then its **Dual** is defined as:
>$X' := \mathcal{L}(X, \mathbb{K})$, also
>$X^* := \text{Hom}(X, \mathbb{K})$

## Example

>[!Example]
>If $\dim X < \infty$, then $X^* = X'$.
##### Proof
Take $\varphi \in X^*$. Let $e_1,e_2,...,e_n$ be a basis for $X$. Then $\varphi\left(\sum_{i=1}^n x_ie_i\right)= \sum_{i=1}^nx_i \varphi(e_i)$
We know that $$\|\varphi(x)\| = \left|\sum_{i=1}^n x\varphi(e_i)\right|\leq \sum_{i=1}^n|x_i|\cdot \underbrace{\max_{1\leq i\leq n} |\varphi(e_i)|}_{=:M} = M \sum_{i=1}^n|x_i| \leq MC\|x\|$$
by equivalence of norms on $\mathbb{K}^n$ since $\left\|\sum_{i=1}^n x_ie_i\right\| := \sum_{i=1}^n|x_i|$ is a norm on $X$.  
$\therefore \varphi \in X'$.

The other direction is obvious.

Also, take $\varphi(x) = \varphi_a(x)= \sum_{i}x_ia_i \:\:(=a\cdot x)$  where $a = (\varphi(e_1),...,\varphi(e_n))$.
The map $X'\to \mathbb{K}^n$ for $n$-dimensional $X'$ given by $\varphi_a \mapsto a$ is an isomorphism (but NOT an isometry).
So $X' \simeq X^*$.

### Remark

>[!Remark] 
>If $\dim X = \infty$, then $X' \subsetneq X^*$

As an example, take $(C([0,1]), \|\cdot\|_1)$ which is NOT Banach and consider $\varphi \in X^*$ given by $\varphi(f) = f(1)$