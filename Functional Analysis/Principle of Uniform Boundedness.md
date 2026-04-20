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
Thus $\sup_{\alpha \in A} \|T_\alpha\| < \infty$.  $\square$


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


# Application
## Pointwise Non-Convergence of Fourier Series

#### Motivation

Recall the Fourier series of $f \in L_\mathbb{C}^2 ([0,2\pi])$ with respect to Hilbert basis $S = \{e_n(t) \:|\: n\in \mathbb{Z}\}$ where $e_n(t) = \frac{1}{\sqrt{2\pi}}e^{int}$, is 
$$f= \sum_{n \in \mathbb{Z}} \langle f,e_n \rangle e_n,$$
where $\langle f, e_n \rangle = \frac{1}{\sqrt{\pi}} \int_0^{2\pi} f(t) e^{-int}\:dt$.

This is only an $L^2$-equality. It was conjectured that
$$f \in C_{2\pi}([0,2\pi]) \qquad \implies \qquad f(t)= \sum_{n \in \mathbb{Z}} \langle f,e_n \rangle e_n(t)\:\: \forall t \in [0,2\pi].$$
This is **FALSE**! We can prove this using PUB.

#### Proof of non-convergence of Fourier Series
>[!Theorem]
>Let $a \in [0,2\pi]$. There exists $f \in C_{2\pi}([0,2\pi])$ where *no* Fourier series converges at $t=a$
##### Proof
Let $X = C_{2\pi}([0,2\pi])$. Then $X$ is a closed subspace of $C([a,b])$ and thus $X$ is Banach with $\|\cdot\|_\infty$.
If $f \in X$, let 
$$f_n= \sum_{|k|\leq n} \langle f,e_k \rangle e_k. \tag{$n \in \mathbb{N}$}$$
For each $n \in \mathbb{N}$, define $T_n: X \to \mathbb{C}$ by:
$$T_nf = f_n(a)\qquad \forall f \in X.$$
>[!Claim]
>$T_n$ is continuous, and 
>$$\|T_n\| = \frac{1}{2\pi} \int_0^{2\pi} |D_n(t)|\:dt$$
###### Proof
$$\begin{align*}
f_n(a) &= \sum_{|k|\leq n} \langle f, e_k \rangle e_k(a) \\
&= \sum_{|k|\leq n} \left(\frac{1}{2\pi} \int_0^{2\pi} f(t) e^{-ikt} \:dt\right) e^{ika} \\
&= \frac{1}{2\pi} \int_0^{2\pi} f(t) \left(\sum_{|k|\leq n} e^{ik(a-t)}\right) \:dt \\
&= \frac{1}{2\pi} \int_0^{2\pi} f(t) D_n(a-t)\:dt \\
&= \frac{1}{2\pi} \int_0^{2\pi} f(a-t) D_n(t)\:dt \tag{by periodicity}
\end{align*}$$
where $D_n(t) := \sum_{|k| \leq n} e^{ikt} = \frac{\sin(n+\tfrac{1}{2})t}{\sin \tfrac{t}{2}}$ is the **Dirichlet kernel**.
Now 
$$\begin{align*}
|T_nf| &= |f_n(a)| \\[2pt]
&= \frac{1}{2\pi} \left|\int_0^{2\pi} f(a-t) D_n(t) \: dt\right| \\
&\leq \left(\frac{1}{2\pi} \int_0^{2\pi} |D_n(t)| \: dt\right)\: \|f\|_\infty\\
\end{align*}$$
So $T_n$ is continuous and $\|T_n\|\leq \frac{1}{2\pi} \int_0^{2\pi} |D_n(t)| \: dt$. $\square$

Now define the step function
$$s(t) = \begin{cases}
1 & D_n(t) \geq 0  \\
-1 & D_n(t) \leq 0
\end{cases}$$
Recall by the [[Lebesgue Spaces|Fisher-Risz Theorem]], that $C([a,b])$ is dense in $L^1$ w.r.t $\|\cdot\|_1$. So the step function can be uniformly approximated in $L^1$-

