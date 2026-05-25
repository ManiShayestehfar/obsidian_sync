# Hahn–Banach and separation in locally convex spaces

For the Krein–Milman proof below, the exact consequence of Hahn–Banach we need is the following.

> [!Theorem] Separation used in Krein–Milman
> Let $X$ be a real Hausdorff locally convex topological vector space. Let $K \subseteq X$ be compact and convex, let $C \subseteq K$ be closed and convex, and let $x_0 \in K \setminus C$. Then there exists $\varphi \in X^*$ such that
>
> $$\varphi(x_0) > \sup_{c \in C} \varphi(c).$$

- This is the locally convex analogue of the familiar normed-space fact that a point outside a closed convex set can be separated by a continuous linear functional. In a normed space, the proof is often phrased using distance to the convex set. In a general locally convex space, there may be no norm and no distance, so convex neighbourhoods and Minkowski functionals replace balls and norms.

# Krein–Milman theorem

> [!Theorem] Krein–Milman
> Let $X$ be a real Hausdorff locally convex topological vector space, and let $K \subseteq X$ be nonempty, compact, and convex. Then
>
> $$K = \overline{\operatorname{co}}(\operatorname{Ext}(K)).$$
>
> In particular, $K$ has at least one extreme point.

The closure is taken in the given topology on $X$.

## Supporting faces

> [!Lemma] Exposed faces
> Let $K \subseteq X$ be nonempty compact and convex, and let $\varphi \in X^*$ be a continuous linear functional. Let $M = \max_{x \in K}\varphi(x)$. Then $F = \{x \in K : \varphi(x)=M\}$ is a nonempty compact face of $K$.
##### Proof

Since $K$ is compact and $\varphi$ is continuous, $\varphi$ attains its maximum on $K$. Hence $F$ is nonempty. It is closed in $K$, hence compact.

To show that $F$ is a face, suppose $tx + (1-t)y \in F$, $x,y \in K$, and $0 < t < 1$. Then

$$M = \varphi(tx+(1-t)y)=t\varphi(x)+(1-t)\varphi(y).$$

But $\varphi(x) \leq M$ and $\varphi(y) \leq M$. The only way their strict convex combination equals $M$ is if $\varphi(x)=\varphi(y)=M$. Thus $x,y \in F$.

## Existence of extreme points

> [!Lemma]
> Every nonempty compact convex subset $K$ of a real Hausdorff locally convex topological vector space has an extreme point.

##### Proof

Let $\mathcal{F}$ be the family of all nonempty compact faces of $K$, ordered by reverse inclusion:

$$F_1 \preceq F_2 \Longleftrightarrow F_1 \supseteq F_2.$$

Every chain in this order corresponds to a nested family of nonempty compact subsets of $K$. By compactness, the intersection of such a chain is nonempty. It is also a compact face of $K$. Therefore, by Zorn’s lemma, there exists a minimal nonempty compact face $F$ of $K$.

We claim that $F$ is a singleton. Suppose not. Choose distinct $x,y \in F$. Since $X$ is Hausdorff locally convex, continuous linear functionals separate points. Hence there exists $\varphi \in X^*$ such that $\varphi(x) \neq \varphi(y)$.

Let $M = \max_{z \in F}\varphi(z)$ and set $F_0 = \{z \in F : \varphi(z)=M\}$. By the previous lemma, $F_0$ is a nonempty compact face of $F$, and hence also a face of $K$. Since $\varphi$ is not constant on $F$, $F_0$ is a proper subset of $F$. This contradicts the minimality of $F$.

Therefore $F = \{e\}$ for some $e \in K$. Since singleton faces are exactly extreme points, $e \in \operatorname{Ext}(K)$.

## Proof of Krein–Milman

Let $C = \overline{\operatorname{co}}(\operatorname{Ext}(K))$. Then $C \subseteq K$ because $K$ is closed and convex.

