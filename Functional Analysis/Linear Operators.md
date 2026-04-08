# Definition

>[!Def] 
>Let $X,Y$ be Normed Vector spaces over $\mathbb{K}$. Then $T: X \to Y$ is a **linear operator** (a.k.a a vector space homomorphism) such that
>1. $T(x+y) = T(x) + T(y)$ $\forall x,y \in X$
>2. $T(\lambda x) = \lambda T(x)$  $\forall \lambda \in \mathbb{K}$

## Examples

1. If $\dim X < \infty$ and $\dim Y < \infty$, then if we choose bases for $X,Y$, i.e. $X = \langle v_1,...,v_n\rangle$ and $Y = \langle w_1,...,w_m\rangle$ then $T$ is a linear transformation matrix $$Tv_j = \sum_{i=1}^m a_{ij}w_i \quad\implies \quad T = (a_{ij})$$
2. $\mathcal{D}: \mathcal{P}([0,1]) \to \mathcal{P}([0,1]), \quad p \mapsto p'$   (differentiation)
3. $\mathcal{I}: C_\mathbb{R}([0,1]) \to C_\mathbb{R}([0,1]),$  $f(x) \mapsto \int_{0}^x f(t)\:dt$  (integration)
4. $L: \ell_F(\mathbb{K}) \to \ell_F(\mathbb{K}),$  $(x_1,x_2,x_3,...)\mapsto (x_2,x_3,x_4,...)$ (left-shift)
5. $R: \ell_F(\mathbb{K}) \to \ell_F(\mathbb{K}),$ $(x_1,x_2,x_3,...)\mapsto (0,x_1,x_2,...)$ (right-shift)
6. $T: \ell^2 \to \ell^1,$ $(x_1,x_2,x_3,...)\mapsto (\tfrac{x_1}{1},\tfrac{x_2}{2},\tfrac{x_3}{3},...)$
   We must check if $x \in \ell^2$, then $\|Tx\|\in \ell^1$: $$\|Tx\|_1 = \sum_{i=1}^\infty \left|\frac{x_i}{i}\right| \overset{C.S}{\leq} \sqrt{\sum_{i=1}^\infty \frac{1}{i^2}} \sqrt{\sum_{i=1}^\infty |x_i|^2} = \frac{\pi}{\sqrt{6}}\|x\|_2 \quad\implies Tx \in \ell^1$$

# Space of Continuous Linear Operators

>[!Def] 
>$X,Y$ are vector spaces. Then $$\mathcal{L}(X,Y) = \{T \in \text{Hom} \:|\: T \:\text{continuous}\}$$

**Continuity of $T$ at $x=a$:**
$\forall \varepsilon >0$, $\exists \delta >0$ such that $\|x-a\|_X < \delta \implies \|Tx-Ty\|_Y \leq \varepsilon$
e.g. if $x_n \to A$ (in $X$), then $Tx \to Ta$ (in $Y$)


# Linear Operator Characterisation of Continuity

>[!Lemma]
>For $T \in \text{Hom}(X,Y)$, the following are equivalent:
>1. $T$ is continuous at $0$
>2. $T$ is uniformly continuous
>3. $T$ is continuous everywhere
>4. $T$ is bounded, i.e. $\forall M > 0, \exists M'>0$ such that $\|x\|_X \leq M \implies \|Tx\|_Y\leq M'$
>5. $\exists C>0$ such that $\|Tx\|_Y \leq C\|x\|_X$ for all $x \in X$.
##### Proof
###### 1 -> 2
Let $\varepsilon >0$ be given. There is $\delta>0$ so that $\|h-0\|_X = \|h\| <\delta \implies \|Th-T0\| = \|Th\| <\varepsilon$  for all $h \in X$.

Now let $h := x-y$
So $\forall x,y \in X$, $\|x-y\|<\delta \implies \|T(x-y)\| < \varepsilon \implies \|Tx-Ty\|<\varepsilon$ 
So $T$ is uniformly continuous. 
###### 2 -> 3
Obvious
###### 3 -> 4
WLOG we can assume continuity at $x=0$. So $\forall \varepsilon >0$, $\exists \delta> 0$ such that $\|x\|<\delta \implies \|Tx\| < \varepsilon$.
Hence for any $M>0$, if $\|x\|<M \implies \|x\| < (\frac{M}{\delta})\delta$ .
Hence $\|\tfrac{\delta}{M}x\|< \delta \implies \|T(\tfrac{\delta}{M}x)\|< \varepsilon \implies \tfrac{\delta}{M}\|Tx\| < \varepsilon \implies \|Tx\| < \frac{M}{\delta}\varepsilon =: M'$ 
###### 4 -> 5
Assume $\exists C>0$ such that if $\|x\|<1\implies \|Tx\| \leq C$.
Hence for any $x \in X$ we have $\tfrac{x}{\|x\|}=1\implies \|T(\tfrac{x}{\|x\|})\| \leq C\implies \|Tx\| \leq C\|x\|$  

