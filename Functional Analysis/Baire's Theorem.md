# Statement

>[!Theorem]
>Let $X$ be a compact metric space.
>Let $U_1,U_2,U_3,...$ are open dense subsets of $X$, then 
>$$U := \bigcap_{n=1}^\infty U_n \qquad\tag{countable intersection}$$
>is dense in $X$.
##### Proof
Let $Y \subseteq X$ (open). Required to prove that $Y \cap U \neq \varnothing$.
That is, $\exists x \in Y$ with $x \in U_n$ for all $n \geq 1$.

- By density of $U_1$ there is $x_1 \in Y \cap U_1$, and by openness of $Y$ and $U_1$ there is $0 < \epsilon_1 < 1$ with $\overline{B}(x_1,\epsilon_1) \subseteq Y \cap U_1$ (here $\overline{B}(x,r) = \{y \:|\: d(x,y) \leq r\}$) 

- Then there is $x_2 \in B(x_1,\epsilon_1) \cap U_2$ and since $B(x_1,\epsilon_1)$ and $U_2$ are open, there is $0 < \epsilon_2<\frac{1}{2}$ so that $$\overline{B}(x_2,\epsilon_2)\subseteq B(x_1,\epsilon_1)\cap U_2.$$
- Inductively, there is a sequence $0 < \epsilon_2 < \frac{1}{n}$ and $x_n \in X$ with $$\overline{B}(x_n,\epsilon_n) \subseteq B(x_{n-1}, \epsilon_{n-1})\cap U_n.$$
- Since $x_n \in B(x_m,\epsilon_m)$ for all $n>m$, the sequence $(x_n)_{n\geq1}$ is Cauchy. So $x_n \to x$ in $X$ (since $X$ is complete).

- For all $m$, $x \in \overline{B}(x_m,\epsilon_m)$. So $x \in \overline{B}(x_{m+1}, \epsilon_{m+1}) \subseteq B(x_m,\epsilon_m)$.
  Hence $x \in U_m$ and $x \in \overline{B}(x_1,\epsilon_1)\subseteq Y$ (so $x \in U \cap Y$).
$\square$

## Main Application

### Corollary

>[!Corollary]
>Let $X$ be a compact metric space.
>Suppose $C_1,C_2,...$ are closed and
>$$X = \bigcup_{n=1}^\infty C_n \tag{countable union}$$
>Then $\text{int}(C_n)\neq \varnothing$ for some $n$.
##### Proof
>[!Claim]
>If $\text{int}(C_n) = \varnothing$ for all $n \geq 1$, then $U_n = X \setminus C_n$ is open and dense.
###### Proof
- Let $Y$ be open. We need $Y \cap U_n \neq \varnothing$. 
- If $Y \cap U_n = \varnothing$, then $Y \subseteq C_n$ so $\text{int}(C_n) \neq \varnothing$. $\square$

So $\bigcap_{n=1}^\infty U_n$ is dense (by Baire). In particular it is non-empty, so
$$X = \bigcup_{n=1}^\infty C_n = \bigcup_{n=1}^\infty (X \setminus U_n) = X \setminus \left(\bigcap_{n=1}^\infty U_n\right)\neq X$$
a contradiction. $\square$


### Uncountability of $[0,1]$

>[!Corollary]
>$[0,1]$ is uncountable
##### Proof
$X = [0,1]$ is a complete metric space.
If $X$ is countable, then 
$$X = \bigcup_{x \in [0,1]} \{x\} \tag{countable union}$$
so $\text{int}(\{x\}) \neq \varnothing$ for some $x$, which is a contradiction $\square$

### Uncountability of Infinite-dim Hamel Basis

>[!Corollary]
>Every Hamel basis of an infinite dimensional Banach space is uncountable.
##### Proof
Suppose 
