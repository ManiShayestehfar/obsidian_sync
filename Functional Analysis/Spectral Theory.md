# Motivation

Eigenvalues of a matrix $T$ over $\mathbb{C}$ are $\lambda \in \mathbb{C}$ with $\det(\lambda I -T)= 0$.
i.e. the $\lambda \in \mathbb{C}$ such that the linear operation $\lambda I - T: \mathbb{C}^n \to \mathbb{C}^n$ is *not* invertible.
Spectral theory generalises this.

# Spectrum

>[!Definition]
>$X$ a normed vector space. The **spectrum** of $T \in \mathcal{L}(X,X)$ is 
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
>Then any *nonzero* $x \in \ker(\lambda I -T)$ is called a **$\lambda$-eigenvector**.
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
The function $f: \mathbb{C}\to \mathcal{L}(X,X)$ given by $\lambda \mapsto \lambda I -T$ is continuous and 
$$\sigma(T) = f^{-1}(\mathcal{L}(X,X)\setminus GL(X))$$
where $\mathcal{L}(X,X)\setminus GL(X)$ is a closed set due to the proposition for [[General Linear Group]].
So $\sigma(T)$ is closed. $\square$

##### 1.

>[!Definition]
>The **resolvent set** of $T\in\mathcal{L}(X,X)$ is 
>$$\rho(T) = \mathbb{C}\setminus \sigma(T).$$
>Let $R_T: \rho(T) \to \mathcal{L}(X,X)$ given by $\lambda \mapsto (\lambda I - T)^{-1}$ be the **resolvent operator**

>[!Lemma]
>Let $\varphi\in \mathcal{L}(X,X)'$ and let $f_\varphi= \varphi \circ R_T: \rho(T) \to \mathbb{C}$.
>Then $f_\varphi$ is analytic on the open set $\rho(T)$.
###### Proof
If $\lambda,\lambda_0 \in \rho(T)$ then 
$$\begin{align*}
\frac{f_\varphi(\lambda) - f_\varphi(\lambda_0)}{\lambda - \lambda_0} &= \frac{\varphi(R_T(\lambda)) - \varphi(R_T(\lambda_0))}{\lambda - \lambda_0} \\[3pt]
&= \varphi \left(\frac{R_T(\lambda) - R_T(\lambda_0)}{\lambda - \lambda_0}\right) \\[3pt]
&= \varphi \left(\frac{(\lambda I -T)^{-1}-(\lambda_0I-T)^{-1}}{\lambda - \lambda_0}\right) \\[3pt]
&= \varphi \left(\frac{(\lambda_0 I -T)^{-1}(\lambda_0 I - T - \lambda I + T)(\lambda I-T)^{-1}}{\lambda - \lambda_0}\right) \\[3pt]
&= -\varphi((\lambda I -T)^{-1}(\lambda_0I-T)^{-1})
\end{align*}$$
Since $\varphi$ is continuous, and $T \mapsto T^{-1}$ is continuous (by proposition in [[General Linear Group]]), we have
$$\lim_{\lambda \to \lambda_0} \frac{f_\varphi(\lambda) - f_\varphi(\lambda_0)}{\lambda - \lambda_0} = - \varphi((\lambda_0I-T)^{-2})$$
$\square$

>[!Corollary]
>Let $X \neq \{0\}$ be Banach over $\mathbb{C}$, and $T \in \mathcal{L}(X,X)$. Then $\sigma(T)\neq \varnothing$.
>
###### Proof
Suppose $\sigma(T)=\varnothing$. So $\rho(T)=\mathbb{C}$.
Thus $f_\varphi:\mathbb{C} \to \mathbb{C}$ is analytic on all of $\mathbb{C}$ for all $\varphi \in \mathcal{L}(X,X)'$.

We claim that $f_\varphi$ is also bounded.
Since $f_\varphi$ is analytic, it is continuous, and so there is $M>0$ with 
$$|f_\varphi(\lambda)| \leq M \qquad \text{whenever }\: |\lambda|\leq \|T\|.$$
If $|\lambda| > \|T\|$, then 
$$\begin{align*}
|f_\varphi(\lambda)| &= |\varphi((\lambda I-T)^{-1})| \\
&= \left|\varphi\left(\sum_{k=0}^\infty \frac{1}{\lambda^{k+1}}T^k\right)\right| \\
&\leq \|\varphi\|\: \sum_{k=0}^\infty \frac{\|T\|^k}{|\lambda|^{k+1}} \\
&= \frac{\|\varphi\|}{|\lambda|-\|T\|} \longrightarrow 0 \qquad\text{as }|\lambda| \to \infty
\end{align*}$$
So $f_\varphi$ is bounded on $\mathbb{C}$, and hence it is constant by *Liouville's Theorem*.

