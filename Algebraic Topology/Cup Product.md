The idea is that we want a map: $H^i(X) \times H^j(X) \overset{}{\longrightarrow}H^{i+j}(X)$


>[!def] Cup Product
>Given $\varphi \in C^k(X;R)$, $\psi \in C^\ell(X;R)$, the **cup product** $\varphi \smile\psi \in C^{k+\ell}(X;R)$ is defined as $$\varphi \smile \psi(\sigma):= \varphi(\sigma|_{[v_0,...,v_k]})\cdot \psi(\sigma|_{[v_0,...,v_{k+\ell}]})$$
>where $\sigma:\Delta^{k+\ell}\to X$ is a singular simplex

To get $* \smile *: H^k(X;R)\times H^\ell(X;R)\overset{}{\longrightarrow}H^{k+\ell}(X;R)$, we need
1. $\varphi,\psi \in \ker \delta$, then $\varphi \smile \psi \in \ker \delta$.
2. $\delta \varphi \smile \psi = \delta \theta$ for some $\theta$, and $\varphi \smile \delta \psi = \delta \theta'$ for some $\theta'$.

>[!lemma] H Lemma 3.6
>$$\delta(\varphi \smile \psi) = \delta\varphi\smile \psi \:+\: (-1)^k \phi\smile \delta\psi$$
>for $\varphi \in C^{k}(X;R)$ and $\psi \in C^\ell(X;R)$.

1. $\delta \varphi = 0, \delta \psi = 0$ \implies $\delta(\varphi \smile \psi)=0$
2. Suppose $\varphi = \delta \varphi$ and $\psi = \delta \psi$. Then $\varphi \smile \psi = \delta(\varphi \smile \psi) \pm \varphi \smile \delta \psi$
   If $\psi \in \ker \delta$, then, $\delta \psi = 0 \implies \delta \varphi \smile \psi = \delta (\varphi \smile \psi)$ 

## Properties

- *Associativity:* $(\varphi \smile \psi)\smile \theta = \varphi (\psi \smile \theta)$
- *Distributive:* $(\varphi_1 \smile \varphi_2)\smile \psi= \varphi_1 \smile \psi + \varphi_2 \smile \psi$
- If $1 \in R$, can define $[1] \in H^0(X;R)$ which takes $0$-simplices to $1$. i.e. $[1]\smile [1]=[1]$.
- Same formula of cup products works for simplicial cohomology
  $f: H^i(X;R)\overset{\cong}{\longrightarrow}H^i_{Simp}(X;R)$ where $f(\varphi \cup \psi) = f(\theta) \cup f(\psi)$
- When $A$ and $B$ are open subsets of $X$, our subcomplexes of $X$, we get a **relative cup product**
  $H^k(X,A;R)\times H^\ell(X,B;R)\overset{}{\longrightarrow}H^{k+\ell}(X, A\cup B;R)$  coming from the expected chain group isomorphism $C^n(X,A\cup B;R)\overset{\cong}{\longrightarrow}C^n(X,A+B;R)$

>[!Proposition] H Prop 3.10
>Given $f:X \to Y$, then we get $f^*:(\alpha \smile \beta)= f^*(\alpha)\smile f^*(\beta)$ for $f^*:H^n(Y;R)\overset{}{\longrightarrow}H^n(X;R)$.
>Same works for the relative case.


>[!Theorem] H Theorem 3.11
>Suppose $R$ is commutative, $\alpha \in H^k(X;R), \beta\in H^\ell(X;R)$, then $$\alpha \smile \beta = (-1)^{kl}\:\beta \smile \alpha$$