###### 5 -> 1
If $\|Tx\| <c\|x\| \leq c\delta =: \varepsilon$ provided that $\|x\|<\delta$.
Hence $T$ is continuous at $0$.
$\square$

## Boundedness of operators (for previous examples)

1. $\mathcal{D}: (\mathcal{P}([0,1]), \|\cdot\|_\infty) \to (\mathcal{P}([0,1]), \|\cdot\|_\infty)$
   Take $p_n = x^n \implies \mathcal{D}p_n = nx^{n-1}$ 
   So $\|p_n\|_\infty =1$ but $\|\mathcal{D}p_b\|_\infty = n = n\|p_n\|_\infty$ so no inequality of form $\|\mathcal{D}p_n\|_\infty < C\|p_n\|_\infty$ 
   $\therefore$ NOT bounded

2. $\mathcal{I}: (C([a,b]), \|\cdot\|_\infty) \to (C([a,b]), \|\cdot\|_\infty)$ such that $(\mathcal{I}f)(x) = \int_a^x f(t)\:dt$ 
   $$\begin{align*}
\|\mathcal{I}f\|_\infty = \sup_{x \in [a,b]}\left|\int_a^x f(t)\:dt\right| \overset{\Delta-\text{ineq.}}{\leq} &\sup_{x \in [a,b]} \int_a^x|f(t)|\:dt \\[2pt]
&\leq \int_a^b |f(t)|\:dt \\[2pt]
&\leq \|f\|_\infty(b-a) 
\end{align*}$$
so by $(5) \implies (4)$ $\mathcal{I}$ is bounded.


# Norm of Linear Operators

>[!Theorem]
>$(\mathcal{L}(X,Y), \|\cdot\|)$ is a normed vector space with $$\|T\| = \inf\:\{c>0 \:|\: \|Tx\|_Y \leq c \|x\|_X \:\: \forall x \in X\}$$
>Moreover if $Y$ is Banach, then $\mathcal{L}(X,Y)$ is Banach too.
##### Proof
###### $\|T\|$ is a norm
We only need to check $\Delta$-inequality. Everything else comes for free.
Take $S,T \in \mathcal{L}(X,Y)$. $$\begin{align*}
\|(S+T)x\| = \|Sx+Tx\| &\overset{\Delta-\text{ineq.}}{\leq} \|Sx + Tx\| \\[3pt]
&\leq \|S\|\|x\| + \|T\|\|x\| \\[3pt]
&= \underbrace{(\|S\| + \|T\|)}_{=C}\|x\| 
\end{align*}$$$\therefore S+T \in \mathcal{L}(X,Y)$, and $\|S+T\| \leq \|S\|+\|T\|$ 

###### Second Part $(\Longrightarrow)$
Assume $Y$ is Banach.
Let $(T_n)_{n\geq 1}$be Cauchy in $\mathcal{L}(X,Y)$. Then for each $x \in X$:
$$\|T_mx-T_nx\| = \|(T_m-T_n)x\|\leq \|T_m-T_n\|\|x\|$$
So $(T_nx)_{n\geq1}$ is Cauchy in $Y$ (for some fixed $X$).
Since $Y$ is complete, there is a limit. Define a function $T:X\to Y$ by $Tx := \lim_{n\to \infty}T_nx$

>[!Claim]
>$T$ is linear

If $\lambda,\mu \in \mathbb{K}$ and $x,x'\in X$, then $T_n(\lambda x+\mu x') = \lambda T_nx + \mu T_n x'$. But both sides are pointwise convergent so the expression is equal to $T(\lambda x+\mu x') = \lambda Tx + \mu T x'$. $\square$

>[!Claim]
>$T$ is continuous

$\|Tx\| = \lim_{n\to \infty} \|T_nx\|\leq \|T_n\|\|x\|$. But $(\|T_n\|)_{n\geq 1}$ in $\mathbb{K}$ is Cauchy. so
$|\|T_m\|-\|T_n\|| \leq \|T_m-T_n\|$ converges and $\exists C>0$ such that $\|T_n\|\leq C$ for all $n$. 
$\therefore \|Tx\| \leq C\|x\|$ and so $T$ is continuous by the equivalent characterisation of continuity.
$\square$