Assume, for contradiction, that $C \neq K$. Choose $x_0 \in K \setminus C$. Since $C$ is closed and convex and $X$ is locally convex, the Hahn–Banach separation theorem gives a continuous linear functional $\varphi \in X^*$ such that

$$\varphi(x_0) > \sup_{y \in C}\varphi(y).$$

Let $M = \max_{x \in K}\varphi(x)$ and define the exposed face $F = \{x \in K : \varphi(x)=M\}$.

This is a nonempty compact face of $K$. By the previous lemma, $F$ has an extreme point $e$ of $F$.

We now observe that $e$ is also extreme in $K$. Indeed, if $e = tx + (1-t)y$, $x,y \in K$, and $0 < t < 1$, then $e \in F$ and $F$ is a face, so $x,y \in F$. Since $e$ is extreme in $F$, we get $x = y = e$. Thus $e \in \operatorname{Ext}(K)$.

Hence $e \in C$. But $\varphi(e)=M$. Since $x_0 \in K$, we have

$$M \geq \varphi(x_0) > \sup_{y \in C}\varphi(y),$$

which is impossible because $e \in C$ and $\varphi(e)=M$. Therefore $K=C$.

# Compactness of the space of probability measures

Let $X$ be a compact metric space. Denote by $C(X)$ the Banach space of continuous real-valued functions on $X$, equipped with the supremum norm $\|f\|_\infty = \sup_{x \in X}|f(x)|$.

We denote by $P(X)$ the space of Borel probability measures on $X$.

## Separability of $C(X)$

> [!Proposition]
> Let $X$ be a compact metric space. Then $C(X)$, with the supremum norm, is separable.
##### Proof

Since $X$ is compact, it is totally bounded. Hence for every $n \geq 1$ we may choose a finite $1/n$-net $D_n = \{x_{n,1},\ldots,x_{n,N_n}\} \subseteq X$.

Consider the following countable family of continuous functions. For each $n$, each rational number $L > 0$, and each rational vector $q = (q_1,\ldots,q_{N_n}) \in \mathbb{Q}^{N_n}$, define

$$g_{n,L,q}(x)=\min_{1 \leq j \leq N_n}\left(q_j + Ld(x,x_{n,j})\right).$$

Each $g_{n,L,q}$ is continuous, being the minimum of finitely many continuous functions. Since there are only countably many choices of $n$, $L$, and $q$, this gives a countable family.

We claim this family is dense in $C(X)$.

Let $f \in C(X)$ and let $\varepsilon > 0$. Since $X$ is compact, $f$ is uniformly continuous. Choose $\delta > 0$ such that $d(x,y)<\delta \Rightarrow |f(x)-f(y)|<\varepsilon/4$.

Let $M = \|f\|_\infty$. Choose a rational $L > 0$ so large that $L\delta > 2M+1$. Then choose $n$ so large that $1/n < \delta$ and $L/n < \varepsilon/4$.

For each $j=1,\ldots,N_n$, choose $q_j \in \mathbb{Q}$ such that $|q_j - f(x_{n,j})| < \varepsilon/4$.

We show that $\|g_{n,L,q}-f\|_\infty < \varepsilon$.

Fix $x \in X$. Since $D_n$ is a $1/n$-net, there exists $j$ such that $d(x,x_{n,j}) < 1/n$. Therefore $g_{n,L,q}(x) \leq q_j + Ld(x,x_{n,j})$. Hence

$$g_{n,L,q}(x) \leq f(x_{n,j}) + \frac{\varepsilon}{4} + \frac{L}{n}.$$

Since $d(x,x_{n,j}) < 1/n < \delta$, $|f(x_{n,j})-f(x)| < \varepsilon/4$. Thus $g_{n,L,q}(x) < f(x) + 3\varepsilon/4$.

It remains to prove the lower bound. For every $j$, we claim $q_j + Ld(x,x_{n,j}) > f(x)-\varepsilon$.

Indeed, if $d(x,x_{n,j}) < \delta$, then $f(x_{n,j}) > f(x)-\varepsilon/4$, and so

