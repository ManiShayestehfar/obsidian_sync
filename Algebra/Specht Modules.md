# Symmetric Groups Intro
## Definition

$$S_n = \{g:[n] \to [n] \: :\: \text{bijective}\}$$
- Multiplication is given by composition of maps.
- For distinct $a_1,...,a_k \in [n]$ we have the cycle 
$$(a_1\,a_2\,\cdots\,a_k)(i)=  
\begin{cases}  
a_{m+1}, & \text{if } i=a_m \text{ for some } m=1,\ldots,k,\\[4pt]  
i, & \text{if } i\notin\{a_1,\ldots,a_k\},  
\end{cases}$$
and $a_{k+1}=a_1$.

- Each $\omega \in S_n$ is associated to some **cycle type** $CT(\omega)=(\lambda_1,..., \lambda_k)$ where $\lambda_1 \geq \lambda_2 \geq \cdots \geq \lambda_k \geq 0$, and $\sum_{i=1}^k \lambda_i=n$.

## Conjugating Elements

>[!Lemma]
>Let $a_1,...,a_k \in [n]$ be distinct and $w \in S$. Then 
>$$w(a_1\cdots a_k)w^{-1} = (w(a_1)\cdots w(a_k))$$
##### Proof
Let $i \in [n]$. If $i = w(a_m)$ for some $m$, then $w^{-1}(i) = a_m$, so
$$
\bigl(w(a_1\cdots a_k)w^{-1}\bigr)(i)
=
w\bigl((a_1\cdots a_k)(a_m)\bigr)
=
w(a_{m+1}),
$$
where $a_{k+1}=a_1$. If $i \neq w(a_m)$ for every $m$, then $w^{-1}(i)\notin\{a_1,\dots,a_k\}$.
Hence $(a_1\cdots a_k)$ fixes $w^{-1}(i)$, so $\bigl(w(a_1\cdots a_k)w^{-1}\bigr)(i) = ww^{-1}(i) = i.$
Therefore, $w(a_1\cdots a_k)w^{-1} = (w(a_1)\cdots w(a_k)).$ $\square$


>[!Corollary]
>The conjugacy classes of $S_n$ are determined by cycle type.
>i.e. if $v,w \in S_n$, then $v \sim w \iff CT(v)=CT(w)$.
##### Proof
Write $w$ as a product of disjoint cycles $w=(a_1\cdots a_k)(b_1\cdots b_l)\cdots$.
Then 
$$\begin{align*}
gwg^{-1} &= g(a_1\cdots a_k)g^{-1}g(b_1\cdots b_l)g^{-1}g\cdots \\[3pt]
&= (g(a_1)\cdots g(a_k))(g(b_1)\cdots g(b_l))\cdots
\end{align*}$$
So if $v \sim w$, then $CT(w)=CT(v)$.

Conversely, if $CT(w)=CT(v)$, then $w=(a_1\cdots a_k)(b_1\cdots b_l)\cdots$ and $v=(a'_1\cdots a_k')(b_1'\cdots b_l')\cdots$
Let $g$ be the permutation that sends $a_i \mapsto a_i'$ and $b_j \mapsto b_j'$.
Then $gwg^{-1}=v \implies w\sim v$. $\square$


## Partition

>[!Definition]
>A **partition** of $n$ is any such sequence $(\lambda_1,...,\lambda_k)$.
>Let $\mathcal{P}_n = \{\text{partitions of }n\}$.


# Diagram

- Over $\mathbb{C}$, the irreducible modules of $\mathbb{C}S_n$ are indexed by $\mathcal{P}_n$.

>[!Success] Goal
>We want to associate $\lambda \in \mathcal{P}_n$ with irreducible modules $S^\lambda$ over $\mathbb{C}$.

>[!Definition]
>Let $\lambda \in \mathcal{P}_n$. The **diagram** of $\lambda$ is the set $\{(r,c)\:|\: 1 \leq c \leq \lambda_r,\:r \geq 1\}$

## Example
For $\lambda =(4,3,2,1,1)= (4,3,2,1^2)$:
![[Specht Modules-1779190234442.png|400]]

# $\lambda$-Tableaux
## Definition

>[!Definition]
>A **$\lambda$-Tableaux** is a bijection $t:\lambda\to [n]$ where $\lambda$ is the diagram of the $\lambda$ partition.
>
>Define $\text{Tab}(\lambda)=\{\lambda \text{-tableaux}\}$

- for example $\lambda =(4,2)$
  ![[Specht Modules-1779190523564.png|300]]
- $\# \text{Tab}(\lambda)=n!$


# Row/Column Equivalence

>[!Definition]
>Two tableaux $s,t \in \text{Tab}(\lambda)$ are
>- **Row equivalent** if they have the same sets of numbers in each row. $s \sim_{row}t$.
>- **Column equivalent** if they have the same sets of numbers in each column. $s \sim_{col}t$.

![[Specht Modules-1779190939995.png]]


# Row/Column Stabiliser

