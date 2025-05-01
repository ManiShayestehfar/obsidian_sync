
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