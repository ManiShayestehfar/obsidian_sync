>[!info] Definition
>The **Cumulative Distribution Function (CDF)** of an RV $X$ is defined as:
>$$F_X(x) := P(X\leq x)$$

>[!tip] Claim
>If $F$ is a CDF if an RV $X$ with $P(X \in \mathbb{R}) = 1$, then:
>i. $F$ is non-decreasing
>ii. $F$ is right-continuous: $\lim_{x \to x_0^+} F(x) = F(x_0)$
>iii. $\lim_{x \to \infty} F(x) = 1$ and $\lim_{x \to -\infty} F(x) = 0$
>   
>   Conversely, if $F$ satisfies 1-3 then $F$ is the CDF of some RV $X$ with $P(X \in \mathbb{R})=1$.
#### Proof
##### (i)
$a\leq b \implies \{X \leq a\} \subset \{X \leq b\}$. So
$$F(a) = P(X\leq a) \leq P(X\leq b) = F(b) \quad \quad \square$$

##### (iii)
>[!tip] Lemma (Continuity if the probability measure)
>1. If the events $A_n$ are increasing, i.e. if $A_n \subset A_{n+1}$, then $P\left(\bigcup_n A_n \right) = \lim_{n \to \infty} P(A_n)$
>2. If $A_n$ are decreasing, i.e. if $A_{n+1}\subset A_n$, then $P\left(\bigcap_n A_n\right) = \lim_{n \to \infty} P(A_n)$

###### Proof

![[Pasted image 20250413143038.png|650]]

$B_n$ are disjoint events and $\bigcup_{k=1}^n B_k = A_n$. In particular $\bigcup_1^\infty A_n = \underbrace{\cup_1^\infty B_n}_{\text{disjoint}}$.
$$\begin{align*}
P\left(\sum_{1}^\infty A_n\right) &= P\left(\sum_{1}^\infty B_n\right) \\[5pt]
&= \sum_1^\infty P(B_n) \\[5pt]
&= \lim_{N\to \infty} \sum_{1}^\infty P(B_n) \\[5pt]
&= \lim_{N\to \infty} P\left(\bigcup_1^N B_n\right) \\[5pt]
&= \lim_{N\to \infty} P(A_n)  \quad\quad \square
\end{align*}$$
The proof to 2. is similar but instead if $A_n$ is decreasing, then $A_n^c$ is increasing.

**Back to proving (iii):**

Let $A_n = \{X \leq n\}$. So $A_n$ is increasing, and $P(A_n) = F(n)$ so by the lemma above
$$P\left(\bigcup_1^\infty A_n\right) = \lim_{n \to \infty} P(A_n) =  \lim_{n\to\infty} F(n).$$
Now, $\cup A_n = \cup_{n=1}^\infty \{x \leq n\} = \{X < \infty \}$.  
$$1 \geq \lim_{n} F(n) = P(\cup A_n) = P(X < \infty)  \geq P(X \in \mathbb{R}) = 1$$
$\implies \lim_{n\to \infty} F(n) = 1$.

But this is for $n$ integer indices. We need to confirm this for real numbers $x$. Because $F$ is monotone $\lim_{x\to \infty} F(x)$ exists, and since $\lim_{n\to \infty} F(n) = 1$, it follows that $\lim_{x \to \infty} F(x) = 1$.

For the second half of (iii), let $A_n = \{X \leq -n\}$. $A_n$ is decreasing so 
$$P(\cap A_n) = \lim_n P(A_n) = \lim_n F(-n)$$
but $\cap_1^\infty A_n = \cap_1^\infty \{X \leq -n\} = \{X = -\infty\}$.
$$ 0 \leq \lim_{n\to \infty} F(-n) = P(\cap_1^\infty A_n) = P(X= -\infty) \leq P(X \not\in \mathbb{R}) = 0.$$
Again with monotonicity, we can show that $\lim_{x \to -\infty} F(x) = 0$.        $\square$ 

##### (ii) 
Exercise.


