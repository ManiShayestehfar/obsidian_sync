- We often model random quantities that take a continuous set of possible values. e.g. lifetime, temperature, height of individuals, etc.
- In this case the [[Probability Mass Function|pmf]] cannot be used to specify such a distribution. In fact for such RVs usually $P(X=x) = 0$ for all $x \in X(\Omega)$. We need [[Cumulative Distribution Function | CDF]].

>[!info] Definition
>An RV $X: \Omega \to \mathbb{R}$ with CDF $F$ is called a **continuous RV** if there exists an integrable function $f \leq 0$ called the *density*, aka the **pdf (probability density function)** of $X$ such that
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