$$q_j + Ld(x,x_{n,j}) > f(x_{n,j}) - \frac{\varepsilon}{4} > f(x) - \frac{\varepsilon}{2}.$$

If instead $d(x,x_{n,j}) \geq \delta$, then

$$q_j + Ld(x,x_{n,j}) \geq -M - \frac{\varepsilon}{4} + L\delta.$$

By our choice of $L$, this is larger than $M$, provided $L\delta$ was chosen large enough. Since $f(x) \leq M$, this gives in particular $q_j + Ld(x,x_{n,j}) > f(x)-\varepsilon$.

Taking the minimum over $j$, we obtain $g_{n,L,q}(x) > f(x)-\varepsilon$. Together with the upper bound, $|g_{n,L,q}(x)-f(x)| < \varepsilon$.

Since $x \in X$ was arbitrary, $\|g_{n,L,q}-f\|_\infty < \varepsilon$. Thus $C(X)$ has a countable dense subset, and hence is separable.

## Weak-* topology on probability measures

By the Riesz representation theorem, every probability measure $\mu \in P(X)$ defines a continuous linear functional on $C(X)$ by $f \mapsto \int_X f\,d\mu$. Thus $P(X) \subseteq C(X)^*$.

> [!Definition]
> The weak-* topology on $P(X)$ is the topology generated by the maps $\mu \mapsto \int_X f\,d\mu$, $f \in C(X)$.
>
> Equivalently, a sequence $(\mu_n)$ converges to $\mu$ if and only if
>
> $$\int_X f\,d\mu_n \longrightarrow \int_X f\,d\mu$$
>
> for every $f \in C(X)$.

## Metrizability of $P(X)$

> [!Proposition]
> If $X$ is compact metric, then the weak-* topology on $P(X)$ is metrizable.
##### Proof
Since $C(X)$ is separable, choose a countable dense set $\{f_n\}_{n \geq 1}$ in the unit ball of $C(X)$. Define

$$d(\mu,\nu)=\sum_{n=1}^\infty 2^{-n}\left|\int_X f_n\,d\mu - \int_X f_n\,d\nu\right|.$$

Since $\left|\int f_n\,d\mu - \int f_n\,d\nu\right| \leq 2$, the series converges absolutely.

It is straightforward to verify that $d$ is a metric.

We claim that this metric induces the weak-* topology.

Suppose first that $d(\mu_k,\mu) \to 0$. Then for every $n$, $\int f_n\,d\mu_k \to \int f_n\,d\mu$.

Now let $f \in C(X)$. Since $\{f_n\}$ is dense in the unit ball, choose $f_{n_j} \to f$ uniformly. Then

$$\begin{aligned}
\left|\int f\,d\mu_k - \int f\,d\mu\right|
&\leq \left|\int (f-f_{n_j})\,d\mu_k\right| \\
&\quad + \left|\int f_{n_j}\,d\mu_k - \int f_{n_j}\,d\mu\right| \\
&\quad + \left|\int (f_{n_j}-f)\,d\mu\right|.
\end{aligned}$$

The first and third terms are bounded by $\|f-f_{n_j}\|_\infty$, while the middle term tends to zero for fixed $j$. Hence $\int f\,d\mu_k \to \int f\,d\mu$.

Thus $\mu_k \to \mu$ weak-*.

Conversely, weak-* convergence clearly implies convergence in $d$. Therefore $d$ generates the weak-* topology.

## Compactness of $P(X)$

> [!Theorem]
> If $X$ is compact metric, then $P(X)$ is compact in the weak-* topology.
##### Proof

Since $P(X)$ is metrizable, it suffices to prove sequential compactness.

Let $(\mu_k)_{k \geq 1} \subseteq P(X)$. Choose a countable dense family $\{f_n\}_{n \geq 1}$ in the unit ball of $C(X)$.

For each fixed $n$, the sequence $\left(\int_X f_n\,d\mu_k\right)_{k \geq 1}$ is bounded, since $\left|\int_X f_n\,d\mu_k\right| \leq \|f_n\|_\infty \leq 1$.

