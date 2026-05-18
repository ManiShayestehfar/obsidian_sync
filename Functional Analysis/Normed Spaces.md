
# Closed and Boundedness of N.S

>[!Corollary]
>Every compact normed vector space is closed and bounded

- This can easily be extended to metric spaces

##### Proof
###### $(\Rightarrow)$ 
$Y \subset (\mathbb{K}^n, \|\cdot\|_2)$. Since $\mathbb{K}^n$ is compact, then so is $Y$ and therefore $Y$ is sequentially compact.
By [[Main Definitions|Fish's Heine-Borel]], $Y$ compact implies $Y$ is totally bounded, which means that we can make a ball big enough $B(0,M)$ that covers all of $Y$. Hence $Y$ is *bounded*.

Suppose $(x_n)\subset Y$ converges in $\mathbb{K}^n$. i.e. $x_n \to x$ in $\mathbb{K}^n$. 
But there exists a subsequence $(x_{n_k}) \subset (x_n)$ which also converges with $x_{n_k} \to y$. But if a sequence converges to $x$, a subsequence must also converge to the same limit $x$. So $x=y$ and this $Y$ is *closed*.

###### $(\Leftarrow)$
$(\mathbb{K}^n, \|\cdot\|_2)$ is complete. Since $Y \subset \mathbb{K}^n$ is closed by assumption, then every Cauchy sequence in $Y$ must converge inside it, thus $Y$ is *complete*. 

By assumption $(Y, \|\cdot \|_2)$ is bounded. $Y \subset B(0,R) = \{x \in \mathbb{K}^n\:|\: \|x\|_2 < R\}$. Since $B(0,R)$ is totally bounded, then so $Y$ is *totally bounded* too.

By [[Main Definitions|Fish's Heine-Borel]], *complete* and *totally bounded* implies compact in $\mathbb{K}^n$. $\square$


# Isometric Isomorphisms

>[!Definition]
>A map $\varphi: (X, \|\cdot \|_X) \to (Y, \|\cdot\|_Y)$ is an **isometric isomorphism** if:
>1. $\varphi$ is an isomorphism between $X$ and $Y$
>2. $\varphi$ preserves the norms. i.e. $\|\varphi(x)\|_Y = \|x\|_X$

- If $X \cong Y$, then $X$ is Banach $\iff$ $Y$ is Banach.

## Examples

1. $(C([0,1]), \|\cdot\|_\infty) \not \cong (C([0,1]), \|\cdot\|_n)$ for $n>1$ since one of them is Banach and the other is not.
2. $(C([0,1]), \|\cdot\|_1) \not\cong (C([0,1]), \|\cdot\|_2)$
3. For $1 < p,q < \infty$,  $(\ell^p, \|\cdot\|_p) \cong (\ell^q, \|\cdot\|_q)$ if $\frac{1}{p} + \frac{1}{q} = 1$. 




# Equivalent Norms

If $X$ is a vector space on field $\mathbb{K}$, if $\|x_n - x\|_A \to 0$, then does it imply that $\|x_n-x\|_B \to 0$?
- Two topologies induced by $\|\cdot \|_A, \|\cdot\|_B$ coincide.

>[!Definition] Equivalent Norms
>Norms $\|\cdot \|_A,\|\cdot \|_B$ on $X$ are **equivalent** if $\exists c_1,c_2 >0$ such that $$c_1\|x\|_B \leq \|x\|_A \leq c_2\|x\|_B \quad \forall x \in X$$

- Indeed $\|x\|_A \sim \|x\|_B$ is an equivalence relation

## Convergence Coming from One Norm

>[!claim] 
>Assume $\exists C>0$ such that $\|x\|_A \leq C \|x\|_B$ for all $x \in X$. Then if $x_n \to x$ in $\|\cdot\|_B$, then $x_n \to x$ in $\|\cdot \|_A$ as well.
##### Proof
$x_n \to x$ in $\|\cdot\|_B$ means $\|x_n - x\|_B \to 0$. 
Since $\|x_n-x\|_A \leq C \|x_n-x\|_B \to 0$ and thus $\|x_n - x\|_A \to 0$.

#### The Claim implies:

>[!Theorem]
>Topologies of $(X,\|\cdot\|_A)$ and $(X, \|\cdot\|_B)$ coincide $\iff$ $\|\cdot\|_A \sim \|\cdot\|_B$.
##### Proof
###### $(\Leftarrow)$  
Follows from the claim
###### $(\Rightarrow)$
**Proof by contrapositive:**
Assume the norms are not equivalent. Without loss of generality, $\|x\|_A \leq C\|x\|_B$ does not hold. 
Hence $\forall n\geq 1$, $\exists x_n \in X$ such that $\|x_n\|_A \geq n\|x_n\|_B$.
Since $x_n \neq 0$, then $$\left\|\frac{x_n}{\|x_n\|_A}\right\|_B \leq \frac{1}{n}\implies \frac{\|x_n\|_B}{\|x\|_A} \leq \frac{1}{n} \longrightarrow 0 \quad \text{w.r.t. } \|\cdot\|_B$$
But $\left\|\frac{x_n}{\|x_n\|_A}\right\|_A = 1 \neq 0$ and hence the limits are not the same. $\square$


## Examples
### Equivalent norms on $\mathbb{K}^n$
$\|x\|_1 \sim \|x\|_2$ for $x \in \mathbb{K}^n$. 
   *Upper Bound:*$$\|x\|_1 = \sum_{i=1}^n |x_i \cdot 1| \:\overset{C.S}{\leq}\: \left(\sum_{i=1}^n x_i^2\right)^{1/2}\left(\sum_{i=1}^n 1^2\right)^{1/2} = \left(\sum_{i=1}^n x_i^2\right)^{1/2}\sqrt{n}$$
   where we used the Cauchy-Schwartz inequality above. 
   
   *Lower Bound:*
   $\forall i, |x_i| \leq \|x\|_1$. Hence 
   $$\frac{|x_i|^2}{\|x\|_1^2}\leq\frac{|x_i|}{\|x\|_1} \implies \frac{\sum |x_i|^2}{\|x\|_1^2}\leq\frac{\sum|x_i|}{\|x\|_1} = \sum \frac{|x_i|}{\|x\|_1} = 1$$
   $\implies \|x\|_2^2 \leq \|x\|_1^2$. Thus $\|x\|_2 \leq \|x\|_1 \leq \sqrt{n}\|x\|_2$.

### Equivalent norms on $C([0,1])$

$\|f\|_1 \not \sim \|f\|_2$ in $C([0,1])$. 
But $\int_0^1 |f_n|\:dx \overset{C.S}{\leq} \left(\int_0^1 |f(x)|^2 \:dx\right) \underbrace{\left(\int_0^1 1^2\:dx\right)}_{=1}$. 
Therefore $\|f\|_1 \leq \|f\|_2$. But $\not\exists C >0$ such that $\|f\|_2 \leq C\|f\|_1$.  
To prove it, assume it does exist and consider the following graph:
   
   ![[desmos-graph (2).png|350]]
   
We are assuming $\forall (f_n) \subset C([0,1])$ such that $\|f_n-f\|_1 \to 0$, $\|f_n-f\|_2 \to 0$. 
But in the graph, $\|f_n\|_1 = \frac{1}{\sqrt{n}} \to 0$. $$\|f_n\|_2^2 = \int_0^1 |f_n(x)|^2\:dx = 2 \int_0^{1/n}n\sqrt{n}x\:dx = \frac{2}{3}n^3\frac{1}{n^3} = \frac{2}{3} \neq 0$$




## Finite Dimensional Normed Spaces

>[!Theorem]
>Let $X$ be a finite-dimensional vector space over $\mathbb K$. Then any two norms on $X$ are equivalent.
##### Proof

Let $\dim X=N$, and fix a basis $\{e_1,\dots,e_N\}$ of $X$.
It is enough to show that every norm on $X$ is equivalent to the Euclidean norm induced by this basis. Indeed, if two norms are both equivalent to the same norm, then they are equivalent to each other.

Let $\|\cdot\|$ be an arbitrary norm on $X$. For each $x\in X$, write $x=\sum_{i=1}^N x_i e_i$, and define $\|x\|_2:=\left(\sum_{i=1}^N |x_i|^2\right)^{1/2}$.

We will show that there exist constants $c,C>0$ such that $c\|x\|_2\leq \|x\|\leq C\|x\|_2$ for all $x\in X$.

###### Upper Bound
Let $M:=\max_{1\leq i\leq N}\|e_i\|$. Then, for any $x=\sum_{i=1}^N x_i e_i\in X$, we have

$$
\|x\|
=
\left\|\sum_{i=1}^N x_i e_i\right\|
\leq
\sum_{i=1}^N |x_i|\|e_i\|
\leq
M\sum_{i=1}^N |x_i|
\overset{C.S}{\leq}
\sqrt N\left(\sum_{i=1}^N |x_i|^2\right)^{1/2}
=\sqrt N\|x\|_2
$$
Hence $\|x\|\leq M\sqrt N\|x\|_2$. Therefore the upper bound holds with $C:=M\sqrt N$.

###### Lower Bound

>[!claim]
>Define $f:(X,\|\cdot\|_2)\to(\mathbb R,|\cdot|)$ by $f(x):=\|x\|$. The $f$ is continuous.

- **Proof:**
	For all $x,y\in X$, by the reverse triangle inequality, $|f(x)-f(y)|=\big|\|x\|-\|y\|\big|\leq\|x-y\|.$
	Using the upper bound already proven, $\|x-y\|\leq C\|x-y\|_2$. Therefore $|f(x)-f(y)|\leq C\|x-y\|_2$.
	So $f$ is Lipschitz continuous, and hence continuous. $\square$


Now consider $S:=\{x\in X:\|x\|_2=1\}$. Since $X$ is finite-dimensional, $S$ is closed and bounded, hence compact by [[Main Definitions|Fish's Heine-Borel]].

Since $f$ is continuous on $S$, the Extreme Value Theorem implies that $f$ attains its minimum on $S$. Hence there exists $x_0\in S$ such that $f(x_0)\leq f(x)$ for all $x\in S$. Equivalently, $\|x_0\|\leq \|x\|$ for all $x\in S$.

Let $c:=\|x_0\|$. Since $x_0\in S$, we have $\|x_0\|_2=1$, so $x_0\neq 0$. Since $\|\cdot\|$ is a norm, $c=\|x_0\|>0$. Therefore, for all $x\in S$, $c\leq \|x\|$.

Now let $x\in X\setminus\{0\}$. Then $\frac{x}{\|x\|_2}\in S$, so

$$
c
\leq
\left\|\frac{x}{\|x\|_2}\right\|
=
\frac{\|x\|}{\|x\|_2} \qquad\implies \qquad c\|x\|_2\leq \|x\|.
$$

This inequality also holds when $x=0$, since both sides are $0$.

Thus, for all $x\in X$, we have $c\|x\|_2\leq \|x\|\leq C\|x\|_2$. Therefore $\|\cdot\|\sim \|\cdot\|_2$.
Finally, let $\|\cdot\|_a$ and $\|\cdot\|_b$ be any two norms on $X$. Since both are equivalent to $\|\cdot\|_2$, they are equivalent to each other.
 $\square$


### Banach-ness of Finite Dimensional Vector Spaces

>[!Corrolary]
>1. All finite dimensional normed vector spaces are Banach
>2. Any finite dimensional subspace of a normed space is closed.

- (1) follows simply from above as $(\mathbb{K}^N, \|\cdot\|_2)$ is Banach and from theorem above every norm is equivalent to $\|\cdot\|_2$.
- (2) Follows from $Y \subset X$ with $\dim Y < \infty$. Then by $(1)$, $Y$ is Banach $\implies Y$ is closed. 

**Remark for (2):**
Not ALL subspaces of a given space is closed. 
e.g. $(\ell_F, \|\cdot\|_2) \subset (\ell^2, \|\cdot\|_2)$ where $\ell_F$ is the space of sequences in $\mathbb{K}$ with finitely many non-zeros is open.

Take $x^{(m)} = (1,1/2,1/3,...,1/m,0,0,...)$. Then each $x^{(m)}\in \ell_F$.
Let $x := (1,1/2,1/3,1/4,...)$. Then $x \in \ell^2$ since $$\|x\|_2^2 = \sum_{n=1}^\infty \frac{1}{n^2} < \infty$$but $x \not\in \ell_F$ since it has infinitely many nonzero terms.
So $\|x^{(m)}-x\|_2 \to 0$. Thus $x^{(m)}\to x$ in $\ell^2$ with all $x^{(m)}\in \ell_F$ but the limit $x \not\in \ell_F$.
Therefore $\ell_F$ is not closed.

*Therefore* $\ell_F$ *is not Banach*.


