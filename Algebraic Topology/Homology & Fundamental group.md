# Motivation

Recall that $H_0(X) \cong \mathbb{Z}^{\#\text{ of path-components of }X}$.

For $f:I \to X$, we can view it as 
1. a singular 1-simplex
2. path in $X$
If $f$ is a loop, $f(0) = f(1)\implies \partial f = f(1)-f(0) = 0\implies f \in \ker \partial$ is a cycle

# Commutator

>[!def] Commutator
>For a group $G$, the **commutator** of a  group, denoted $[G,G]$ is a subgroup $$[G,G]:= \{g^{-1}h^{-1}gh\:\:\:\: \forall g \in G. h \in G\}$$

>[!Theorem]
>$[G,G]$ is the smallest normal subgroup $H$ of $G$ such that $G/H$ is abelian.


# Abelianisation

>[!def] Abelianisation of $G$
>The **abelianisation of $G$**, denoted $G^{ab}$ is $G/[G,G]$ 

>[!Theorem] 
>Any homomorphism $\phi:G \to H$ with $H$ abelian can be factored through $\phi': G^{ab}\to H$.


# Homology and $\pi_1$ Equivalence

>[!Theorem] H Theorem 2.A.1
>1. Have a homomorphism $h:\pi_1(X,x_0) \to H_1(X)$
>2. If $X$ is path-connected, then $h$ induces an isomorphism $h':\pi_1^{ab}(X,x_0)\overset{\sim}{\longrightarrow}H_1(X)$

- We denote $f$ being **homologous** to $g$ (belonging to the same class in $H_1(X)$) by $f \sim g$

>[!lemma] 
>1. If $f,g:I \to X$ are paths such that $f(1) = g(0)$, then $[f\cdot g] \sim [f] + [g]$
>2. $f$ is the constant map $\implies f \sim 0$
>3. $f: I \to X$ a path. $f + \bar{f}$ is a boundary map $\implies f + \bar{f} \in \text{im }\partial$ 
>4. $f \simeq g \implies f \sim g$



##### Proof
###### 1.

![[Homology & Fundamental group-1761532183994.png|400]]

$[v_0,v_2]= f\cdot g$. So for $\sigma:\Delta^2 \to X$, $\sigma([v_0,v_2]) = f \cdot g$.
$\partial \sigma = \sigma[v_1,v_2] - \sigma[v_0,v_2]+ \sigma [v_0,v_1] = g - f \cdot g + f$
$\implies f + g - (f \cdot g) \in \text{im }\partial$
$\implies [f+g] \sim [f\cdot g]$ where $[f+g] = [f]+[g]$  $\square$

###### 2. 
TODO
###### 3. 
TODO
###### 4.
![[Homology & Fundamental group-1761533188425.png|350]]

Let $F: I\times I \to X$
$$\begin{align*}
\partial(\sigma_1-\sigma_2) &= \partial\sigma_1 - \partial \sigma_2 \\
&= \text{const}_{f(1)} - \text{diag} + f - (g - \text{diag} +\text{const}_{f(0)}) \\
&= f-g + \text{const}
\end{align*}$$
$\implies [f-g]+\text{const}\in \text{im }\partial$
$\implies [f-g]= [\text{const}] \overset{Lemma \:2}{=} [0]$
$\implies [f] = [g]\implies f \sim g$. $\square$

##### Proof (of Theorem 2.A.1)
###### 1. 
Now define $\phi: \pi_1(X,x_0) \to H_1(X)$ via $[f] \longmapsto [[f]]$ which is well-defined from lemma 4 from above: If $[f]= [g]$ then $f \simeq g$ so $[[f]] =[[g]]$.
$\phi([f][g])= \phi([f\cdot g]) = [[f\cdot g]] \overset{Lemma\:1}{=} [[f]] + [[g]]$
$\implies \phi$ is a homomorphism

Since $H_1(X)$ is abelian, $\phi$ factors through $\pi_1^{ab}(X,x_0)$ so we get $\phi_*: \pi_1^{ab}(X,x_0) \to H_1(X)$.

###### 2. 
Want $\psi_* : H_1(X)\to \pi_1^{ab}(X,x_0)$. So define $\psi: C_1(X) \to \pi_1^{ab}(X,x_0)$ via $\sigma \mapsto [\lambda_{\sigma(0)}\cdot \sigma \cdot \lambda^{-1}_{\sigma(1)}]$ where $\lambda_x$ is some path from $x_0$ to $x$. 
Want to prove that $\psi \circ \phi_* = \text{id}$, and $\phi_* \circ \psi = \text{id}$. 

>[!lemma]
>For $t \in \text{im }\partial_2$, $\psi(t) = [1]$.
###### Proof
Take $\sigma : \Delta^2 \to X$ such that $t=\partial\sigma$. Then 
$$\begin{align*}
\psi(\partial \sigma) = \psi(a_1 - (a_2)^{-1} + a_0) 
&= \psi(a_1)\, \psi(a_0)\, \psi(a_2) \\
&= [\lambda_{v_1} \cdot a_1 \cdot \lambda_{v_1}^{-1}]
   [\lambda_{v_0} \cdot a_0 \cdot \lambda_{v_1}^{-1}]
   \psi(a_2) \\
&= [\lambda_{v_1} \cdot a_1 \cdot \lambda_{v_2}^{-1} 
   \cdot \lambda_{v_0} \cdot a_0 \cdot \lambda_{v_1}^{-1} 
   \cdot (\lambda_{v_0} \cdot a_2^{-1} \cdot \lambda_{v_2})^{-1}] \\
&= [a_1 \cdot a_0 \cdot a_2] \\
&= [a_0 \cdot a_1 \cdot a_2] \\
&= [\text{const}] \\
&= [1]
\end{align*}
$$
$\square$ 
ADD THE DIAGRAM

So $\psi:X_1(X) \to \pi_1^{ab}(X,x_0)$. By lemma above, this induces $\psi_*: H_1(X) \to \pi_1^{ab}(X,x_0)$.
For a loop $f$, $\psi_*(\phi_*([f])) = \psi_*([[f]]) = [\lambda_{f(0)} \cdot f \cdot \lambda_{f(0)}^{-1}] =  [\lambda_{f(1)} \cdot f \cdot \lambda_{f(1)}^{-1}] = [f]$
$\implies \psi_* \circ \phi_* = \text{id}$. 

For the other implication consider the lemma:
>[!lemma] 
>1. If $\sigma: \Delta^1 \to X$, then $\phi_*(\psi_*(\sigma)) = [[\sigma- \lambda_{\partial\sigma}]]$ 
>2. If $\sigma \in C^1(X)$, then $\phi_*(\psi_*(\sigma)) = [[\sigma- \lambda_{\partial\sigma}]]$ 
>3. if $\sigma \in \ker \partial_1$, then $\phi_* \circ \psi_*(\sigma)= [[\sigma]]$
###### Proof
$\sigma \in H_1(X)$ where $(\sigma\in \ker\partial)$
$\implies \phi_* \circ \psi_*([[\sigma]]) = [[\sigma]]$ 
$\implies \phi_* \circ \psi_* = \text{id}$.

$\square$