By Bolzano–Weierstrass, we may choose a subsequence along which $\int f_1\,d\mu_k$ converges.

Passing inductively to subsequences and diagonalising, we obtain a subsequence $(\mu_{k_j})$ such that for every $n$, $\int_X f_n\,d\mu_{k_j}$ converges.

We now show that for every $f \in C(X)$, $\int_X f\,d\mu_{k_j}$ converges. Choose $f_{n_m} \to f$ uniformly. Then

$$\left|\int f\,d\mu_{k_j} - \int f\,d\mu_{k_\ell}\right| \leq 2\|f-f_{n_m}\|_\infty + \left|\int f_{n_m}\,d\mu_{k_j} - \int f_{n_m}\,d\mu_{k_\ell}\right|.$$

For fixed $m$, the second term tends to zero as $j,\ell \to \infty$, while the first term can be made arbitrarily small by choosing $m$ large. Hence $\left(\int f\,d\mu_{k_j}\right)$ is Cauchy, therefore convergent.

Define

$$L(f)=\lim_{j \to \infty}\int_X f\,d\mu_{k_j}.$$

Then $L:C(X) \to \mathbb{R}$ is linear, positive, and satisfies $L(1)=1$.

By the Riesz representation theorem, there exists a unique probability measure $\mu \in P(X)$ such that $L(f)=\int_X f\,d\mu$ for all $f \in C(X)$.

Therefore $\mu_{k_j} \to \mu$ weak-*. Thus every sequence in $P(X)$ has a convergent subsequence, so $P(X)$ is sequentially compact. Since it is metrizable, it is compact.

## Invariant probability measures

Let $T:X \to X$ be continuous.

Define

$$P_T(X)=\{\mu \in P(X):T_*\mu=\mu\}.$$

Equivalently,

$$\int_X f \circ T\,d\mu = \int_X f\,d\mu$$

for every $f \in C(X)$.

> [!Proposition]
> The set $P_T(X)$ is compact and convex.
##### Proof
Convexity is immediate.
To prove compactness, it suffices to show that $P_T(X)$ is closed in $P(X)$.
Suppose $\mu_n \to \mu$ weak-*, and each $\mu_n$ is $T$-invariant. Then for every $f \in C(X)$,
$$\int_X f \circ T\,d\mu_n = \int_X f\,d\mu_n.$$
Passing to the limit gives

$$\int_X f \circ T\,d\mu = \int_X f\,d\mu.$$
Hence $\mu$ is $T$-invariant.
Therefore $P_T(X)$ is closed in compact $P(X)$, hence compact.

# Approximation of probability measures by finitely supported measures

We prove that every probability measure on $X$ can be approximated in the weak-* topology by finitely supported probability measures.

> [!Theorem]
> Let $X$ be a compact metric space. Then
>
> $$P(X)=\overline{\operatorname{co}\{\delta_x : x \in X\}}^{w^*}.$$
>
> In other words, for every $\mu \in P(X)$, every $f_1,\ldots,f_n \in C(X)$, and every $\varepsilon > 0$, there exist points $x_1,\ldots,x_m \in X$ and coefficients $a_1,\ldots,a_m \geq 0$, with $\sum_{j=1}^m a_j = 1$, such that
>
> $$\left|\int_X f_i\,d\mu - \sum_{j=1}^m a_j f_i(x_j)\right| < \varepsilon$$
>
> for every $i=1,\ldots,n$.
##### Proof

We regard $P(X)$ as a subset of the dual space $C(X)^*$. By the Riesz representation theorem, $P(X)$ is precisely the set of positive linear functionals $L \in C(X)^*$ satisfying $L(1)=1$.

The set $P(X)$ is convex. It is also weak-* compact. Indeed, $P(X) \subseteq \{L \in C(X)^*: \|L\| \leq 1\}$, and the closed unit ball of $C(X)^*$ is weak-* compact by Banach–Alaoglu. Moreover, positivity and the condition $L(1)=1$ are weak-* closed conditions, so $P(X)$ is weak-* closed inside the weak-* compact unit ball.

