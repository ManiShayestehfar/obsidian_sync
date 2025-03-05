>[!info] Definition
>A **random variable** is a *measurable* function
>$$X: \Omega \to \mathbb{R}$$
>Some times the range being $\bar{\mathbb{R}} := \mathbb{R}\cup \{-\infty, \infty\}$ 

>[!info] Definition
>A random variable is **discrete** if its range, $X(\Omega)$, is a countable set.


# Independent Random Variables

> [!info] Definition
> The discrete random variables $X$ and $Y$ are independent if $\forall x,y \in \mathbb{R}$, the events $\{X = x\}$ and $\{Y=y\}$ are independent. i.e 
> $$p_{XY}(x,y) = P(X=x,Y=y) = P(X=x)P(Y=y) = p_X(x)p_Y(y)$$

- If $X$ and $Y are independent then $P(X=x | Y=y) = P(X=x)$ 

>[!tip] Claim 1
>The discrete RVs $X$ and $Y$ are independent $\iff$ 
>$$P(X\in A, Y\in B) = P(X\in A)P(X\in B)\quad \forall A,B\subset \mathbb{R}$$
##### Proof
If the left hand-side works then clearly the joint pmf factors. **EXERCISE** for the other half of proof

>[!tip] Claim 2
>The discrete RVs $X$ and $Y$ are independent $\iff$ 
>$$P(X\leq x, Y\leq y) = P(X \leq x)P(Y \leq y)\quad \forall x,y\in \mathbb{R}$$ 
##### Proof
Claim 1 implies Claim 2. **EXERCISE** for Claim 2 to 1.

