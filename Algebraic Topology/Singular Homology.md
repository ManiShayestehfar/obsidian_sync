# n-Simples, n-Chain, boundary homomorphism

>[!def]
>A **singular n-simplex** is a continuous map $\sigma:\Delta^n \to X$

>[!Def]
>A **singular n-chain** is a finite formal sum $\sum_\alpha k_\alpha \sigma_\alpha$ for $k_\alpha \in \mathbb{Z}$, $\sigma_\alpha$ a singular n-simplex. Write $C_n(X)$ for the set of all singular **n-chains**.

- $C_n(X)$ is a **free $\mathbb{Z}$-module** with basis the set of all singular n-simplices $\sigma:\Delta^n \to X$.

>[!Def] 
>The **singular chain complex** for $X$ is $$\cdots\:\overset{\partial_{n+2}}{\longrightarrow} C_{n+1} \overset{\partial_{n+1}}{\longrightarrow}C_{n} \overset{\partial_{n}}{\longrightarrow}C_{n-1} \overset{\partial_{n-1}}{\longrightarrow}\cdots C_{1} \overset{\partial_{1}}{\longrightarrow}C_{0} \overset{\partial_{0}}{\longrightarrow}0.$$
>Similarly the **nth-singular homology group** of $X$ is $H_n(X) = \ker \partial_{n}/\text{im }\partial_{n+1}$

- If $f:X\to Y$ is a homomorphism, then $H_n(X) \cong H_n(Y)$  $\forall n \geq 0$


## Propositions

>[!proposition]
>If $X = \sqcup_\alpha X_\alpha$ where each $X_\alpha$ is non-empty and path-connected, then $H_n(X) \cong \oplus_\alpha \:H_n(X_\alpha)$
##### Proof

$\sigma:\Delta^n \to X$ is a singular n-simplex. Since $\sigma$ is continuous, $\sigma(\Delta^n)$ lies in a single $X_\alpha$, so $C_n(X) \cong \oplus_\alpha\: C_n(X_\alpha)$.

The boundary maps $\partial_n$ preserve the direct sum as $\partial_nC_n(X_\alpha) \subseteq C_{n-1}(X_\alpha)$. Hence $\ker \partial_n$ and $\text{im }\partial_{n+1}$ also split into direct sums, thus $H_n(X) \cong \oplus_\alpha\: H_n(X_\alpha)$. $\square$


>[!proposition]
>If $X$ is non-empty and path-connected, then $H_0(X)\cong \mathbb{Z}$. 
>Hence for any space $X= \sqcup_\alpha X_\alpha$ as above, $H_0(X) \cong \oplus_\alpha \:\mathbb{Z}$ with one copy of $\mathbb{Z}$ for each path component of $X$.
##### Proof
$H_0(X) = \ker \partial_0/\text{im }\partial_1 = C_1(X)/\text{im }\partial _1$ where we recall that $\partial_0$ is the zero map.

Define $\varepsilon:C_0(X) \to \mathbb{Z}$ by $\sum_\alpha k_\alpha \sigma_\alpha \mapsto \sum_\alpha k_\alpha$ where $\sigma_\alpha:\Delta^0 \to X$. This is a homomorphism and is surjective as $X$ is non-empty. We need to show $\ker \varepsilon = \text{im }\partial_1$.

###### $\supseteq$
Let $\sigma:\Delta^1\to X$ be a singular $1$-simplex. Then $\varepsilon(\partial_1\sigma) = \varepsilon(\sigma|_{[v_1]} - \sigma|_{[v_0]}) = 1-1=0$. So $\text{im }\partial_1 \subseteq \ker \varepsilon$ 

###### $\subseteq$
Now suppose $\sum_\alpha k_\alpha \sigma_\alpha \in \ker \varepsilon$. Then $\sum_\alpha k_\alpha=0$. Here $\sigma_\alpha$ are singular $0$-simplices. i.e. continuous maps $\Delta^0=\{1\} \to X$. We can thus identify each point of $X$ with a $0$-simplex.

Choose basepoint $x_0 \in X$. $\forall \alpha$, choose path $\tau_\alpha$ in $X$ from $x_0$ to $\sigma_\alpha(1)$.

![[Singular Homology-1760149374470.png|200]]

Let $\sigma_0$ be the singular $0$-simplex with $\sigma_0(1)= x_0$. View $\tau_\alpha$ as a singular $1$-simplex. Then $\partial_1\tau_\alpha=\sigma_\alpha - \sigma_0$. Hence
$$\begin{align*}
\partial_1\left(\sum_\alpha k_\alpha \tau_\alpha\right) &= \sum_\alpha k_\alpha (\sigma_\alpha - \sigma_0) \\
&= \sum_\alpha k_\alpha \sigma_\alpha - \underbrace{\left(\sum_\alpha k_\alpha\right)}_{=0} \sigma_0 \\
&= \sum_\alpha k_\alpha
\end{align*}$$
i.e. $\sum_\alpha k_\alpha \sigma_\alpha \in \text{im }\partial_1 \implies \ker \varepsilon \subseteq \text{im }\partial_1$.  $\therefore \ker \varepsilon = \text{im }\partial_1$

Now $H_0(X) = \ker \partial_0/\text{im }\partial_1 = C_0(X)/\ker \varepsilon \cong \text{im }\varepsilon \cong \mathbb{Z}$, where the second last $\cong$ is a consequence of the 1st isomorphism theorem. $\square$

