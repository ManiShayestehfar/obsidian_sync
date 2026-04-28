# Motivation

Eigenvalues of a matrix $T$ over $\mathbb{C}$ are $\lambda \in \mathbb{C}$ with $\det(\lambda I -T)= 0$.
i.e. the $\lambda \in \mathbb{C}$ such that the linear operation $\lambda I - T: \mathbb{C}^n \to \mathbb{C}^n$ is *not* invertible.
Spectral theory generalises this.

# Spectrum

>[!Definition]
>$X$ a normed vector space. The **spectrum** of $T \in \mathcal{L}(X)$ is 
>$$\sigma(T) = \{\lambda \in \mathbb{K} \:|\: \lambda I  - T \text{ not invertible }\}$$

## Observations

1. $\lambda I - T$ is not invertible $\iff$ $\lambda I -T$ not bijective $\iff$ Not surjective/injective 
2. If $\dim(X) < \infty$ then $X/\ker T \cong \text{im }T$. So $\dim X = \dim(\ker T)+\dim(\text{im }T)$. So
   $$T \text{ injective } \iff T \text{ surjective }$$
3. If $\dim X = \infty$, then (2) fails.
	- e.g. $L :\ell^2 \to \ell^2$ given by $x \mapsto (x_2,x_3,...)$ surjective but not injective
	- e.g. $R: \ell^2 \to \ell^2$ given by $x \mapsto (0,x_1,x_2,...)$ injective but not surjective

4. To show $T \in \mathcal{L}(X,X)$ is invertible with inverse $S$, we need to check 
   $$ST = I, \qquad TS=I$$
   
5. If $X$ is Banach and $T \in \mathcal{L}(X,X)$ is invertible, then by the [[Open Mapping Theorem|Bounded Inverse Theorem]], $T^{-1}\in \mathcal{L}(X,X)$


## Eigenvalue

>[!Definition]
>$\lambda \in \mathbb{K}$ is an **eigenvalue** of $T \in \mathcal{L}(X,X)$ if $\lambda I -T$ is not injective. (i.e. $\ker (\lambda I -T)\neq \{0\}$)
>
>Then any *nonzero* $x \in \ker(\lambda I -T)$ is called a $\lambda$-eigenvector.
>So $Tx=\lambda x$ where $x\neq0$.


## Properties of Spectrum

>[!Theorem]
>Let $X \neq \{0\}$ be Banach over $\mathbb{C}$, and let $T \in \mathcal{L}(X,X)$.
>Then the spectrum $\sigma(T)$ is
>1. non-empty
>2. compact (closed + bounded)
>3. $\sigma(T) \subseteq \{\lambda \in \mathbb{C}\:|\: |\lambda|\leq \|T\|\}$
#### Proof
##### 3.
If $S,T \in \mathcal{L}(X,X)$, then $\|STx\|\leq \|S\|\|Tx\|\leq \|S\|\|T\|x$.
So $\|ST\| \leq \|S\|\|T\|$. In particular $\|T^n\|\leq \|T\|^n$.

>[!Proposition]
>Let $X$ be Banach over $\mathbb{C}$, and $T \in \mathcal{L}(X,X)$. Then
>$$\sigma(T) \subseteq \{\lambda \in \mathbb{C} \:|\: |\lambda| \leq \|T\|\}$$
###### Proof
We need to show that if $|\lambda| > \|T\|$, then $\lambda I - T$ is invertible. A good approach is to guess what the inverse is and check it.
**Guess:** $(\lambda I -T)^{-1} = \frac{1}{\lambda}(I - \frac{1}{\lambda}T)^{-1} \overset{??}{=} \sum_{k=0}^\infty \frac{1}{\lambda^{k+1}}T^k$.

Let $S_n = \sum_{k=0}^n \frac{1}{\lambda^{k+1}}T^k \in \mathcal{L}(X,X)$. Since 
$$\sum_{k=0}^\infty \left\|\frac{1}{\lambda^{k+1}} T^k\right\| \leq \frac{1}{|\lambda|}\sum_{k=0}^\infty \left(\frac{\|T\|}{|\lambda|}\right)^k < \infty \tag{since $|\lambda|>\|T\|$} $$
we have $S_n \to S = \sum_{k=0}^\infty \frac{1}{\lambda^{k+1}}T^k \in \mathcal{L}(X)$, since $X$ is complete and so $\mathcal{L}(X,X)$ is complete, and absolutely convergent series are convergent in Banach spaces.

Also
$$\begin{align*}
S_n(\lambda I - T) &= I - \frac{1}{\lambda^{n+1}} T^{n+1} \longrightarrow I\\
(\lambda I - T) S_n &= I - \frac{1}{\lambda^{n+1}} T^{n+1} \longrightarrow I
\end{align*}$$
so $S$ is the inverse of $\lambda I - T$   $\square$

##### 2.
Since we showed boundedness in part (3), we just need to show $\sigma(L)$ is closed.
##### 1.





### Example

Let $L:\ell^2 \to \ell^2$ be the left shift operator: $Lx = (x_2,x_3,...)$.
Then $\|L\| = 1$, so the theorem says: $\sigma(L) \subseteq \{\lambda \in \mathbb{C}\:|\: |\lambda| \leq 1\}= D^1$. 
If $|\lambda| <1$, then $x = (1,\lambda,\lambda^2,\lambda^3,...)\in \ell^2$ and 
$$(\lambda I - L)x = (\lambda,\lambda^2,\lambda^3,...) - (\lambda,\lambda^2,\lambda^3,...)=0$$
Since $\lambda I-L$ is not injective, then $\lambda$ is an eigenvalue. So $\{\lambda \in \mathbb{C}\:|\: |\lambda| < 1\}\subseteq \sigma(L)$ and by the theorem $\sigma(L)$ is closed, so 
$$\sigma(L) = \{\lambda \in \mathbb{C}\:|\: |\lambda| \leq 1\}= D^1.$$
#### Remark
If $\lambda =1$, then $\lambda$ is NOT an eigenvalue of $L$. 
Consider $(\lambda I - L)x =0 \implies (\lambda x_1-x_2,\lambda x_2-x_3,...)=0$
$\implies x_2=\lambda x_1$ 
$x_3 = \lambda x_2 \implies x_3= \lambda^2 x_1$
$x_4=\lambda x_3 \implies x_4=\lambda^3 x_1$
$\vdots$
$\implies x = x_1(1,\lambda,\lambda^2,...)$
But $(1,\lambda,\lambda^2,...) \not\in\ell^2$,so $x_1=0$. But then $x=0$ so $\lambda I-L$ is injective (but not surjective).

