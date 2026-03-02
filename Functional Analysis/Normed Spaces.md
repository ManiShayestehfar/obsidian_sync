
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





