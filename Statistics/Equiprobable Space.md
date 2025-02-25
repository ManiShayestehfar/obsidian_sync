>[!info] Definition
>An **Equiprobable space** consists of a *finite* sample space $\Omega$ such that
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
