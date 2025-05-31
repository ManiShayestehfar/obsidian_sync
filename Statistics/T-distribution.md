A **T-distribution** with $n$ d.o.f is the distribution of the cont. RV $T = Z/ \sqrt{W/n}$  where $Z \sim N(0,1)$ is ind. of $W \sim \chi_n^2$ 

- The T-distribution is symmetric

-  pdf $f(x)$  $\forall x \in \mathbb{R}$ is 
$$f(x) = \frac{\Gamma(\frac{n+1}{2})}{\sqrt{\pi n} \:\:\Gamma(\frac{n}{2})} \:\left(1+\frac{x^2}{n}\right)^{-\frac{n+1}{2}}$$

- $E[T] = 0$ for $n > 1$, otherwise undefined
- $$\text{Var}(T) = \begin{cases}
\frac{n}{n-2} & n > 2  \\[3pt]
\infty & 1<n<2  \\[3pt]
\text{undefined} & \text{otherwise}
\end{cases} $$