>[!Theorem] Liouville's Theorem
>If $f:\mathbb{C}\to \mathbb{C}$ is bounded and analytic on all of $\mathbb{C}$, then $f$ is constant.

Since $|f_\varphi(\lambda)|\to 0$ as $|\lambda|\to \infty$, we have $f_\varphi \equiv 0$. But this is true for *all* $\varphi \in \mathcal{L}(X,X)$'.

By Hahn-Banach, $R_T(\lambda)=0$ for all $\lambda \in \mathbb{C}$.
So $(\lambda I -T)^{-1}=0$ which is a contradiction, as $0 \in \mathcal{L}(X,X)$ is not invertible. $\square$



---
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



# Spectral Mapping Theorem

>[!Theorem]
>Let $X$ be Banach over $\mathbb{C}$. Let $T \in \mathcal{L}(X,X)$. Then
>$$\sigma(p(T))= p(\sigma(T)) = \{ p(\lambda) \:|\: \lambda \in \sigma(T)\}$$
>for all polynomials $p(t) \in \mathbb{C}[t]$.
##### Proof
If $p(t) =\text{constant}$, then $\sigma(p(T)) = \sigma(cI)= \{c\}$, and $p(\sigma(T))= \{c \in \mathbb{C}\:|\: \lambda \in \sigma(T)\} = \{c\}$ as $\sigma(T)\neq\varnothing$.

Suppose $p(t)$ is not constant. Let $\mu \in \mathbb{C}$. By the fundamental theorem of algebra
$$\mu - p(t)= \alpha(t-\lambda_1)^{m_1}(t-\lambda_2)^{m_2}\cdots(t-\lambda_n)^{m_n}$$
where $\lambda_i \in \mathbb{C}$ are the distinct roots of $\mu - p(t)$ and so $\mu = p(\lambda_i)$ for some $i$.
Since $\psi:\mathbb{C}[t]\to \mathcal{L}(X,X)$ given by $t \mapsto T$ is an algebra homomorphism, we have
$$\mu I-p(T)= \alpha(T-\lambda_1I)^{m_1}\cdots(T-\lambda_n I)^{m_n}$$
**Note:** If $T_1,...,T_n \in \mathcal{L}(X,X)$ pairwise commute, then $T_1...T_n$ is invertible $\iff$ each $T_i$ is invertible.

Hence, $\mu \in \sigma(p(T)) \iff \mu I - p(T)$ is not invertible $\iff$ $T-\lambda_iI$ is not invertible for some $i$ $\iff$ $\lambda_i \in \sigma(T)$ $\iff$ $\mu=p(\lambda_i)\in p(\sigma(T))$.  $\square$

## Example

Consider $Tx := (I-L+L^2)x = (x_1-x_2+x_3,x_2-x_3+x_4,...)$
We saw above that $\sigma(L) = \overline{D(0,1)}$. So by the spectral mapping theorem,
$$\sigma(T) = \{1-\lambda  +\lambda^2 \in \mathbb{C} \:|\: |\lambda|\leq1 \}$$


# Spectral Radius

>[!Definition]
>Let $X$ be Banach over $\mathbb{C}$. The **spectral radius** of $T \in \mathcal{L}(X,X)$ is 
>$$r(T)=\sup_{\lambda \in \sigma(T)} |\lambda|$$
>Importantly, $r(T) \leq \|T\|$
##### Explanation of inequality

$\sigma(T) \subseteq \{\lambda \in \mathbb{C} \:|\: |\lambda| \leq \|T\|\}$.
Strict inequality may hold. e.g. $T:\mathbb{C}^2 \to \mathbb{C}^2$ with $\|\cdot\|_2$ with
$$Tx = \begin{pmatrix}0 & 1 \\ 0 & 0\end{pmatrix}\binom{x_1}{x_2}.$$
Then $\det(\lambda I -T)= \det \left(\begin{smallmatrix} \lambda & 1 \\ 0 & \lambda \end{smallmatrix} \right) = \lambda^2=0$. 
So $\sigma(T) = \{0\}$, so $r(T)=0$, yet
$$\|T\|= \sup_{x_1^2+x_2^2=1}\|Tx\|_2 = \sup_{x_1^2+x_2^2+1}\sqrt{|x_2|^2}= 1.$$

## Example