>[!Definition]
>- The **row stabiliser** of $t$ is $R_t = \{g \in S_n \:|\: gt \sim_{row} t\}$
>- The **column stabiliser** of $t$ is $C_t = \{g \in S_n \:|\: gt \sim_{col}t\}$

## Key Observation

$S_n$ acts on $\text{Tab}(\lambda)$ via composition of maps 
![[Specht Modules-1779191214545.png|400]]
$gt$ is the tableaux obtained by replacing $m$ in $t$ with $g(m)$

For example if $g = (1\:3\:2)$, then
![[Specht Modules-1779191538977.png|450]]

## Lemmas

>[!Lemma]
>Let $t \in \text{Tab}(\lambda)$ and $w \in S_n$. Then
>1. $R_{wt}=wR_tw^{-1}$ and $C_{wt}=wC_tw^{-1}$
>2. $R_t$ and $C_t$ are subgroups of $S_n$
>3. If $g,h \in S_n$ then
> 	  - $gR_t = hR_t \iff gt \sim_{row} ht$
> 	  - $gC_t=hC_t \iff gt \sim_{col}ht$
##### Proof
###### 1.
$$g \in R_{wt} \iff gwt \sim_{row}wt \iff w^{-1}gwt \sim_{row}t \iff w^{-1}gw \in R_t \iff g \in wR_t w^{-1}.$$
Similarly for $C_t$.

###### 2.
NEED TO PROVE

###### 3.
$$gR_t = hR_t \iff h^{-1}g \in R_t \iff h^{-1}gt \sim_{row} t \iff gt \sim_{row} ht.$$
$gC_t=hC_t$ is similar.
$\square$


# Row/Column Standard

>[!Definition]
>A tableaux is 
>- **Row standard** if its entries increase left to right in each row
>- **Column standard** if its entries increase top to bottom in each column
>
>Such tableau are denotes $RStd(\lambda)$ and $CStd(\lambda)$ respectively.


# Row/Column Symmetrisers

Let $\varepsilon:S_n \to \mathbb{F}$ be the sign representation of $S_n$. So $\varepsilon(w) = \pm 1$ for all $w \in S_n$.

>[!Definition]
>Let $t \in \text{Tab}(\lambda)$. Define the **row and column symmetrisers** as
>$$\rho_t = \sum_{x \in R_t} x \in \mathbb{F}S_n\qquad,\qquad \kappa_t = \sum_{x \in C_t} \varepsilon(x)x$$
>respectively, which are elements of the group algebra $\mathbb{F}S_n$.


## Lemmas

>[!Lemma]
>Let $t \in \text{Tab}(\lambda)$ and $g \in S_n$. Then
>1. $g \rho_t = \rho_{gt}g$  and $g\kappa_t=\kappa_{gt}g$
>2. $u \in R_t \implies u \rho_t= \rho_t$
>3. $v \in C_t \implies v \kappa_t = \varepsilon(v)\kappa_t$
##### Proof
$$C_{wt}=wC_tw^{-1} \implies \kappa_{wt} = w\kappa_tw^{-1} \implies \kappa_{wt}w = w\kappa_t$$
$$R_{gt}=gR_tg^{-1}\implies \rho_{gt}=g\rho_tg^{-1}\implies \rho_{gt}g=g\rho_t$$
If $u \in R_t$, then $u \rho_t = \sum_{x \in R_t}ux = \rho_t$ as $x$ and $ux$ range over $R_t$.
If $v \in C_t$, then $v \kappa_t=v \sum_{x \in C_t}\varepsilon(x)x = \sum_{x \in C_t} \varepsilon(x)vx$.
Set $y=vx$, then $y \in C_t$ and $x = v^{-1}y$, Then
$$\sum_{x\in C_t}\varepsilon(x)vx = \sum_{y \in C_t}\varepsilon(v^{-1}y)y = \sum_{y \in C_t}\varepsilon(v^{-1})\varepsilon(y)y = \varepsilon(v) \sum_{y \in C_t}\varepsilon(y)y = \varepsilon(v)\kappa_t$$
where we used the fact that $\varepsilon$ is a group homomorphism, and that $\varepsilon(v)=\varepsilon(v^{-1})$.
$\square$

# Young Permutation Module

- $t^\lambda$ is the row standard $\lambda$-tableaux with $1,2,...,n$ entered in order along the rows

>[!Definition]
>The **Young permutation module** is $M^\lambda = \mathbb{F}S_n\rho_{t^\lambda}$.
>For $t \in \text{Tab}(\lambda)$, let 
>1. $d_t \in S_n$ be the unique permutation such that $t = d_t t^\lambda$ and
>2. $m_t = d_t \rho_{t^\lambda}= \sum_{w \in R_t} wd_t \in M^\lambda$.

>[!Proposition]
>1. $m_t \in M^\lambda$ and $M^\lambda = \mathbb{F}S_nm_t$ for $t \in \text{Tab}(\lambda)$
>2. $M^\lambda$ has basis $\{m_t \:|\: t \in RStd(\lambda)\}$
>3. If $g \in S_n$, then $gm_t=m_{gt}=m_s$ where $s \in RStd(\lambda)$ is unique with $gt \sim_{row}s$ 
##### Proof
###### 1.
Since $m_t = d_t\rho_{t^\lambda} \in M^\lambda$, then $\rho_t=d_t^{-1}m_t \in \mathbb{F}S_nm_t$.
Hence $M^\lambda=\mathbb{F}S_nm_t$ for all $t \in \text{Tab}(\lambda)$.

