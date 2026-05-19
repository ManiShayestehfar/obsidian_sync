# Measure-preserving System

> [!Definition]
> Let $(X, \mathcal B, \mu)$ be a probability space. An invertible measurable map $T : X \to X$ is called **measure-preserving** if $\mu(T^{-1}A) = \mu(A)$ for every $A \in \mathcal B$.
>
> The quadruple $(X, \mathcal B, \mu, T)$ is called an **invertible measure-preserving system**.


# Koopman Operator

> [!Definition] Definition 2 (Koopman operator)
> Let $(X, \mathcal B, \mu, T)$ be an invertible measure-preserving system. The associated **Koopman operator** $U_T : L^2(X, \mu) \to L^2(X, \mu)$ is defined by $U_T f = f \circ T$.

> [!Proposition] Proposition 1
> Let $(X, \mathcal B, \mu, T)$ be an invertible measure-preserving system. Then the Koopman operator $U_T f = f \circ T$ is unitary on $L^2(X, \mu)$.
##### Proof

First we check that $U_T$ is an isometry. For $f \in L^2(X, \mu)$,
$$
 \|U_T f\|_2^2 = \int_X |f(Tx)|^2\,d\mu(x).
$$

Since $T$ preserves $\mu$, $\int_X |f(Tx)|^2\,d\mu(x) = \int_X |f(x)|^2\,d\mu(x)$. Therefore $\|U_T f\|_2 = \|f\|_2$.

Because $T$ is invertible and $T^{-1}$ is also measure-preserving, the inverse of $U_T$ is $U_T^{-1}f = f \circ T^{-1}$. Thus $U_T$ is a surjective isometry. Hence $U_T$ is unitary. $\square$

