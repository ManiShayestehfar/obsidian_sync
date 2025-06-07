>[!info] Definition
>An **Equiprobable space** consists of a *finite* [[Basic Definitions|sample space]] $\Omega$ such that
>$$\forall \omega \in \Omega,\quad P_e(\{\omega\}) = c > 0$$  
>where $c = 1 / |\Omega|$.

- Here let $\mathcal{F}_{e}= 2^\Omega$ 
- $\{\omega\}\in \mathcal{F}_e$ is the event which includes only the sample point $\omega$
- Simplify $P(\omega) := P(\{\omega\})$

#### Why is $\Omega$ finite?
Suppose there exists $\{\omega_n\}_{n=1}^{\infty}\subset \Omega$  (disjoint). Then
$$P_e(\bigsqcup_{n}\{\omega_{n}\})= \sum_{n}P_e(\{\omega_{n}\})= \sum_{n}c = \infty.$$
But this is in contradiction to $P$ being real-valued.


> [!tip] Claim 1
> $\forall A \in \mathcal{F}, P(A) \in [0,1]$ 
##### Proof


> [!tip] Claim 2
> $\forall A,B \in \mathcal{F}$ and $A \subset B$, $P(A) \leq P(B)$. 
> 
##### Proof



> [!tip] Claim 3
>$\forall A \in \mathcal{F}_{e},\quad P_{e}(A) = \frac{|A|}{|\Omega|}$  
> 
##### Proof
Let $A = \bigsqcup_{\omega \in A} \{\omega\} \implies P_{e(A)}= P(\bigsqcup_{\omega \in A} \{\omega\}) = \sum_{\omega \in A}P_e(\{\omega\})$ .
For $A = \Omega \implies 1 = P_{e(\Omega)}= |\Omega|\cdot c$, so
$$c = \frac{1}{|\Omega|}$$
and 
$$P_e(A)=\frac{|A|}{|\Omega|}.\quad \square$$

- Notice how this only works when $|\Omega| < \infty$.

#### Examples
- A fair die rolled and its outcome noted. For $A \subset \{1,...,6\},$
$$P(A) = \frac{|A|}{6}$$

#### Birthday Problem

>A group of $n$ people meet at a party. What is the probability that at least two of the share their birthday?

- Each individual birthday in $\{1,2,...,365\}$
- Each combination of $n$ days is equally likely. So sample space is
$$\Omega := \{(i_1,i_2,...,i_n):i_{k}\in\{1,...,365\},\quad k =1,...,n\}$$
$\implies |\Omega| = 365^n$. So $P(\omega) = 1/365^{n}$

Let $A = \{(i_1,i_2,...,i_{n})\in \Omega:\exists j\neq k \:\:\text{s.t.}\:\: i_j=i_k\}$. We need $P(A)$.

Start from the negation. $A^{c}= \{(i_1,i_2,...,i_{n})\in \Omega:\forall j\neq k \:\:\text{s.t.}\:\: i_{j} \neq i_k\}$.
$$|A^{c}|= 365\times 364\times ... \times (365 - (n-1)) = \prod_{i=1}^{n}(365 - (i-1))$$
$$\begin{align*}\implies P(A^{c}) &=  \frac{\prod_{i=1}^{n}(365 - (i-1))}{\prod_{i=1}^{n}365} \\[6pt]
&= \prod_{i=1}^{n}\left(1-\frac{i-1}{365}\right)
 \end{align*}$$
For $n=23, P(A^{c})\approx 0.5$. $\implies P(A) = 0.5\quad\square$.

#### A slightly different problem

> What is the probability that at least one of $n$ guests shares the host's birthday? i.e. what is the number of guests $n$ such that $P(B) = 0.5$?

$B = \{(i_1,...,i_{n})\in\Omega : \exists j\:\:\text{s.t.}\:\: i_{j}=x\}$ where $x$ is the host's birthday.

$B^{c}= \{(i_1,...,i_{n})\in\Omega : \forall j\:\:\text{s.t.}\:\: i_{j}\neq x\}$.
$|B^{c}| = 364 \times 364 \times ... \times 364 = 364^n$, so $P(B^{c})= \frac{364^{n}}{365^{n}} = (1 - \frac{1}{365})^{n}\approx e^\frac{-n}{365}$  

For $n =253, P(B^c) \approx 0.5 \implies P(B) = 0.5 \quad\square$
