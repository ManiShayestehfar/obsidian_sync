# Motivation

>[!example]
>$(C([a,b]), \|\cdot\|_\infty)$ and $(C([a,b]), \|\cdot\|_\infty)_p$  for $1\leq p < \infty$ are not the same
##### Proof
Need to show there exists $(f_n) \in C([0,1])$ such that:
1. $f_n \to 0$ with $\|\cdot\|_1$
2. $f_n \not\to 0 \in \|\cdot\|_\infty$ 

Consider this example
![[Screenshot 2026-03-02 at 11.32.13 am.png|250]]

$\|f_n - 0 \|_1 = \int_{0}^1 |f_n(x)|dx = \text{Area of } \Delta = \frac{1}{n} \to 0$.
But $\|f_n-0 \|_\infty = \|f_n\|_\infty = 1 \neq 0$ 


# Definition

>[!definition] Banach Space
>A metric space $(X,d)$ is a **Banach Space** if it is *normed* and *complete*.

## Examples

1. $(\mathbb{K}, \|\cdot\|)$ is complete $\implies$ It is Banach
2. $\bb$

$\$