# Definition

>[!Def] 
>Let $X,Y$ be Normed Vector spaces over $\mathbb{K}$. Then $T: X \to Y$ is a **linear operator** (aka a vector space homomorphism) such that
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
Let $\varepsilon >0$ be given. There is $\delta>0$ so that $\|x-0\|_X = \|x\| <\delta \implies \|Tx-T0\| = \|Tx\| <\varepsilon$ 

So $\forall a \in X$, $\|x-a\|<\delta \implies \|T(x-a)\| < \varepsilon \implies \|Tx-Ta\|<\varepsilon$ 
So $T$ is uniformly continuous. 
###### 2 -> 3
Obvious
###### 3 -> 4
WLOG we can assume continuity at $x=0$. So $\forall \varepsilon >0$, $\exists \delta> 0$ such that $\|x\|<\delta \implies \|Tx\| < \varepsilon$.
Hence for any $M>0$, if $\|x\|<M \implies \|x\| < (\frac{M}{\delta})\delta$ .
Hence $\|\tfrac{\delta}{M}x\|< \delta \implies \|T(\tfrac{\delta}{M}x)\|< \varepsilon \implies \tfrac{\delta}{M}\|Tx\| < \varepsilon \implies \|Tx\| < \frac{M}{\delta}\varepsilon =: M'$ 
###### 4 -> 5
Assume $\exists C>0$ such that if $\|x\|<1\implies \|Tx\| \leq C$.
Hence for any $x \in X$ we hve $\tfrac{x}{\|x\|}=1\implies \|T(\tfrac{x}{\|x\|})\| <= C\implies \|Tx\| \leq C\|x\|$  

###### 5 -> 1
If $\|Tx\| <c\|x\| \leq c\delta =: \varepsilon$ provided that $\|x\|<\delta$.
Hence $T$ is continuous at $0$.
$\square$

## Boundedness of operators (for previous examples)

2. $\mathcal{D}: (\mathcal{P}([0,1]), \|\cdot\|_\infty) \to (\mathcal{P}([0,1]), \|\cdot\|_\infty)$
   Take $p_n = x^n \implies \mathcal{D}p_n = nx^{n-1}$ 
   So $\|p_n\|_\infty =1$ but $\|\mathcal{D}p_b\|_\infty = n = n\|p_n\|_\infty$ so no inequality of form $\|\mathcal{D}p_n\|_\infty < C\|p_n\|_\infty$ 
   $\therefore$ NOT bounded

3. $\mathcal{I}: (C([a,b]), \|\cdot\|_\infty) \to (C([a,b]), \|\cdot\|_\infty)$ such that $(\mathcal{I}f)(x) = \int_a^x f(t)\:dt$ 
   $$\begin{align*}
\|\mathcal{I}f\|_\infty = \sup_{x \in [a,b]}\left|\int_a^x f(t)\:dt\right| \overset{\Delta-\text{ineq.}}{\leq} &\sup_{x \in [a,b]} \int_a^x|f(t)|\:dt \\[2pt]
&\leq \int_a^b |f(t)|\:dt \\[2pt]
&\leq \|f\|_\infty(b-a) 
\end{align*}$$
so by $(5) \implies (4)$ $\mathcal{I}$ is bounded.


# Norm of Linear Operators

>[!Theorem]
>$\mathcal{L}(X,Y)$ is a normed vector space with $$\|T\| = \inf\:\{c>0 \:|\: \|Tx\|_Y \leq c \|x\|_X \:\: \forall x \in X\}$$
>Moreover $\mathcal{L}(X,Y)$ is Banach $\iff$ $Y$ is Banach.
##### Proof
###### $\|T\|$ is a norm
We only need to check $\Delta$-inequlity. Everything else comes for free.
Take $S,T \in \mathcal{L}(X,Y)$. $$\begin{align*}
\|(S+T)x\| = \|Sx+Tx\| &\overset{\Delta-\text{ineq.}}{\leq} \|Sx + Tx\| \\[3pt]
&\leq \|S\|\|x\| + \|T\|\|x\| \\[3pt]
&= \underbrace{(\|S\| + \|T\|)}_{=C}\|x\| 
\end{align*}$$$\therefore S+T \in \mathcal{L}(X,Y)$, and $\|S+T\| \leq \|S\|+\|T\|$ 

###### Second Part



## Formula for $\|T\|$

>[!Lemma]
>$$\|T\| = \sup_{\|x\|\leq 1} \|Tx\| = \sup_{\|x\|=1}\|Tx\| = \sup_{x\neq0} \frac{\|Tx\|}{\|x\|}$$



## Algorithm for calculating operator norms

1. Use sensible inequalities to find a "$C$" that works in $\|Tx\| \leq C\|x\|$  for all $x \in X so $\|T\|\leq C$
2. 