###### 3.
If $g \in S_n$, then $gm_t=gd_t\rho_{t^\lambda}$.
Since $gd_t = d_{gt}$, then $gm_t = d_{gt}\rho_{t^\lambda}=m_{gt}$.

For the second equality, 
$$m_t= \sum_{v \in R_{t^\lambda}}d_tv = \sum_{x\in d_tR_{t^\lambda}} x = \text{sum over coset } d_tR_{t^\lambda}$$
If $s \in RStd(\lambda)$ with $gt \sim_{row} s$, then 
$$gm_t=\sum_{x \in gd_tR_{t^\lambda}}x=\sum_{x \in d_sR_{t^\lambda}} x = m_s$$

###### 2.
By definition $M^\lambda$ is spanned by $\{gm_{t^\lambda}=g\rho_{t^\lambda} \:|\: g \in S_n\}$.
By part (3), $gm_{t^\lambda}=m_{gt^{\lambda}}= m_s$ for some unique $s \in RStd(\lambda)$ with $s \sim_{row} gt^\lambda$.
Hence $\{m_s \:|\: s \in RStd(\lambda)\}$ span $M^\lambda$
If $\sum_{s \in RStd(\lambda)} r_sm_s=0 \implies \sum_{s \in RStd(\lambda)} r_sd_s \sum_{v \in R_{t^\lambda}}v =0 \implies r_s =0$ 
since $S_n = \bigsqcup_{s \in RStd(\lambda)}d_s S_\lambda$ since the row-standard $s$ index the coset of $S_\lambda$ in $S_n$.

Then $M^\lambda=\mathbb{F}S_n \rho_{t^\lambda} =\langle m_s \:|\: s \in RStd(\lambda) \rangle$.
$\square$


# Specht Module

>[!Definition]
>Let $\lambda \in \mathcal{P}_n$. The **Specht module** $S^\lambda$ is 
>$$S^\lambda=\mathbb{F}S_n\kappa_{t^\lambda}\rho_{t^\lambda}\subseteq M^\lambda$$
>

- For any $t \in \text{Tab}(\lambda)$ set $e_t = \kappa_tm_t \in M^\lambda$.

>[!Proposition]
>1. Let $t \in \text{Tab}(\lambda)$. Then $e_t \in S^\lambda$. Moreover, $S^\lambda = \mathbb{F}S_n e_t$.
>2. If $g \in S_n$, then $ge_t=e_{gt}$.
>3. $S^\lambda$ is spanned by $\{e_t \:|\: t \in \text{Tab}(\lambda)\}$.
##### Proof
###### 2.
By definition, $S^\lambda=\mathbb{F}S_n\kappa_{t^\lambda}\rho_{t^\lambda}$, and $m_{t^\lambda}= \rho_{t^\lambda}$. So $S^\lambda= \mathbb{F}S_n e_{t^\lambda}$.
If $g \in S_n$, then $ge_t= g \kappa_t m_t = \kappa_{gt}\cdot gm_t = \kappa_{gt}m_{gt}=e_{gt}$ which proves (2).

###### 1.
In particular, $d^{-1}_te_t=e_{d^{-1}_tt}=e_{t^\lambda}$.
so $e_{t^\lambda}\in \mathbb{F}S_ne_t$, and hence $S^\lambda \subseteq \mathbb{F}S_ne_t$.

By definition, $e_t=\kappa_tm_t=\kappa_td_tm_{t^\lambda}=d_t\kappa_{t^\lambda}m_{t^\lambda}$. Hence $e_t = d_te_{t^\lambda}\in S^\lambda\implies \mathbb{F}S_ne_t \subseteq S^\lambda$
Combining with the previous dot point gives $S^\lambda=\mathbb{F}S_ne_t$.

###### 3.
$S^\lambda$ is spanned by $\{ge_{t^\lambda}\:|\: g \in S_n\} = \{e_t \:|\: t \in \text{Tab}(\lambda)\}$ using (2).
$\square$


# Dominance

>[!Definition]
>Define a **partial order** on $\mathcal{P}_n$, such that $\lambda \trianglerighteq\mu$ ("$\lambda$ dominates $\mu$") if
>$$\sum_{i=1}^r \lambda_i \geq \sum_{i=1}^r \mu_i$$
>for all $r\geq1$.

![[Specht Modules-1779277892123.png|380]]

## Key Lemma

>[!lemma]
>Let $s \in \text{Tab}(\lambda)$, $t \in \text{Tab}(\mu)$ for $\lambda,\mu \in \mathcal{P}_n$ and suppose that $\kappa_sm_t \neq 0$.
>Then $\lambda \trianglerighteq \mu$. 
>Moreover, if $\lambda = \mu$ then $\kappa_sm_t=\pm e_s$.
##### Proof