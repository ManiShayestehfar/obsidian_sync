
# Closed and Boundedness of N.S

>[!Corollary]
>Every compact normed vector space is closed and bounded

- This can easily be extended to metric spaces

##### Proof

$Y \subset (\mathbb{K}^n, \|\cdot\|_2)$. Since $\mathbb{K}^n$ is compact, then so is $Y$ and therefore $Y$ is sequentially compact.
By [[Main Definitions|Fish's Heine-Borel]], $Y$ compact implies $Y$ is totally bounded, which means that we can make a ball big enough $B(0,M)$ that covers all of $Y$. Hence $Y$ is *bounded*.

Suppose $(x_n)\subset Y$ converges in $\mathbb{K}^n$. i.e. $x_n \to x$ in $\mathbb{K}^n$. 
But there exists a subsequence $(x_{n_k}) \subset (x_n)$ which also converges with $x_{n_k} \to y$. But $x=y$