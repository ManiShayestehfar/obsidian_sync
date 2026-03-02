
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

