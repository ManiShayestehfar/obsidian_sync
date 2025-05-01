
# In Discrete RVs

>[!info] Definition
>The discrete RVs $X$ and $Y$ are **independent** if $\forall x,y\in \mathbb{R}$, the events $\{X=x\}$ and $\{Y=y\}$ are independent:
$$p_{XY}(x,y) = P(X=x,Y=y) = P(X=x) P(Y=y)  =P_X(x)P_Y(y)$$

>[!tip] Claim 
>The discrete RVs $X$ and $Y$ are independent $\iff$ $\forall x,y \in \mathbb{R}$
>$$F_{XY}(x,y) = P(X\leq x, Y \leq y) = P(X\leq x)P(Y\leq y) = F_X(x)F_Y(y)$$
- This only involves the CDF and so can be generalised

# In General RVs

>[!info] Definition
>The RVs $X_1,...,X_n$ are **independent** if $\forall x \in \mathbb{R}^n$
>$$\begin{align*}
>F_X(x_1,...,x_n) &:= P(X_1 \leq x_1, ...,X_n \leq x_n) \\[4pt]
>&= P(X_1 \leq x_1) ... P(X_n \leq x_n) \\[4pt]
&= F_{X_1}(x_1)...F_{X_n}(x_n)
\end{align*}$$

**Note:** For $\mathbb{R}$-valued RVs $X_1,...,X_n$ and $x_i \in \mathbb{R}$, $X_i \leq x_i \iff X \in (-\infty, x_i] =: B_i$.
If $X_i$ are independent then
$$\begin{align*}
P(X_1 \in B_1,...,X_n \in B_n) &= P(X_1 \leq x_1,...,X_n \leq x_n) \\[4pt]
&= P(X_1 \leq x_1)\:...\:P(X_n\leq x_n)\\[4pt]
&= P(X_1 \in B_1)\:...\: P(X_n \in B_n)  
\end{align*}$$
>[!tip] Claim
> The $\mathbb{R}$-valued RVs $X_1,...,X_n$ are independent $\iff$ for any Borel measurable sets $B_i \subset \mathbb{R}$,
> $$P(X_1\in B_1,...,X_n \in B_n) = P(X_1\in B_1) ... P(X_n \in B_n)$$
##### Proof

For $n=2$ and jointly continuous $(X,Y)$ with $f_{XY}$. Let $B_1 \times B_2 = \{(x,y) \in \mathbb{R}^2 : x \in B_1, y \in B_2\}$, then

$$ \begin{align*} P(X \in B_1, Y \in B_2) &= P((X,Y) \in B_1 \times B_2) \\[4pt]
&= \iint_{B_1 \times B_2} f_{XY}(x,y) \, dx \, dy \\[4pt] 
&= \iint_{\mathbb{R}^2} \mathbb{1}_{B_1}(x) \cdot \mathbb{1}_{B_2}(y) f_X(x) f_Y(y) \, dx \, dy \\[4pt] 
&= \int_{x=-\infty}^{\infty} \mathbb{1}_{B_1}(x) f_X(x) \left( \int_{y=-\infty}^{\infty} \mathbb{1}_{B_2}(y) f_Y(y) \, dy \right) \, dx \\[4pt] 
&= \left( \int \mathbb{1}_{B_1}(x) f_X(x) \, dx \right) \left( \int\mathbb{1}_{B_2}(y) f_Y(y) \, dy \right) \\[4pt] 
&= \left( \int_{B_1} f_X(x) \, dx \right) \left( \int_{B_2} f_Y(y) \, dy \right) \\[4pt] 
&= P(X \in B_1) P(Y \in B_2).\quad\quad \square \end{align*}$$
same follows for arbitrary $n$.


>[!tip] Claim
>If $X$ and $Y$ are independent [[Continuous RV]]s then they are jointly cont. and $f_{XY}(x,y) = f_X(x)f_Y(y)$. Conversely, if the joint density factors then $X$ and $Y$ are independent.

