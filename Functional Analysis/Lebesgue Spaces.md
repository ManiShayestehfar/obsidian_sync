# $L^p$
Let $1 \leq p < \infty$

$(L^p([a,b]), \|\cdot\|_p)$ is the completion of $(C([a,b]), \|\cdot\|_p)$ 

Let $d\mu$ be a Lebesgue measure on $\mathbb{R}$.
$$L^p([a,b]) = \left\{\begin{gather} \text{Lebesgue} \\ \text{Measureable} \\ f:[a,b] \to \mathbb{K}\end{gather} \: \Bigg | \: \int_a^b |f(x)|^p \:d\mu < \infty \right\}$$
- $\|f(x)\|_p$ is only a semi-norm here as $f(x) = 0$ only if $x = 0$ "almost everywhere". i.e. $\mu\left(\{x|f(x) \neq 0\}\right) = 0$.
	- Recall that $\mu(A) = 0$ iff $\forall \varepsilon >0$, $\exists I_n$ intervals on $\mathbb{R}$ such that:
		1. $A \subset \bigcup I_n$ finitely
		2. $\sum_n^\infty |I_n| < \infty$


## Fisher-Riesz

>[!Theorem] Fisher-Riesz Theorem
>$(L^p, \|\cdot\|_p)$ is the completion of $(C([a,b]), \|\cdot\|_p)$

*Remark:* As expected, $(L^p, \|\cdot\|_\infty)$ is NOT the completion of $C([a,b]), \|\cdot\|_\infty)$.
