
# Compactness
Let $(X,d)$ be a metric space.

>[!definition] 
>$Y \subset X$ is **compact** if for all open covers of $Y$, there exists a finite subcover.
>i.e. $\exists\: (U_\alpha)_{\alpha \in I}$ such that $Y \subset \bigcup_{\alpha = 0}^N U_\alpha$ for some $N > 0$.


# Totally Boundedness

>[!Definition]
>$Y \subset (X,d)$ is **totally bounded** if $\forall \varepsilon > 0$, there exists a finite collection of $B_\varepsilon$ which covers $Y$.

- In a metric space: totally bounded $\implies$ bounded

# Fish's Heine-Borel Theorem

>[!Theorem]
>$(X,d)$ a metric space and $Y \subset X$. Then the following are equivalent:
>1. $Y$ is compact
>2. Every sequence in $Y$ has a convergent subsequence (i.e. $Y$ is sequentially compact)
>3. $Y$ is complete + totally bounded

## Generalised Heine-Borel Theorem

>[!Theorem]
>If $Y \subset (\mathbb{K}^N, \|\cdot\|)$. $Y$ is compact $\iff$ $Y$ is closed + bounded.



# Closed Ball

>[!Definition] Closed Ball
>
Let $(X,\|\cdot\|)$ be a [[Normed Spaces|normed vector space]] over $\mathbb{K}$. The **Closed ball** is
$$\bar{B}(0,1) = \{x \in X \:|\: \|x\| < 1\}$$

# Dense

>[!Definition] Dense
>$Y\subseteq X$ a metric space is **dense** in $X$ if $\bar{Y} = X$.
>Equivalently, $\forall x\in X, \exists (y_n) \subset Y$ such that $y_n \to x$.