We want to find $r(T)$ for $T:\ell^2\to \ell^2$ with $T(x)=(x_1-x_2+x_3,x_2-x_3+x_4,...)$.
We already saw before that $\sigma(T) = \{1 - \lambda + \lambda^2 \:|\: |\lambda|\leq 1\}$.
So $r(T) \leq 3$. 
Since $1-(-1)+(-1)^2=3$, then $r(T)=3$.


## Gelfand's Theorem

>[!Theorem]
>Let $X$ be Banach over $\mathbb{C}$. Let $T \in \mathcal{L}(X,X)$. Then 
>$$r(T) \leq \|T^n\|^{1/n}\qquad \forall n \geq1$$
>and 
>$$r(T) = \lim_{n\to\infty} \|T^n\|^{1/n}.$$
##### Proof
By spectral mapping theorem
$$\sigma(T^n)= \{\lambda^n \in \mathbb{C} \:|\: \lambda \in \sigma(T)\}$$
Hence $r(T^n) = r(T)^n$ for all $n \geq 1$.
So $r(T)= r(T^n)^{1/n} \leq \|T^n\|^{1/n}$.
Thus $r(T) \leq \liminf_{n\to \infty} \|T^n\|^{1/n}$. 

We will now prove that $\limsup_{n\to\infty} \|T^n\|^{1/n}\leq r(T)$, which completes the proof.
Let $\varphi \in \mathcal{L}(X,X)'$ and $f_\varphi:\rho(T) \to \mathbb{C}$ with $f_\varphi(\lambda) = \varphi((\lambda I - T)^{-1})$.
We previously proved that $f_\varphi$ is analytic on the open set $\rho(T)$, and in particular on the set $\{\lambda \in \mathbb{C} \:|\: |\lambda|> r(T)\}$ by definition of $r(T)$.
If $|\lambda|> \|T\|$, then from before
$$f_\varphi(\lambda) = \sum_{k=0}^\infty \frac{1}{\lambda^{k+1}}\varphi(T^{k}) \tag{$\ast$}$$
![[Spectral Theory-1777457984783.png]]
Hence by analytic construction $(\ast)$ holds for all $|\lambda|> r(T)$.
In particular,
$$\lim_{n\to\infty} \frac{1}{|\lambda|^{n+1}}|\varphi(T^n)|=0 \qquad \forall \varphi \in \mathcal{L}(X,X), \:\:\forall|\lambda|> r(T)$$
So $\exists M_{\varphi,\lambda}>0$ such that 
$$\frac{1}{|\lambda|^{n+1}}|\varphi(T^n)| < M_{\varphi,\lambda}$$
So $|\varphi(\frac{T^n}{\lambda^{n+1}})| < M_{\varphi,\lambda}$.
So $\left\{\frac{1}{\lambda^{n+1}}T^n \:|\:  n\geq 1\right\}$ is weakly bounded in $\mathcal{L}(X,X)$. So by Principle of Uniform Boundedness and Hahn-Banach theorem, the set is bounded in norm.
So $\exists M_\lambda >0$ such that 
$$\left\|\frac{1}{\lambda^{n+1}}T^n\right\| < M_\lambda \qquad \forall n \geq1$$
So $\|T^n\|^{1/n}\leq |\lambda|\:(|\lambda|M_\lambda)^{1/n}$, and 
$$\limsup_{n\to \infty} \|T^n\|^{1/n}\leq |\lambda| \qquad \forall |\lambda|> r(T)$$
So 
$$\limsup_{n\to\infty} \|T^n\|^{1/n} \leq r(T) \qquad\square$$



### Proposition

>[!Proposition]
>Let $H$ be a Hilbert space over $\mathbb{C}$ and $T \in \mathcal{L}(H,H)$.
>If $T$ is self-adjoint (i.e. $T^*=T$ or *Hermitian*), then $\|T\|=r(T)$
##### Proof
Recall that $\|T^*T\|= \|T\|^2$. Hence $\|T^2\|=\|T\|^2$. So $\|T^{2^n}\|= \|T\|^{2^n}$.
By Gelfand's Theorem
$$\begin{align*}
r(T) &= \lim_{n\to\infty} \|T^n\|^{1/n}\\
&= \lim_{n\to\infty} \|T^{2^n}\|^{1/2^n}\\
&= \|T\|   \qquad\square
\end{align*}$$


# Point, Continuous, Residual Spectrum

