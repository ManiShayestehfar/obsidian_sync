- We often model random quantities that take a continuous set of possible values. e.g. lifetime, temperature, height of individuals, etc.
- In this case the [[Probability Mass Function|pmf]] cannot be used to specify such a distribution. In fact for such RVs usually $P(X=x) = 0$ for all $x \in X(\Omega)$. We need [[Cumulative Distribution Function |CDF]].

>[!info] Definition
>An RV $X: \Omega \to \mathbb{R}$ with CDF $F$ is called a **continuous RV** if there exists an integrable function $f \geq 0$ called the *density*, aka the **pdf (probability density function)** of $X$ such that
>$$F(x) = \int_{-\infty}^x f(x') dx'$$

# Comments on Properties

For continuous RV $X$ with CDF $F$ and pdf $f$,

1. $X$ is absolutely convergent
2. $f$ is not uniquely defined, but it is unique whenever it is continuous. 
3. $F$ is a cont. function, and by Fundamental theorem of calculus, for any $x$ where $f$ is cont. at $x$, $F'(x) = f(x)$.
4. If $F_X$, the CDF of some RV $X$, is differentiable and $f = F_X'$ is Riemann-integrable, then $X$ is a cont. RV and $f$ is its density (same holds if $F_X$ is cont. and differentiable everywhere except on a finite set of points).
5. *What can we compute with the density?*
	 For $a,b$,  
$$\begin{align*}
\int_a^b f(t)\:dt &= \int_{-\infty}^b f(t)\:dt - \int_{-\infty}^a f(t)\:dt \\[5pt]
&= F(b) - F(a) \\[5pt]
&= P(X\leq b) - P(X \leq a) \\[5pt]
&= P(X \in [a,b])
\end{align*}$$
$\implies$ For any (measurable) set $B \subset \mathbb{R}$, $P(X \in B) = \int_B f(t) \: dt$.  
**$\implies f$ determines the distribution of $X$**

6. See below
>[!tip] Claim
>For *any* RV $X$, and $b \in \mathbb{R}$, 
>$$P(X=b) = F(b) - \lim_{n\to\infty} F(b - \tfrac{1}{n}) = F(b) - F(b^-)$$
>![[Pasted image 20250413214540.png]]
##### Proof
$\{\omega : X(\omega) = b\} = \bigcap_n \underbrace{\{b- \tfrac{1}{n} < X \leq b\}}_{B_n}$. 
![[Pasted image 20250413221447.png|300]]

$$\begin{align*}
\implies P(X=b) &= P\left(\bigcap_n B_n\right) \\[6pt]
&= \lim_{n\to\infty} P(B_n) \\[6pt]
&= \lim_{n \to \infty} P(X \in (b-\tfrac{1}{n},b])\\[6pt]
&= \lim_{n \to \infty}[F(b) - f(b - \tfrac{1}{n})] \quad \square
\end{align*}$$

7. If $X$ is a cont. RV, then for $a<b$:
$$P(X \in [a,b]) = P(X \in (a,b)) = P(X \in (a,b]) = \int_a^b f(x') \:dx'$$
which is true since $P(X \in \{a,b\}) = P(X=a) + P(X=b) = 0$.
---

>[!tip] Corollary
>a. $P(X=b) = 0$ if $F$ is continuous at $b$.
>b. If $X$ is a cont. RV then for any $x \in \mathbb{R}$, $P(X=x) = 0$. 
>c. The CDF always determines the pmf. In general, the pmf does not specify the CDF. For example, if $F_x$ is cont., then $p_X = 0$.  

>[!tip] Claim
>If $f$ is a pdf then:
>1. $f \geq 0$
>2. $\int_{-\infty}^{\infty} f(x)\: dx = 1$
>   
>   Conversely, if $f$ is integrable and it satisfies (1) and (2), then $f$ is a pdf of a cont. RV $X$ with CDF $F(x) = \int_{-\infty}^x f(x') \: dx'$ 
##### Proof
If $f$ is a pdf, then (1) follows from the definition, but for (2):
$$\int_{-\infty}^{\infty} f(x)\:dx = \lim_{x \to \infty} \int_{-\infty}^x f(x') \: dx' = \lim_{x \to \infty} F(x) = 1$$

To prove the converse, we need to show that $F(x) := \int_{-\infty}^x f(x') \:dx'$ satisfies properties (1)-(3) of a CDF.


# Example

## Uniform Distribution

$U$ has a $\text{Uniform}(0,1)$ dist. if it has a density
$$f(u) = \mathbb{1}_{[a,b]}(u) = \begin{cases}
1 & u \in [0,1] \\[4pt]
0 & u \not\in [0,1]
\end{cases}$$

```tikz
\begin{document}

\begin{tikzpicture}[scale=2]
  % Axes
  \draw[->, thick] (-0.5,0) -- (2,0) node[right] {$u$};
  \draw[->, thick] (0,-0.5) -- (0,1.5);

  % Function f
  \draw[green, thick] (-0.5,0) -- (0,0); % Left zero
  \draw[green, thick] (0,1) -- (1,1);    % Top line from 0 to 1
  \draw[green, thick] (1,0) -- (2,0);    % Right zero

  % Dots at transitions
  \filldraw[green] (0,1) circle (1pt);
  \filldraw[green] (1,0) circle (1pt);
  \filldraw[red] (0.7,0) circle (1pt);
  
  % Labels
  \node at (0,-0.2) {$0$};
  \node at (1,-0.2) {$1$};
  \node at (-0.1,1) {$1$};
  \node at (0.7,-0.15) {\textcolor{red}{u}};
  \node[green] at (1.1,1.1) {$f$};
\end{tikzpicture}

\end{document}
```

$$\implies F(u) = \int_{-\infty}^u f(t) \:dt = \begin{cases}
0 & u \leq 0 \\[3pt]
\int_0^u 1 = u & u \in (0,1) \\[3pt]
1 & u \geq 1
\end{cases}$$

```tikz
\begin{document}

\begin{tikzpicture}[scale=2]
  % Axes
  \draw[->, thick] (-0.5,0) -- (2,0) node[right] {$u$};
  \draw[->, thick] (0,-0.5) -- (0,1.5);

  % Function f
  \draw[green, thick] (-0.5,0) -- (0,0); 
  \draw[green, thick] (0,0) -- (1,1);   
  \draw[green, thick] (1,1) -- (2,1);    
  
  % tiks at transitions
  \draw[thick] (1,0.05) -- (1,-0.05);  % Tick at x = 1
  \draw[thick] (0.05,1) -- (-0.05,1);  % Tick at y = 1
  
  % Labels
  \node at (0,-0.2) {$0$};
  \node at (1,-0.2) {$1$};
  \node at (-0.1,1) {$1$};
  \node[green] at (2.1,1) {$F$};
\end{tikzpicture}

\end{document}
```
- Note that $F'(x) = f(x)$ except for $x \in \{0,1\}$
- For $a<b$,  $f(u) = \frac{1}{b-a}\cdot \mathbb{1}_{[a,b]}(u)$


# Functions of RVs

>[!example] Theorem
>Suppose $X$ is a continuous RV with:
>1. pdf $f_X$
>2. $g$ a continuously differentiable and strictly monotone function on interval $I \supset X(\Omega)$ .
>   
>Then $Y := g(X)$ is a continuous RV with pdf 
>$$f_y(Y) = f_X(g^{-1}(y)) \left|\frac{d}{dy} g^{-1}(y)\right| = f_X(g^{-1}(y)) \left|\frac{1}{g'(g^{-1}(y))}\right|$$
##### Proof
Since $g$ is strictly monotone, $g^{-1}$ exists and is also monotone. Also since $g$ is cont. diff., $g^{-1}$ is also cont. diff. and by chain rule:
$$\begin{align*}
1 &= \frac{d}{dy}y\\
&=\frac{d}{dy} g(g^{-1}(y))\\
&= g'(g^{-1}(y)) \:\frac{d}{dy} g^{-1}(y)\\
\implies \frac{d}{dy}(g^{-1}(y)) &= \frac{1}{g'(g^{-1}(y))}.
\end{align*}$$

- *Assumption:* $F_X$ is differentiable everywhere. Same argument holds if $F_X$ is diff everywhere except for a finite number of points. 

$$\begin{align*}
F_Y(y) &= P(Y \leq y) \\[4pt]
&= P(g(X) \leq y)
\end{align*}$$
- Assume $g \uparrow \implies g^{-1} \uparrow$, and so $\forall y \in Y(\Omega)$
	$$\begin{align*}
F_Y(y) &= P(X \leq g^{-1}(y)) \\[4pt]
&= F_X(g^{-1}(y))
\end{align*}$$
And by chain rule $F_Y$ is diff. and 
$$\begin{align*}
f_Y(y) &= F'_X(g^{-1}(y)) \cdot \frac{d}{dy}g^{-1}(y) \\
&= f_X(g^{-1}(y))\cdot \left|\frac{d}{dy}g^{-1}(y)\right|
\end{align*}$$
- Assume $g \downarrow \implies g^{-1} \downarrow$, and so $\forall y \in Y(\Omega)$
	$$\begin{align*}
F_Y(y) &= P(X \geq g^{-1}(y)) \\[4pt]
&= 1 - P(X < g^{-1}(y)) \\[4pt]
&= 1 - F_X(g^{-1}(y))
\end{align*}$$
And again by chain rule, given $F_Y$ is diff.
$$\begin{align*}
f_Y(y) &= F'_X(g^{-1}(y)) \cdot \frac{d}{dy}g^{-1}(y) \\[4pt]
&= -f_X(g^{-1}(y))\cdot \frac{d}{dy}g^{-1}(y) \\[4pt]
&= f_X(g^{-1}(y))\cdot \left|\frac{d}{dy}g^{-1}(y)\right|
\end{align*}$$
$\square$ 


## Examples

### Standard Normal RV 

$X$ A standard normal RV and for $\sigma > 0$ and $\mu \in \mathbb{R}$ define $Y = \sigma \cdot X + \mu$.
The claim here is that $Y$ is continuous RV and 
$$f_Y(y) = \frac{1}{\sqrt{2\pi \sigma^2}} e^{-\frac{(y - \mu)^2}{2\sigma^2}}$$
##### Proof
$\sigma > 0$ so $g(x) = \sigma x + \mu$ is strictly increasing for $x \in \mathbb{R} = X(\Omega)$.

By theorem above, $Y = g(X)$ is a continuous RV and 
$$f_Y(y) = f_X(g^{-1}(y)) \cdot \left|\frac{d}{dy}g^{-1}(y)\right|$$
where $x = g^{-1}(y) = \frac{y- \mu}{\sigma}$ and $f_X(x) = \frac{1}{\sqrt{2\pi}} e^{-\frac{x^2}{2}}$ so
$$f_Y(y) = \frac{1}{\sqrt{2\pi}} e^{-\frac{(y - \mu)^2}{2\sigma^2}} \cdot \frac{1}{\sigma}$$
$\square$


### Uniform Distribution
$U \sim U(0,1)$ and $V = \frac{1}{U}$, find $f_V$.

$V = g(U)$ where $g(u) = \frac{1}{u}$ is smooth and strictly decreasing on $(0,1) = U(\Omega)$. Hence by theorem
$$f_V(v) = f_U\left(\frac{1}{v}\right) \left|-\frac{1}{v^2}\right| = \begin{cases}
\tfrac{1}{v^2} & v > 1  \\[5pt]
0 & v \leq 1
\end{cases}$$

![[Pasted image 20250419153913.png|600]]


### Different Normal Dist. 

$Z \sim N(0,1)$, so $f_Z(z) = \frac{1}{\sqrt{2\pi}} e^{-\frac{z^2}{2}}$ and let $Y = Z^2 = g(Z)$ where $g(z)=z^2$. Find $f_Y$.

$g^{-1}(y) = \sqrt{y}$, and using the Theorem for $y > 0$

$$f_Y(y) = \frac{1}{\sqrt{2\pi}} e^{-\frac{y}{2}} \cdot \left|\frac{1}{2\sqrt{y}}\right|$$
Sanity check:
$$\begin{align*}
\int_{-\infty}^{\infty} f_Y(y)\:dy &= \int_{0}^\infty \frac{1}{\sqrt{2\pi}} e^{-\frac{y}{2}} \cdot \frac{1}{2\sqrt{y}} \:dy \tag{\small $t :=\sqrt{y}\implies dt = \tfrac{dy}{2\sqrt{y}}$} \\[4pt]
&= \int_{0}^\infty \frac{1}{\sqrt{2\pi}}e^{-t^2/2}\:dt \\[4pt]
&= \frac{1}{2} \quad {\color{aquamarine} (!)}
\end{align*}$$
- *What is the problem?* $g(z) = z^2$ is not strictly monotone on $\mathbb{R}= Z(\Omega)$.
Instead of theorem we can find $f_Y$ directly:

![[Pasted image 20250419164123.png|600]]




## Special Cases

### Distribution of $U = F_X(X)$ 

>[!tip] Claim
> Let $X$ be a RV with a continuous $F=F_X$ strictly increasing on $X(\Omega)$ (e.g. $X$ has a positive density). Then $F(X) \sim U(0,1)$.  
##### Proof

$F$ is cont. and strictly increasing so in this case, $F^{-1}:(0,1) \to \mathbb{R}$ is well-defined: 

![[Pasted image 20250419221105.png|350]]

Also $F^{-1}$ is strictly increasing on $(0,1)$ and therefore $\forall p \in (0,1)$ 
$$F(X) \leq p \iff X \leq F^{-1}(p)$$
Therefore with $U = F(X)$ and $p \in (0,1)$
$$\begin{align*}
P(U \leq p) &= P(F(X) \leq p) \\[4pt]
&= P(X \leq F^{-1}(p))\\[4pt]
&= F(F^{-1}(p)) \\[4pt]
&= p
\end{align*}$$


### The null distribution of the p-value

The **p-value** is used to quantify the level of surprise, or deviation from the null-hypothesis. 

![[Pasted image 20250419222333.png]]

By the Claim above, $F_T(T) \sim U(0,1)$ therefore
$$P(F_T(T) \leq 0.05) = 0.05$$
More generally, for any test statistic $T$, with a continuous and strictly increasing $F_T$ on $T(\Omega)$, the p-value $\sim U(0,1)$ under the null hypothesis. 


### Sampling given a uniform sample

>[!warning] Motivation
>$U = F(X) \sim U(0,1) \implies X = F^{-1}(U) \sim F.$

>[!tip] Claim 
>Suppose the CDF $F$ has an inverse $F^{-1}$ on $(0,1)$ (i.e. again that $F$ is cont. strictly increasing on $I = F^{-1}(0,1)$), and let $U \sim U(0,1)$.
>
>Define $X = F^{-1}(U)$, then $F_X \equiv F$. i.e. $X \sim F$.

![[Pasted image 20250419225720.png]]


 >[!tip] Generalisation of Claim Above 
 >Let $F$ be a CDF and $U \sim U(0,1)$ RV. Then $Q_F(U) \sim F$ 
##### Proof
We showed in [[Quantiles]] that $\forall p \in (0,1), x \in \mathbb{R}:$
$$Q_F(p) \leq x \iff p \leq F(x)$$
Therefore,
$$\begin{align*}
\{\omega: Q_F(U(\omega)) \leq x\} &= \{\omega: U(\omega) \leq F(x)\} \\[7pt]
\implies P(Q_F(U(\omega)) \leq x) &= P(U \leq F(x)) \\[7pt]
&= F(x)
\end{align*}$$

>[!tip] Corollary
>If $U_1,...,U_n$ is a sample from the $U(0,1)$ distribution, then $Q_F(U_1),...,Q_F(U_n)$ is a sample from the distribution determined by the CDF $F$. 


# Functions of Jointly Continuous RVs

Suppose $X,Y$ have a joint density $f_{XY}$, and $T:\mathbb{R}^2 \to \mathbb{R}^2$ is *bijective* and *differentiable*, and define the random point
$$(U,V):= T(X,Y).$$
Let $(u,v) = T(x,y) = (x+y, x-y)$, and $\delta >0$ so 

![[Pasted image 20250504123246.png]]

$S_\delta$ is a square with $|S_\delta| = \delta^2$. $T(S_\delta)$ is a square with sides of length $\sqrt{2}\delta$, so $|T(S_\delta)| = 2\delta^2$.

$$\begin{align*}
\implies P((X,Y) \in S_\delta) &= \iint_{S_\delta} f_{XY}(s,t) \:ds\:dt \\[4pt]
&= \iint_{S_\delta} (f_{XY}(s,t) - f_{XY}(x,y))\:ds\:dt \:\:+\:\: \iint_{S_\delta} f_{XY}(x,y)\:ds\:dt \\[4pt]
&= R_\delta |S_\delta| \quad+ \quad f_{XY}(x,y)|S_\delta|
\end{align*}$$
where $R_\delta(x,y) := \frac{1}{|S_\delta|} \iint_{S_\delta} (f_{XY}(s,t) - f_{XY}(x,y))\:ds\:dt$.

- *Assuming* $f_{XY}$ is continuous, $R_\delta \underset{\delta\to 0}{\longrightarrow} 0$. 
- Similarly, assuming $f_{UV}$ exists and is continuous,  
$$\begin{align*}
P((U,V) \in T(S_\delta)) &= \iint_{T(S_\delta)} f_{UV}(q,r)\:dq\:dr \\
&= R'_\delta |T(S_\delta)| \quad+\quad f_{UV}(u,v) |T(S_\delta)|
\end{align*}$$
	where $R'_\delta \underset{\delta\to 0}{\longrightarrow} 0$. 

![[Pasted image 20250504124337.png|600]]
![[Pasted image 20250504124512.png|600]]
![[Pasted image 20250504124601.png|600]]

![[Pasted image 20250504124830.png|600]]

### Theorem of Density of function of a random point

>[!example] Theorem (Density of function of a random point)
>Suppose $T : \underset{\text{open}}{D} \in \mathbb{R}^2 \to R \underset{\text{open}}{R} \subset \mathbb{R}^2$ is bijective. Also $T$ is differentiable on $D$ with $J_T \neq 0$. (i.e. $T^{-1}$ is differentiable).
>Suppose $(X,Y)$ is jointly continuous with density $f_{XY}$ which vanishes outside of $D$, and let $(U,V) = T(X,Y)$. Then $(U,V)$ is jointly continuous and $\forall (u,v) \in R$,
>$$\begin{align*}
f_{UV} &= f_{XY}(T^{-1}(u,v)) |J_{T^{-1}}(u,v)| \\[5pt]
&= f_{XY}(T^{-1}(u,v))|J_T(T^{-1}(u,v))|
\end{align*}$$
### A Remark

![[Pasted image 20250506213625.png]]

### Examples

#### $V = X+Y$ 

$(u,v)  = T(x,y) = (x,x+y)$ a linear map.
$\implies (x,y) = T^{-1}(u,v) = (u,v-u)$

$\implies J_{T^{-1}} = \left|\begin{pmatrix}1 & 0 \\ -1 & 1\end{pmatrix}\right| = 1$

$\implies f_{UV}(u,v) = f_{XY}(u,v-u) \cdot 1$. So the marginal density is 

![[Pasted image 20250506213233.png|500]]

- Since $V = X+Y$, we rediscovered the pdf of $X+Y$.

#### Standard Bivariate Normal

Recall $Z,W$ and $\rho \in (-1,1)$ with $f_{ZW}(z,w)$ as befo