We now identify the extreme points of $P(X)$. We claim that

$$\operatorname{Ext}(P(X))=\{\delta_x : x \in X\}.$$

First, each Dirac measure $\delta_x$ is extreme. Indeed, suppose $\delta_x = t\mu_1+(1-t)\mu_2$ with $0<t<1$ and $\mu_1,\mu_2 \in P(X)$. If $U \subseteq X$ is open and $x \notin U$, then

$$0=\delta_x(U)=t\mu_1(U)+(1-t)\mu_2(U).$$

Since both terms are nonnegative, we get $\mu_1(U)=\mu_2(U)=0$. Thus both $\mu_1$ and $\mu_2$ give mass zero to every open set not containing $x$. Hence both measures are concentrated at $x$, and therefore $\mu_1=\mu_2=\delta_x$. So $\delta_x$ is extreme.

Conversely, suppose $\mu \in P(X)$ is not a Dirac measure. Then there exists a Borel set $A \subseteq X$ such that $0 < \mu(A) < 1$.

Define probability measures

$$\mu_1(B)=\frac{\mu(B \cap A)}{\mu(A)}, \qquad \mu_2(B)=\frac{\mu(B \cap A^c)}{1-\mu(A)}.$$

Then $\mu_1,\mu_2 \in P(X)$, and $\mu = \mu(A)\mu_1 + (1-\mu(A))\mu_2$. Moreover, $\mu_1(A)=1$ and $\mu_2(A)=0$, so $\mu_1 \neq \mu_2$. Hence $\mu$ is not extreme.

Therefore the extreme points of $P(X)$ are exactly the Dirac measures.

Now apply the Krein–Milman theorem to the compact convex set $P(X)$. We obtain

$$P(X)=\overline{\operatorname{co}(\operatorname{Ext}(P(X)))}^{w^*}.$$

Since $\operatorname{Ext}(P(X))=\{\delta_x:x \in X\}$, it follows that

$$P(X)=\overline{\operatorname{co}\{\delta_x:x \in X\}}^{w^*}.$$

Thus every Borel probability measure on $X$ is a weak-* limit of finite convex combinations of Dirac measures.

# Ergodic measures and the Krein–Milman theorem

Let $X$ be a compact metric space and let $T:X \to X$ be a homeomorphism.

Recall that $P(X)$ denotes the space of Borel probability measures on $X$, equipped with the weak-* topology.

We define $P_T(X)=\{\mu \in P(X):T_*\mu=\mu\}$, the set of $T$-invariant probability measures.

Equivalently, $\mu \in P_T(X)$ if and only if

$$\int_X f \circ T\,d\mu = \int_X f\,d\mu$$

for every $f \in C(X)$.

### Compactness and convexity

> [!Proposition]
> The set $P_T(X)$ is compact and convex in the weak-* topology.

##### Proof
Convexity is immediate.
To prove compactness, it suffices to show that $P_T(X)$ is closed inside the compact space $P(X)$.
Suppose $\mu_n \to \mu$ weak-*, and each $\mu_n$ is $T$-invariant. Then for every $f \in C(X)$,
$$\int_X f \circ T\,d\mu_n = \int_X f\,d\mu_n.$$

Passing to the limit gives

$$\int_X f \circ T\,d\mu = \int_X f\,d\mu.$$

Hence $\mu$ is $T$-invariant. Therefore $P_T(X)$ is closed in compact $P(X)$, and is therefore compact.

## Ergodic measures

> [!Definition]
> A measure $\mu \in P_T(X)$ is called ergodic if whenever $T^{-1}A=A$ for a Borel set $A \subseteq X$, then $\mu(A) \in \{0,1\}$.
>
> We denote the set of ergodic measures by $E_T(X)$.

## Extreme points of $P_T(X)$

