#  Main Theorem

> [!Theorem] Bochner-Herglotz Theorem for Matrix Coefficients of Unitary Operators
> Let $H$ be a complex Hilbert space, let $U : H \to H$ be a unitary operator, and let $v \in H$. Then there exists a finite positive Borel measure $\mu_v$ on the unit circle $\mathbb T = \{z \in \mathbb C : |z| = 1\}$ such that
> $$
> \langle U^n v, v \rangle = \int_{\mathbb T} z^n \, d\mu_v(z)
> $$
> for every integer $n \in \mathbb Z$.

## Positive-definiteness of the coefficients

Define $a_n := \langle U^n v, v \rangle, \:\: n \in \mathbb Z.$  Since $U$ is unitary, $U^{-1} = U^*.$
Therefore, for any complex numbers $c_0, \ldots, c_m$,
$$
\sum_{j,k=0}^m c_j \overline{c_k} a_{j-k}
=
\sum_{j,k=0}^m c_j \overline{c_k} \langle U^{j-k}v, v \rangle.
$$

Moreover, $\langle U^{j-k}v, v \rangle = \langle U^jv, U^kv \rangle,$ because $U^* = U^{-1}$. Hence
$$
\sum_{j,k=0}^m c_j \overline{c_k} a_{j-k}
=
\sum_{j,k=0}^m c_j \overline{c_k} \langle U^jv, U^kv \rangle.
$$
By sesquilinearity of the inner product,
$$
\sum_{j,k=0}^m c_j \overline{c_k} a_{j-k}
=
\left\langle \sum_{j=0}^m c_j U^jv, \sum_{k=0}^m c_k U^kv \right\rangle.
$$

Thus
$$
\sum_{j,k=0}^m c_j \overline{c_k} a_{j-k}
=
\left\| \sum_{j=0}^m c_j U^jv \right\|^2
\geq 0.
$$

Hence $(a_n)_{n \in \mathbb Z}$ is positive definite.

## A Functional on Trigonometric Polynomials

Let $p(z) = \sum_{n=-m}^m b_n z^n$ be a trigonometric polynomial on $\mathbb T$. 
Define a linear functional $L$ on trigonometric polynomials by
$$
L(p) := \sum_{n=-m}^m b_n a_n.
$$
Equivalently, $L(z^n) = a_n = \langle U^n v, v \rangle.$
We will prove that $L$ is positive.

## The Fejer-Riesz Lemma

> [!Lemma] 
> Let $p(z) = \sum_{n=-m}^m a_n z^n$ be a trigonometric polynomial satisfying $p(z) \geq 0 \:\: (z \in \mathbb T).$
> Then there exists an ordinary polynomial
> $$
> Q(z) = \sum_{j=0}^m c_j z^j
> $$
> such that $p(z) = |Q(z)|^2 \:\: (z \in \mathbb T)$.
##### Proof
The case $p \equiv 0$ is trivial. Assume $p \not\equiv 0$.
Since $p$ is real-valued on $\mathbb T$, its coefficients satisfy $a_{-n} = \overline{a_n}.$

Define $P(z) := z^m p(z).$ Then $P$ is an ordinary polynomial.
 
 >[!Claim]
 >$$
 P(z) = z^{2m}\overline{P(1/\overline z)}.
 $$
###### Proof
 Indeed,
 $$
\begin{align*}
\overline{P(1/\overline z)}
&= \overline{\sum_{n=-m}^m a_n(1/\overline z)^{n+m}} \\
&= \sum_{n=-m}^m \overline{a_n} z^{-n-m}. \\
&= \sum_{n=-m}^m a_{-n} z^{-n-m} \tag{using $\overline{a_n} = a_{-n}$} \\
&= \sum_{n=-m}^m a_n z^{n-m} \tag{replacing $n$ by $-n$}\\
 &= z^{-2m}P(z).
\end{align*}
 $$
$\square$


Therefore, if $\alpha$ is a zero of $P$, then so is $\frac{1}{\overline \alpha},$ with the same multiplicity.

>[!Claim]
>Let $\zeta \in \mathbb T$ be a zero of $P$. Then the multiplicity of $\zeta$ is even.
###### Proof
Define $f(t) := p(e^{it}).$
Then $f(t) \geq 0$ for all $t$. Suppose $f$ vanished at $t_0$ to odd order. 
Then $f(t) = (t - t_0)^{2k+1}g(t)$, where $g(t_0) \neq 0$.

 Since $g$ is continuous and nonzero near $t_0$, it keeps a constant sign near $t_0$. But $(t - t_0)^{2k+1}$ changes sign across $t_0$, so $f$ changes sign near $t_0$, contradicting $f(t) \geq 0$. Therefore every zero of $f$ has even order.