$$\begin{align*}
\sigma_p(T) &= \{\lambda \in \mathbb{C} \:|\: \lambda I - T \text{ not injective}\} \\ &= \{\text{eigenvalues of }T\}\tag{Point Spectrum} \\[10pt]
\sigma_c(T) &= \left\{\lambda \in \mathbb{C} \:\:\middle|\:\: \substack{\large\lambda I -T \text{ injective} \\[5pt] \large \lambda I-T \text{ NOT surjective} \\[5pt] \large \overline{\text{im }(\lambda I -T)} = X} \right\} \tag{Continuous Spectrum} \\[10pt]

\sigma_r(T) &= \left\{\lambda \in \mathbb{C} \:\middle| \substack{\large\lambda I-T \text{ NOT injective} \\[5pt]\large \lambda I -T \text{ surjective} \\[5pt]\large \overline{\text{im }(\lambda I -T)} \neq X}  \:\right\} \tag{Residual Spectrum}
\end{align*} $$
So by definition
$$\sigma(T) = \sigma_p(T) \sqcup \sigma_c(T) \sqcup \sigma_r(T)$$
## The Necessity for Distinction

1. If $\lambda \in \sigma_c(T)\cup\sigma_r(T)$, we can define an inverse to the operator $\lambda I-T:X \to Z$ where $Z =\text{im }(\lambda I-T)$. However, $\lambda I -T$ is not invertible.

2. If $\lambda \in \sigma_c(T)$ then the domain of the inverse to $\lambda I -T$ is dense in $X$.

3. If $\lambda \in \sigma_p(T)$ there is no notion of inverse

4. If $\dim(X) < \infty$, then $\sigma(T)=\sigma_p(T)$, and $\sigma_c(T)=\sigma_r(T) = \varnothing$.

## Examples: Left and Right Shift

>[!Proposition]
>If $1 \leq p < \infty$, then $L:\ell_\mathbb{C}^p \to \ell_\mathbb{C}^p$ has 
>$$\begin{align*}
\sigma_p(L)&= \{\lambda \in \mathbb{C}\:|\: |\lambda|<1\} \\[4pt]
\sigma_c(L) &= \{\lambda \in \mathbb{C} \:|\: |\lambda|=1\} \\[4pt]
\sigma_r(L) &= \varnothing
\end{align*}$$
##### Proof
Since $\|L\|=1$, then $\sigma(L) \subseteq \{\lambda \in \mathbb{C} \:|\: |\lambda|\leq 1\}$.
###### Point Spectrum
$$\begin{align*}
\lambda \in \sigma_p(L)
&\Longleftrightarrow \exists \text{ non-zero } x \in \ell^p \text{ with } Lx = \lambda x \\[3pt]
&\Longleftrightarrow (x_2, x_3, \ldots) = (\lambda x_1, \lambda x_2, \ldots), \quad x \neq 0 \\[3pt]
&\Longleftrightarrow x_2 = \lambda x_1,\quad x_3 = \lambda x_2,\quad \ldots \\[3pt]
&\Longleftrightarrow x = x_1(1,\lambda,\lambda^2,\ldots) \in \ell^p, \quad x_1 \neq 0 \\[3pt]
&\Longleftrightarrow |\lambda| < 1.
\end{align*}$$
So $\sigma_p(L)$ is as claimed and by compactness of $\sigma(L)$ we have 
$$\sigma(L) = \{\lambda \in \mathbb{C} \:|\: |\lambda|\leq 1\}$$
So $\sigma_c(L) \cup \sigma_r(L) = \{\lambda \in \mathbb{C}\:|\: |\lambda|=1\}$.

###### The Rest
Let $|\lambda|=1$. 

>[!Claim]
>$$\overline{\text{im }(L-\lambda I)} = \ell^p$$

It is enough to show the image contains $\ell_F$ since $\overline{\ell_F}= \ell^p$ (for $p\neq \infty$).
So let $y = (y_1,y_2,...,y_N,0,0,...)\in \ell_F \subseteq\ell^p$.
We need $x \in \ell^p$ with: $(\lambda I - L)x = y$.
i.e. $(\lambda x_1-x_2 , \lambda x_2-x_3,...)=(y_1,y_2,...)$.
Let $x = (x_1,x_2,...,x_N,0,0,...)$.
Then
$$\begin{bmatrix}  
\lambda & -1 & 0 & 0 & \cdots & 0 \\  
0 & \lambda & -1 & 0 &\cdots & 0 \\  
\vdots & & \ddots & \ddots & \vdots & 0 \\  
0 & \cdots & \cdots & & \lambda & -1 \\  
0 & \cdots & \cdots & &0 & \lambda  
\end{bmatrix}  
\begin{bmatrix}  
x_1 \\  
\vdots \\  
\vdots \\  
\vdots \\  
x_N  
\end{bmatrix}  
=  
\begin{bmatrix}  
y_1 \\  
\vdots \\  
\vdots \\  
\vdots \\  
y_N  
\end{bmatrix}.$$
And since the coefficient matrix has determinant $\lambda^n\neq0$, we can solve for $x \neq 0$. $\square$

