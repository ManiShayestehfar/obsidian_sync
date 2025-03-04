
A **Hypergeometric RV** $X$ models the number of red balls in a sample of $m$ balls drawn *without replacement* from a box of $r$ red balls and $n-r$ black balls.

- 3-parameter family $(r,n,m)$

- RV $X(\Omega) \subset \{0,1,...,\min\{r,m\}\}$ where all samples of size $m$ are equally likely

- $|\Omega| = \begin{pmatrix}n \\ m \end{pmatrix}$ 
- For $k \in \{0,1,...,\min\{r,m\}\}$ there are $\begin{pmatrix}r \\ k \end{pmatrix}$ ways to choose $k$ red balls out of $r$
- For each choice of $k$ red balls, there are $\begin{pmatrix}n-r \\ m-k \end{pmatrix}$ ways to choose black balls.
$$\implies P(X=k) = \frac{\begin{pmatrix}r \\ k \end{pmatrix} \begin{pmatrix}n-r \\ m-k \end{pmatrix}}{ \begin{pmatrix}n \\ m \end{pmatrix}}$$

### Example: Convicted Twins

![[convicted_twins.png|450]]

> *Is there evidence of a genetic link, or is the sibling more likely to be convicted if their convicted twin is identical?*

- 13 red balls (monozygotic twins)
- 17 black balls (dizygotic twins)
- We randomly sample 12 balls

$X \sim HG(r=13, n=30,m=12)$

$$\begin{align*} P(X \geq 10) &= \sum_{k=10}^{12} P(X=k) \\[6pt] &= \sum_{k=10}^{12} \frac{\begin{pmatrix}13 \\ k \end{pmatrix} \begin{pmatrix}17 \\ 12-k \end{pmatrix}}{ \begin{pmatrix}30 \\ 12 \end{pmatrix}} \\ &\approx 0.000465\\ \end{align*}$$