If $e^{it_0} = \zeta$, then near $t_0$, $e^{it} - \zeta = i\zeta(t - t_0) + O((t - t_0)^2).$
Hence $e^{it} - \zeta$ vanishes to first order in $t - t_0$, so the order of vanishing of $f(t) = p(e^{it})$ at $t_0$ equals the multiplicity of $\zeta$ as a zero of $P$. Thus zeros of $P$ on $\mathbb T$ have even multiplicity.
$\square$


Now choose exactly one zero from each pair, $\alpha, \frac{1}{\overline \alpha}$ off the unit circle, and choose half of the multiplicity from each zero on the unit circle. 
Let the resulting zeros be $\alpha_1, \ldots, \alpha_m$.

Define $q(z) := \prod_{j=1}^m (z - \alpha_j)$, and define the reflected polynomial $q^*(z) := z^m\overline{q(1/\overline z)}$.
Then the zeros of $q^*$ are exactly: $\frac{1}{\overline{\alpha_1}}, \ldots, \frac{1}{\overline{\alpha_m}}.$

Therefore $q(z)q^*(z)$ and $P(z)$ have the same zeros with the same multiplicities. Hence there exists a constant $c \neq 0$ such that $P(z) = c q(z)q^*(z).$

Now let $|z| = 1$. Then $1/\overline z = z$, so $q^*(z) = z^m\overline{q(z)}$.
Therefore $P(z) = c q(z)z^m\overline{q(z)} = c z^m |q(z)|^2$.

Since $P(z) = z^m p(z)$, we get $p(z) = c|q(z)|^2$ for $z \in \mathbb{T}$.

Because $p(z) \geq 0$ on $\mathbb T$ and $p \not\equiv 0$, the constant $c$ is positive real. 
Define $Q(z) := \sqrt c\, q(z)$.
Then $p(z) = |Q(z)|^2 \qquad (z \in \mathbb T).$
$\square$

## Positivity of the Functional

Let $p \geq 0$ be a trigonometric polynomial. By the Fejer-Riesz lemma, $p(z) = |Q(z)|^2$
for some polynomial $Q(z) = \sum_{j=0}^m c_j z^j.$

On $\mathbb T$,
$$
|Q(z)|^2
=
Q(z)\overline{Q(z)}
=
\left(\sum_{j=0}^m c_j z^j\right)
\left(\sum_{k=0}^m \overline{c_k} z^{-k}\right).
$$
Therefore $|Q(z)|^2 = \sum_{j,k=0}^m c_j \overline{c_k} z^{j-k}.$
Applying $L$ gives
$$
L(p)
=
\sum_{j,k=0}^m c_j \overline{c_k} a_{j-k}.
$$
By the positive-definiteness proved before,
$$
L(p)
=
\left\| \sum_{j=0}^m c_j U^jv \right\|^2
\geq 0.
$$
Thus $L$ is positive on nonnegative trigonometric polynomials.

## Boundedness and extension to $C(\mathbb T)$

If $p$ is real-valued, then $-\|p\|_\infty \leq p \leq \|p\|_\infty.$

Since $L$ is positive, applying it to $\|p\|_\infty \pm p$ gives $|L(p)| \leq \|p\|_\infty L(1).$
But $L(1) = a_0 = \langle v, v \rangle = \|v\|^2.$ Therefore $|L(p)| \leq \|v\|^2\|p\|_\infty$ for real-valued trigonometric polynomials $p$.

For a general complex-valued trigonometric polynomial $p$, applying the same bound to its real and imaginary parts gives boundedness of $L$ with respect to the sup norm. 
In particular, $L$ extends uniquely to a bounded linear functional on the uniform closure of the trigonometric polynomials.

By the [[Stone-Weierstrass|Stone-Weierstrass Theorem]], trigonometric polynomials are uniformly dense in $C(\mathbb T)$. Hence $L$ extends uniquely to a bounded positive linear functional on $C(\mathbb T)$.

## Riesz representation theorem

By the [[Riesz Representation|Riesz Representation Theorem]], there exists a unique finite positive Borel measure $\mu_v$ on $\mathbb T$ such that
$$
L(f) = \int_{\mathbb T} f(z)\, d\mu_v(z)
$$
for every $f \in C(\mathbb T)$.

Taking $f(z) = z^n,$ we obtain
$$
\langle U^n v, v \rangle
=
L(z^n)
=
\int_{\mathbb T} z^n\, d\mu_v(z).
$$
This proves the theorem. $\square$

# Remarks

> [!Remark]
> The convention for the inner product affects only whether the final formula contains $z^n$ or $z^{-n}$. The above convention is consistent with the displayed computation
>
> $$
> \langle U^{j-k}v, v \rangle = \langle U^jv, U^kv \rangle.
> $$
>
> If the opposite inner-product convention is used, one should adjust the Fourier convention accordingly.
