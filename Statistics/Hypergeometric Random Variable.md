
A **Hypergeometric RV** $X$ models the number of red balls in a sample of $m$ balls drawn *without replacement* from a box of $r$ red balls and $n-r$ black balls.

- 3-parameter family $(r,n,m)$

- RV $X(\Omega) \subset \{0,1,...,\min\{r,m\}\}$ where all samples of size $m$ are equally likely

- $|\Omega| = \begin{pmatrix}n \\ m \end{pmatrix}$ 
- For $k \in \{0,1,...,\min\{r,m\}\}$ there are $\begin{pmatrix}r \\ k \end{pmatrix}$ ways to choose $k$ red balls out of $r$
- For each choice of $k$ red balls, there are $\begin{pmatrix}n-r \\ m-k \end{pmatrix}$ ways to choose black balls.
$$\implies P(X=k) = \frac{\begin{pmatrix}r \\ k \end{pmatrix} \begin{pmatrix}n-r \\ m-k \end{pmatrix}}{ \begin{pmatrix}n \\ m \end{pmatrix}}$$