> [!Theorem]
> The extreme points of $P_T(X)$ are precisely the ergodic measures:
>
> $$\operatorname{Ext}(P_T(X))=E_T(X).$$
##### Proof
We first show that every non-ergodic measure is not extreme.
Suppose $\mu \in P_T(X)$ is not ergodic. Then there exists a Borel set $A \subseteq X$ such that $T^{-1}A=A$ and $0 < \mu(A) < 1$.

Define probability measures

$$\mu_1(B)=\frac{\mu(B \cap A)}{\mu(A)}, \qquad \mu_2(B)=\frac{\mu(B \cap A^c)}{1-\mu(A)}.$$
Since $A$ is $T$-invariant, both $\mu_1$ and $\mu_2$ are $T$-invariant. Indeed,

$$\mu_1(T^{-1}B)=\frac{\mu(T^{-1}B \cap A)}{\mu(A)}=\frac{\mu(T^{-1}(B \cap A))}{\mu(A)}=\frac{\mu(B \cap A)}{\mu(A)}=\mu_1(B),$$

and similarly for $\mu_2$.

Moreover, $\mu = \mu(A)\mu_1 + (1-\mu(A))\mu_2$. Since $\mu_1(A)=1$ and $\mu_2(A)=0$, we have $\mu_1 \neq \mu_2$. Therefore $\mu$ is not an extreme point of $P_T(X)$.

We now prove the converse.

Suppose $\mu \in P_T(X)$ is ergodic, and suppose $\mu = t\mu_1+(1-t)\mu_2$ with $0 < t < 1$ and $\mu_1,\mu_2 \in P_T(X)$.

Since $\mu_i \ll \mu$, the Radon–Nikodym theorem gives functions $f_i \in L^1(\mu)$ such that $d\mu_i = f_i\,d\mu$.

We claim that $f_i \circ T = f_i$ $\mu$-a.e. Indeed, for every $g \in C(X)$,

$$\int_X g \circ T\, f_i\,d\mu = \int_X g \circ T\,d\mu_i = \int_X g\,d\mu_i = \int_X gf_i\,d\mu.$$

Since $\mu$ is $T$-invariant,
$$\int_X g \circ T\, f_i\,d\mu = \int_X g(f_i \circ T^{-1})\,d\mu.$$
Hence
$$\int_X g(f_i - f_i \circ T^{-1})\,d\mu = 0$$

for every $g \in C(X)$, and therefore $f_i = f_i \circ T^{-1}$ $\mu$-a.e. Thus $f_i$ is $T$-invariant.

Since $\mu$ is ergodic, every invariant $L^1$-function is constant almost everywhere. Therefore $f_i = c_i$ $\mu$-a.e. for constants $c_i$.

Since $\mu_i$ is a probability measure,

$$1 = \mu_i(X)=\int_X f_i\,d\mu=c_i.$$

Hence $f_i=1$ $\mu$-a.e. and therefore $\mu_i=\mu$. Thus $\mu$ is extreme.

We conclude that $\operatorname{Ext}(P_T(X))=E_T(X)$.

## Application of Krein–Milman

> [!Theorem]
> Let $X$ be compact metric and let $T:X \to X$ be a homeomorphism. Then
>
> $$P_T(X)=\overline{\operatorname{co}(E_T(X))}$$
>
> in the weak-* topology.
##### Proof
The set $P_T(X)$ is compact and convex, and its extreme points are exactly the ergodic measures. Therefore the Krein–Milman theorem gives

$$P_T(X)=\overline{\operatorname{co}(\operatorname{Ext}(P_T(X)))}.$$
Since $\operatorname{Ext}(P_T(X))=E_T(X)$, we obtain

$$P_T(X)=\overline{\operatorname{co}(E_T(X))}.$$

> [!Remark]
> The theorem shows that every invariant probability measure can be approximated in the weak-* topology by finite convex combinations of ergodic measures.
>
> To obtain an actual integral decomposition
>
> $$\mu = \int_{E_T(X)} \nu\,d\eta(\nu),$$
>
> one needs Choquet’s theorem.
