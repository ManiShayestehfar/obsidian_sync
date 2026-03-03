
# Closed and Boundedness of N.S

>[!Corollary]
>Every compact normed vector space is closed and bounded

- This can easily be extended to metric spaces

##### Proof
###### $(\Rightarrow)$ 
$Y \subset (\mathbb{K}^n, \|\cdot\|_2)$. Since $\mathbb{K}^n$ is compact, then so is $Y$ and therefore $Y$ is sequentially compact.
By [[Main Definitions|Fish's Heine-Borel]], $Y$ compact implies $Y$ is totally bounded, which means that we can make a ball big enough $B(0,M)$ that covers all of $Y$. Hence $Y$ is *bounded*.

Suppose $(x_n)\subset Y$ converges in $\mathbb{K}^n$. i.e. $x_n \to x$ in $\mathbb{K}^n$. 
But there exists a subsequence $(x_{n_k}) \subset (x_n)$ which also converges with $x_{n_k} \to y$. But $x=y$ and this $Y$ is *closed*.

###### $(\Leftarrow)$
$(\mathbb{K}^n, \|\cdot\|_2)$ is complete. Since $Y \subset \mathbb{K}^n$ is closed by assumption, then every sequence in $Y$ must converge inside it, thus $Y$ is *complete*. 

By assumption $(Y, \|\cdot \|_2)$ is bounded. $Y \subset B(0,R) = \{x \in \mathbb{K}^n\:|\: \|x\|_2 < R\}$. Since $B(0,R)$ is totally bounded, then so $Y$ is *totally bounded* too.

By [[Main Definitions|Fish's Heine-Borel]], *complete* and *totally bounded* implies compact in $\mathbb{K}^n$. $\square$


# Isometric Isomorphisms

>[!Definition]
>A map $\varphi: (X, \|\cdot \|_X) \to (Y, \|\cdot\|_Y)$ is an **isomorphic isomorphism** if:
>1. $\varphi$ is an isomorphism between $X$ and $Y$
>2. $\varphi$ preserves the norms. i.e. $\|\varphi(x)\|_Y = \|x\|_X$

- If $X \cong Y$, then $X$ is Banach $\iff$ $Y$ is Banach.

## Examples

1. $(C([0,1]), \|\cdot\|_\infty) \not \cong (C([0,1]), \|\cdot\|_n)$ for $n>1$ since one of the is Banach and the other is not.
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
Assume the norms are not equivalent. Without loss of generality, $\|x\|_A \leq C\|x\|_B$ does not hold. 
Hence $\forall n\geq 1$, $\exists x_n \in X$ such that $\|x_n\|_A \geq n\|x_n\|_B$.
Since $x_n \neq 0$, then $$\left\|\frac{x_n}{\|x_n\|_A}\right\|_B \leq \frac{1}{n}\implies \frac{\|x_n\|_B}{\|x\|_A} \leq \frac{1}{n} \longrightarrow 0 \quad \text{w.r.t. } \|\cdot\|_B$$
But $\left\|\frac{x_n}{\|x_n\|_A}\right\|_A = 1 \neq 0$ and hence the limits are not the same. $\square$


## Examples

1. $\|x\|_1 \sim \|x\|_2$ for $x \in \mathbb{K}^n$. 
   *Upper Bound:*$$\|x\|_1 = \sum_{i=1}^n |x_i \cdot 1| \:\overset{C.S}{\leq}\: \left(\sum_{i=1}^n x_i^2\right)^{1/2}\left(\sum_{i=1}^n 1^2\right)^{1/2} = \left(\sum_{i=1}^n x_i^2\right)^{1/2}\sqrt{n}$$
   where we used the Cauchy-Schwartz inequality above. 
   
   *Lower Bound:*
   $\forall i, |x_i| \leq \|x\|_1$. Hence 
   $$\frac{|x_i|^2}{\|x\|_1^2}\leq\frac{|x_i|}{\|x\|_1} \implies \frac{\sum |x_i|^2}{\|x\|_1}\leq\frac{\sum|x_i|}{\|x\|_1} = \sum \frac{|x_i|}{\|x\|_1} = 1$$
   $\implies \|x\|_2^2 \leq \|x\|_1^2$. Thus $\|x\|_2 \leq \|x\|_1 \leq \sqrt{n}\|x\|_2$.

1. $\|f\|_1 \not \sim \|f\|_2$ in $C([0,1])$. 
   But $\int_0^1 |f_n|\:dx \overset{C.S}{\leq} \left(\int_0^1 |f(x)|^2 \:dx\right) \underbrace{\left(\int_0^1 1^2\:dx\right)}_{=1}$. 
   Therefore $\|f\|_1 \leq \|f\|_2$. But $\not\exists C >0$ such that $\|f\|_2 \leq C\|f_1\|$.  
   To prove it, assume it does exist and consider the following graph:
   
   ![[desmos-graph (2).png|350]]
   
   We are assuming $\forall (f_n) \subset C([0,1])$ such that $\|f_n-f\|_1 \to 0$, $\|f_n-f\|_2 \to 0$. 
   But in the graph, $\|f_n\|_1 = \frac{1}{\sqrt{n}} \to 0$. $$\|f_n\|_2^2 = \int_0^1 |f_n(x)|^2\:dx = 2 \int_0^{1/n}n\sqrt{n}x\:dx = 2n^3\frac{1}{n^3} = 2 \neq 0$$

## Finite Dimensional Normed Spaces

>[!Theorem]
>For all *finite* dimensional vector spaces, all norms are equivalent.
##### Proof
Let $\dim X =: N$ and fix a basis $\{e_1,...,e_N\}$. Consider $\varphi: X \to \mathbb{K}^n$ given by $\varphi(x) = \varphi\left(\sum x_ie_i\right)= (x_1,...,x_N)$.

Also define $\|(x_1,...,x_n)\| := \|x\|$. 
It is enough to show on $\mathbb{K}^n$ that all norms are equivalent. *Specifically to $\|x\|_2$*.

**Upper Bound:**
$$\|(x_1,...,x_n)\| = \left\|\sum_{i=1}^N x_ie_i \right\| \leq \sum_{i=1}^N |x_i|\|e_i\| \leq M\cdot\|x\|_1\quad,\quad \text{for } M=\max(\|e_1\|,...,\|e_N\|)$$ 
 **Lower Bound:**
 Consider this function on $\mathbb{K}^n$: $f(x) := \|x\|$
 
>[!claim]
>$f:(\mathbb{K}^N, \|\cdot\|_2) \to (\mathbb{R}, |\cdot|)$ is continuous
###### Proof
$$|f(x) - f(y)| = |\|x\| - \|y\|| \overset{Rev\: \Delta-ineq}{\leq} \|x-y\| \leq C\|x-y\|_2$$
which is Lipschitz continuous and hence $f$ is continuous on $\mathbb{K}^n$.  $\square$

Now consider $S = \{x \in \mathbb{K}^n \:|\: \|x\|_2 = 1\}$. $S$ is clearly closed and bounded hence it is compact by [[Main Definitions|Fish's Heine-Borel Theorem]].

Since $f$ is continuous on $(\mathbb{K}^n, \|\cdot\|_2)$ from the claim above, it attains min/max due to Extreme Value Theorem. We only need the minimum though.

So $\exists x_0 \in S$ such that $\forall x \in S$, $f(x_0) = \|x_0\| \leq \|x\| = f(x)$. Note that $C = \|x_0\|>0$ so $x_0 \neq 0$.
Therefore $\forall x \in S, C\leq \|x\|$ and so $\forall x \in \mathbb{K}^n \setminus \{0\}$, $$C \leq \left\|\frac{x}{\|x\|_2}\right\|_2=1 \implies f(\frac{x}{})$$