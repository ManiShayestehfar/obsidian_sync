- This theorem allows us to obtain *global* bounds from *local* bounds.

# Theorem

>[!Theorem]
>Let $X$ be Banach and $Y$ a normed vector space. Let $T_\alpha \in \mathcal{L}(X,Y)$ for $\alpha \in A$. Then
>$$\sup_{\alpha \in A}\|T_\alpha x\| < \infty \:\:\ \forall x\in X \qquad\implies \qquad \sup_{\alpha \in A} \|T_\alpha\| < \infty$$


# Corollaries
## Pointwise Convergence of Operator 

>[!Corollary]
>$X$ Banach, and $Y$ a normed space. 
>If $T_n \in \mathcal{L}(X,Y)$ converges *pointwise* to $T:X\to Y$ (i.e. $T_nx \to Tx\:\forall x\in X$), then 
>1. $T \in \mathcal{L}(X,Y)$ (T is continuous)
>2. $\|T\| \leq \limsup_{n \to \infty} \|T_n\|$
##### Proof
If $T_n x \to Tx$ for all $x \in X$, then clearly $T \in \text{Hom}(X,Y)$. We need to prove continuity.
Since $\|T_nx\|\to \|Tx\|$, we have $\sup_{n\geq 1}\|T_nx\| < \infty$ for all $x \in X$.
So by the Principle of Uniform Boundedness: $\sup_{n\geq 1}\|T_n\| < \infty$.

Let $c = \limsup_{n \to \infty} \|T_n\| < \infty$. Then
$$\|Tx\|\longleftarrow \|T_nx\| \leq \|T_n\|\|x\| \leq \sup_{k \geq n} \|T_k\|\|x\| \longrightarrow c \|x\|$$
So $\|Tx\| \leq c \|x\|$ and thus $T$ is continuous by $\|T\|\leq c$.  $\square$


>[!Remark]
>The corollary does *NOT* say that $T_n \to T$ uniformly. i.e $\|T-T_n\| \not\to 0$ necessarily.
>
##### Proof
Take $T_n:\ell^2 \to \ell^2$ with $T_nx = x_ne_n$. Then $\|T_n\| = 1$, but $x_n \to 0$, so $T_n x \to 0x$ for all $x$.
So the pointwise limit is $T=0$ (the zero operator), and $\|T_n-T\| = \|T\|=1 \neq 0$. $\square$


>[!Remark]
>Completeness of $X$ is important for the result of the Corollary (and PUB).
##### Proof
Take $\ell_F \subseteq \ell^2$ and let 
$$T_nx = (x_1,2x_2,3x_3,...,nx_n,0,0,0,...)$$
Then $\|T_nx\|_2^2 = \sum_{k=1}^n k^2|x_k|^2 \leq$ 