>[!Claim]
>$T_n \to T$ in $\mathcal{L}(X,Y)$

Given $\varepsilon > 0$ there exists $N >0$ such that $\forall m,n \geq N$ 
$$\|T_nx - T_m x\| \leq \|T_n-T_m\|\|x\| \leq \varepsilon \|x\|$$
but $\|T_nx -T_mx\|\to \|T_nx-Tx\|$ in $Y$, so $\|T_n -T\|< \varepsilon$ for all $n \geq N$. 
$\therefore \|T_n-T\|\to 0$.  $\square$



## Formula for $\|T\|$

>[!Lemma]
>$$\|T\| = \sup_{\|x\|\leq 1} \|Tx\| = \sup_{\|x\|=1}\|Tx\| = \sup_{x\neq0} \frac{\|Tx\|}{\|x\|}$$



## Algorithm for calculating operator norms

1. Use sensible inequalities to find a "$C$" that works in $\|Tx\| \leq C\|x\|$  for all $x \in X$ so $\|T\|\leq C$
2. Now find an $x_0 \in X$ with $x_0\neq 0$ and $\|Tx_0\| = C\|x_0\|$ giving $\|T\|\geq C$ 
	- There is often no such $x_0$ So we can do the next best thing:
	  Find $(x_n)_{n\geq 1}$ in $X$ such that $\frac{\|Tx_n\|}{\|x_n\|} \to C$ as $n \to \infty$. Then $\|T\|\geq C$.

## Examples 

1. $L: \ell^1 \to \ell^1$ given by $Lx = (x_2,x_3,x_4,...)$
   $\|Lx\|_1 = \sum_{k=2}^\infty |x_k| \leq \sum_{k=1}^\infty |x_k| = \|x\|_1$ so $\|L\|\leq 1$.
   Also $\|L(0,1,0,...)\|_1 = \|(1,0,0,...)\|_1 = 1 =\|(0,1,0,...)\|_1$
   $\implies \|L\|=1$

2. $T:\ell^2 \to \ell^1$, $Tx(\tfrac{x_1}{1}, \tfrac{x_2}{2},...)$. Using Cauchy-Schwartz we showed $\|Tx\| \leq \tfrac{\pi}{\sqrt{6}} \|x\|_2$ so $\|T\|\leq \tfrac{\pi}{\sqrt{6}}$
   Take $x_0 = (\tfrac{1}{1}, \tfrac{2}{1}, \tfrac{3}{1},...) \in \ell^2$ 
   So $\|Tx_0\|_1 = \sum_{k=1}^\infty \frac{1}{k^2} = \frac{\pi^2}{6} = \frac{\pi}{\sqrt{6}}\|x_0\|_2$ 
   $\therefore \|T\|=\frac{\pi}{\sqrt{6}}$.

3. $T: \ell^2 \to \ell^2$,  $(x_1,x_2,...) \mapsto (x_1+x_2,x_2+x_3,...)$. We want to find $\|T\|$.
   Note that $T = I + L$ where $I$ is the identity map and $L$ is the left shift operator.
   Hence $\|T\| = \|I+L\| \leq \|I\| + \|L\| = 2 \implies T \in \mathcal{L}(\ell^2,\ell^2)$. We prove this

>[!Claim]
>1. $\forall x \in \ell^2:\: \|Tx\|_2\leq 2\|x\|_2 \implies \|T\|\leq2$
>2. $\|T\|=2$
##### Proof
###### Part 1
We have $$\begin{align*}
\|Tx\|_2^2 = \sum_{n=1}^\infty |x_k+x_{k+1}|^2 &\leq \sum_{k=1}^\infty (|x_k|^2 + 2|x_k||x_{k+1}| + |x_{k+1}|^2) \\[2pt]
&\overset{C.S}{\leq} 2\|x\|^2 + 2 \sqrt{\sum_{k=1}^\infty |x_k|^2}\sqrt{\sum_{k=2}^\infty |x_k|^2} \\
&\leq 4\|x\|_2^2
\end{align*}$$
Hence $T$ is continuous with $\|T\|\leq 2$.

###### Part 2
Let $x^n := (\overbrace{1,1,...,1}^{n},0,0,...)$.
$\implies \|x^n\|_2^2 = n$.
$\implies Tx^n = (2,2,...,1,1,0,0,...)$
$\implies \|Tx^n\|_2^2 = 4(n-1)+1$
$\implies \frac{\|Tx^n\|_2^2}{\|x^n\|_2^2} = \frac{4(n-1)+1}{n} \longrightarrow 4$ as $n \to \infty$.
$\therefore \|T\| = 2$      $\square$