>[!proposition] 
>$X$ a point. Then $$H_n(X)= \begin{cases}
\mathbb{Z} & n=0  \\
0 & n \geq 1
\end{cases}$$ 
##### Proof
For $n \geq 0$ there is a unique singular n-simplex $\sigma_n:\Delta^n \to X$. So $C_n(X) \cong \mathbb{Z}$ for all $n \geq 0$. 
Now 
$$\begin{align*}
\partial_n \sigma_n &= \sum_{i=0}^n (-1)^i\sigma_n|_{[v_0,...,\hat{v_i},...,v_n]} \\
&= \left(\sum_{i=0}^n (-1)^i\right)\sigma_{n-1} = \begin{cases}
0 & n = \text{odd or\: } 0  \\
\sigma_{n-1} & n = \text{even\:} \geq 2
\end{cases}
\end{align*}$$
So $$\ker \partial_n = \begin{cases}
\mathbb{Z}\sigma_n & n = \text{odd or\: } 0  \\
0 & n = \text{even\:} \geq 2
\end{cases}\quad,\quad \text{im }\partial_n = \begin{cases}
0 & n = \text{odd or\: } 0  \\
\mathbb{Z}\sigma_{n-1} & n = \text{even\:} \geq 2
\end{cases}$$
Then for $n$ *odd*:
$$H_n(X) = \ker\partial_n / \text{im }\partial_{n+1} = \mathbb{Z}\sigma_{n}/\mathbb{Z}\sigma_n \cong 0$$
Then for $n$ *even*:
$$H_n(X) = \ker\partial_n / \text{im }\partial_{n+1} = 0/0 \cong 0$$
Then for $n=0$:
$$H_n(X) \cong \mathbb{Z}$$ by proposition above. $\square$



# Reduced Homology

## Augmented Singular Chain Complex

>[!def] 
>For $X$ non-empty, the **augmented singular chain complex** is  $$\cdots\:\overset{\partial_{n+2}}{\longrightarrow} C_{n+1} \overset{\partial_{n+1}}{\longrightarrow}C_{n} \overset{\partial_{n}}{\longrightarrow}C_{n-1} \overset{\partial_{n-1}}{\longrightarrow}\cdots C_{1} \overset{\partial_{1}}{\longrightarrow}C_{0} \overset{\partial_{0}}{\longrightarrow} \mathbb{Z}{\longrightarrow}0,$$
>where for $n \geq 0$, $C_n(X)$ is the set of singular n-chains for $n \geq 1$, $\partial_n$ is the boundary map, and $\varepsilon:C_0(X) \to \mathbb{Z}$ is given by $\sum_\alpha k_\alpha \sigma_\alpha \mapsto \sum_\alpha k_\alpha$ and is surjective where $\text{im }\partial_1 \subseteq \ker \varepsilon$.
>

## Reduced Homology Group

>[!def] 
>The **reduced homology group** $\widetilde{H}_n(X)$ are the homology groups of the augmented singular chain complexes i.e. $$\widetilde{H}_n(X) = \begin{cases}
\ker \varepsilon / \text{im }\partial_1 & n=0  \\[2pt]
H_n(X) & n \geq 1
\end{cases}$$

- Note that $\varepsilon$ induces a surjective map $C_0(X)/\text{im }\partial_1=H_0(X) \to \mathbb{Z}$ with kernel equal to $\widetilde{H}_0(X)$. So $H_0(X)/\widetilde{H}_0(X) \cong \mathbb{Z}$ and $H_0(X) = \widetilde{H_0}(X) \oplus \mathbb{Z}$.
  Therefore for $X$ non-empty and path-connected, $\widetilde{H}_0(X) \cong 0$ by proposition 6 above.


# Homology Invariance

>[!lemma]
>For $n\geq 0$, any continuous map $f:X \to Y$ induces a homomorphism $f_\#:C_n(X) \to C_n(Y)$.
##### Proof
$\sigma:\Delta^n \to X$ a singular n-simplex. 

![[Singular Homology-1760153058636.png]]

Then $f \circ \sigma$ is continuous, so $f \circ \sigma$ is a singular n-simplex with image in $Y$. To define $f_\#$ on $C_n(X)$, extend this linearly: $f_\#(\sum_\alpha k_\alpha \sigma_\alpha)= \sum_\alpha k_\alpha(f \circ \sigma_\alpha)$  $\square$


## Chain map

>[!def]
>A **chain map** is a collection of homomorphisms $\varphi_n:C_n(X) \to C_n(Y)$ such that TFDC:
>
>![[Singular Homology-1760153372596.png|550]]

**Notation:** Write $\varphi$ for $\varphi_n$ and $\partial$ for $\partial_n^X,\partial_n^Y$. Also write $C_*(X),C_*(Y)$ for respective chain complexes $\varphi:C_*(X)\to C_*(Y)$

>[!lemma]
>If $f:X\to Y$ is continuous, then the induced $f_\#:C_*(X)\to C_*(Y)$ is a chain map.
##### Proof
For $n \geq 1$, let $\sigma:\Delta^n\to X$ be a singular n-simplex. We want to show that each square of the two parallel chains commute. i.e.
![[Singular Homology-1760153735944.png|200]]

We have 
$$\begin{align*}
(f_\# \circ \partial_n^X)(\sigma) &= 
\end{align*}$$