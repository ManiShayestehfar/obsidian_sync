- This theorem allows us to obtain *global* bounds from *local* bounds.

# Theorem

>[!Theorem]
>Let $X$ be Banach and $Y$ a normed vector space. Let $T_\alpha \in \mathcal{L}(X,Y)$ for $\alpha \in A$. Then
>$$\sup_{\alpha \in A}\|T_\alpha x\| < \infty \:\:\ \forall x\in X \qquad\implies \qquad \sup_{\alpha \in A} \|T_\alpha\| < \infty$$
##### Proof
Let $X_n = \{x \in X \:|\: \|T_\alpha x\|\leq n\:\forall \alpha \in A\}$. 
These sets are closed (by continuity of $T_\alpha$), and $X = \bigcup_{n=1}^\infty X_n$ (by the hypothesis).

By Baire's Theorem (corollary on closed sets), there is $m \geq 1$ with $\text{int}(X_m) \neq \varnothing$.
So $x \in \text{int}(X_m)$ and $r >0$ with $B(x_0,r)\subseteq \text{int}(X_m)$.
If $\|z\|\leq 1$, then $x_0 + rz \in \overline{B(x_0,r)}\subseteq X_m$ ($X_m$ is closed.)
Hence, for all $\alpha \in A$,
$$\begin{align*}
\|T_\alpha(rz)\| &= \|T_\alpha(x_0+rz)- T_\alpha x_0\| \\
&\leq \|T_\alpha(x_0+rz)\| + \|T_\alpha x_0\|\\
&\leq m+m = 2m.
\end{align*}$$
$\implies$ $\|T_\alpha z\|\leq 2m/r$ for all $\alpha \in A$ and all $\|z\| \leq 1$.
$\implies \|T_\alpha x\|\leq 2m/r \:\|x\|$ for all $\alpha \in A$, and all $x \in X$.  
$\implies \|T_\alpha\| \leq 2m/r$.
Thus $\sup_{\alpha \in A} \|T_\alpha\| < \infty$.  


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
Then $\|T_nx\|_2^2 = \sum_{k=1}^n k^2|x_k|^2 \leq n^2 \sum_{k=1}^n |x_k|^2 = n^2 \|x\|_2^2$  for all $x \in \ell_F$.
So $T_n \in \mathcal{L}(\ell_F,\ell_F)$. The pointwise limit is $Tx = (x_1,2x_2,3x_3,...)$.
This is *NOT* continuous as $\|Te_n\|_2 = n \|e_n\|_2 \to \infty$.


