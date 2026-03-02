
# Compactness
Let $(X,d)$ be a metric space.

>[!definition] 
>$Y \subset X$ is **compact** if for all open covers of $Y$, there exists a finite subcover.
>i.e. $\exists\: (U_\alpha)_{\alpha \in I}$ such that $Y \subset \bigcup_{\alpha = 0}^N U_\alpha$ for some $N > 0$.


# Totally Boundedness

>[!Definition]
>$Y \subset (X,d)$ is **totally bounded** if $\forall \varepsilon > 0$, there exists a finite collection of $B_\varepsilon$ which covers $Y$.


# Fish's Heine-Borel Theorem

>[!Theorem]
>$(X,d)$ a metric space and $Y \subset X$. Then the following are equivalent:
>1. $Y$ is compact
>2. Every sequence in $Y$ has a convergent subsequence (i.e. $Y$ is sequentially compact)
>3. $Y$ is complete + totally bounded