##### Proof
Assume $X,Y$ are continuous and independent.. Then
$$\begin{align*}
F_{XY}(x,y) = F_X(x) F_Y(y) &= \int_{-\infty}^x f_X(s)\:ds \int_{-\infty}^y \:f_Y(t)\:dt \\
&= \int_{-\infty}^x \int_{-\infty}^y f_X(s)f_Y(t)\:dt\:ds\\
\end{align*}$$
$\implies$ $X,Y$ are jointly continuous and $f_{XY}(x,y) = f_X(x)f_Y(y)$.

Conversely, if the joint density exists and it factors  
$$\begin{align*}
F_{XY}(x,y) &= \int_{-\infty}^x \int_{-\infty}^y f_{XY}(s,t)\\[4pt]
&= \int_{-\infty}^x \int_{-\infty}^y f_X(s)f_Y(t)\:dt\:ds\\[4pt]
&= \int_{-\infty}^x f_X(s)\:ds \int_{-\infty}^y f_Y(t)\:dt \\[4pt]
&= F_X(x)F_Y(y)
\end{align*}$$
$\implies X,Y$ are independent.

>[!tip] Claim
>Suppose $f_{XY}(x,y) = h(x)g(y)$, then $h \equiv \frac{1}{c}\cdot f_X$, $g \equiv c \cdot f_Y$ and it follows that $X,Y$ are independent 
##### Proof
$$\begin{align*}
f_X(x) = \int_{-\infty}^{\infty} f_{XY}(x,y)\:dy &= \int_{-\infty}^{\infty} h(x) g(y)\:dy\\[4pt]
&= h(x)\int_{-\infty}^{\infty}g(y) \:dy \\[4pt]
&= h(x) \cdot C\\[4pt]
\implies \:\: h(x) &= \frac{1}{C} \cdot f_X(x) \quad\quad\square
  
\end{align*}$$

>[!tip] Claim 
>If $X_1,...,X_n$ are independent $\mathbb{R}$-valued RVs and $h_i: \mathbb{R}\to \mathbb{R}$ (measurable), then with $Y_i = h_i(X_i)$, $Y_i$ are independent RVs.
##### Proof

If $h: \mathbb{R}\to \mathbb{R}$and $A \subset \mathbb{R}$, then the following tautology holds:
$$h(x) \in A \iff x \in h^{-1}(A) = \{s: h(s) \in A\}$$
Therefore, with $\tilde{y} = (y_1,...,y_n) \in \mathbb{R}^n$ and $\tilde{Y} = (Y_1,...,Y_n)$,
$$\begin{align*}
F_{\tilde{Y}}(\tilde{y}) = P(Y_1, \leq y_1,...,Y_n \leq y_n) &= P\left(\bigcap_1^n \{Y_i \leq y_i\}\right) \\[5pt]
&= P\left(\bigcap_1^n \{h_i(X_i) \in (-\infty, y_i]\}\right)\\[5pt]
&= P\left(\bigcap_1^n \{X_i \in \underbrace{h_i^{-1}(-\infty, y_i]\}}_{B_i}\right) \\[5pt]
&= \prod_1^n P(X_i \in B_i) \\[5pt]
&= \prod_1^n P(h_i(X_i) \in (-\infty, Y_i])\\[5pt]
&= \prod P(Y_i \leq y_i) \\[5pt]
&= \prod F_{Y_i}(y_i)
\end{align*}$$
$\implies Y_i$ are independent RVs. $\square$



## Examples

### Bivariate Standard Normal with $\rho \in (-1,1):$

$$f_{ZW}(z,w) = \frac{1}{2\pi\sqrt{1- \rho^2}}e^{-\frac{1}{2(1-\rho^2)}(z^2 - 2\rho z w + w^2)}$$
Recall we saw that:
1. $f_Z(z) = \frac{1}{\sqrt{2\pi}}e^{-z^2/2}$, and $f_W(w) = \frac{1}{\sqrt{2\pi}}e^{-w^2/2}$
2. $Z,W$ are independent $\iff \:f_{ZW} = f_Z \otimes f_W$ 

So if $Z,W$ are independent then 
$$\frac{1}{2\pi\sqrt{1-\rho^2}} = f_{ZW}(0,0) = f_Z(0)f_W(0) = \frac{1}{\sqrt{2\pi}} \frac{1}{\sqrt{2\pi}} = \frac{1}{2\pi}$$
$\implies \rho = 0$  and the converse is also true. Therefore the density factors, and so does the CDF.