>[!Proposition]
>If $1 < p < \infty$, then $R:\ell_\mathbb{C}^p \to \ell_\mathbb{C}^p$ has
>$$\begin{align*}
\sigma_p(L)&= \varnothing \\[4pt]
\sigma_c(L) &= \{\lambda \in \mathbb{C} \:|\: |\lambda|=1\} \\[4pt]
\sigma_r(L) &= \{\lambda \in \mathbb{C} \:|\: |\lambda|<1\}
\end{align*}$$
##### Proof
Since $\|R\|=1$, we have $\sigma(R) \subseteq \{\lambda \in \mathbb{C} \:|\: |\lambda|\leq 1\}$.

###### Point Spectrum
$$\begin{align*}  
\lambda \in \sigma_p(R)  
&\Longleftrightarrow \exists x \neq 0 \text{ with } Rx = \lambda x \\[3pt]  
&\Longleftrightarrow (0,x_1,x_2,\ldots) = (\lambda x_1,\lambda x_2,\ldots) \\[3pt]  
&\Longleftrightarrow \lambda x_1 = 0,\quad \lambda x_2 = x_1,\quad \lambda x_3 = x_2,\quad \ldots  
\end{align*}$$
- If $\lambda \neq 0$, then $x=0$. 
- If $\lambda =0$, then $x=0$.
So $\sigma_p(R)=\varnothing$ so $\sigma(R)=\sigma_c(R) \cup \sigma_r(R)$.

###### The Rest

>[!Exercise]
>Let $X$ be a normed vector space, and $Y \subseteq X$ a subspace. Then 
>$$\overline{Y}=X \iff \{\varphi\in X' \:|\: \varphi(y)=0 \:\:\:\forall y \in Y\}= \{0\}$$

Recall that $\ell^q \cong (\ell^p)'$ when $\frac{1}{p}+\frac{1}{q}=1$ given by the maps $y \mapsto \varphi_y$,
where $\varphi_y(x) = \sum_{n=1}^\infty x_ny_n$.
So 
$$\begin{align*}
\lambda \in \sigma_r(R)
&\Longleftrightarrow \operatorname{im}(\lambda I - R) \text{ is not dense}
\qquad \left(\text{already saw } \sigma_p = \varnothing\right) \\[0.5em]
&\Longleftrightarrow \text{there is nonzero } y \in \ell^q
\text{ with } \varphi_y(x)=0
\quad \forall x \in \operatorname{im}(\lambda I - R) \\[0.5em]
&\Longleftrightarrow \exists y \in \ell^q \setminus \{0\}
\text{ with }
\varphi_y\bigl((\lambda I - R)e_i\bigr)=0
\quad \forall i \geq 1
\qquad \left(\operatorname{span}\{e_i\}\text{ dense in }\ell^p\right).
\end{align*}$$
where $\varphi_y(0,\ldots,\lambda,-1,0,\ldots)=0   \quad \Longleftrightarrow \quad   \lambda y_i - y_{i+1}=0.$ Then
$$\begin{align*}
&\Longleftrightarrow \exists y \in \ell^q \setminus \{0\}
\text{ with }
\lambda y_i - y_{i+1}=0
\quad \forall i \\[0.5em]
&\Longleftrightarrow \exists y \in \ell^q \setminus \{0\}
\text{ with }
Ly = \lambda y \\[0.5em]
&\Longleftrightarrow \lambda \in \sigma_p(L),
\qquad \left(L:\ell^q \to \ell^q\right) \\[0.5em]
&\Longleftrightarrow |\lambda| < 1,
\qquad \text{by the previous proposition.}
\end{align*}$$
Hence $\sigma_r(R) = \{\lambda \in \mathbb{C} \:|\: |\lambda|<1\}$.
Since $\sigma(R)$ is closed, we have $\sigma(R)=\{\lambda \in \mathbb{C} \:|\: |\lambda|\leq 1\}$. Hence
$$\sigma_c(R)=\{\lambda \in \mathbb{C} \:|\: |\lambda|=1\}.$$
$\square$

