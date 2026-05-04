# Definition

>[!Definition]
>Let $X,Y$ be normed vector spaces.
>An operator $T \in \text{Hom}(X,Y)$ is **compact** if
>$$B\subseteq X \text{ compact } \implies T(B) \text{ is \textbf{relatively compact}}$$
>i.e. $\overline{T(B)}$ is compact in $Y$.


# Propositions

>[!Proposition]
>$$T \text{ compact }\implies T \text{ continuous }$$
##### Proof
Let $B = \{x \in X \:|\: \|x\| \leq 1\}$ be bounded. So $\overline{T(B)}$ is compact and hence bounded.
So $\|Tx\|\leq M$ whenever $\|x\|\leq 1$.
So $T \in \mathcal{L}(X,Y)$ with $\|T\|\leq M$. $\square$

>[!Proposition]
>Let $X,Y$ be normed spaces and $T \in \mathcal{L}(X,Y)$. Then
>$$T \text{ is compact } \iff T(\overline{B(0,1)}) \text{ is relatively compact}$$
##### Proof
NEED TO PROVE

>[!Proposition]
>Let $X$ be a normed space. 
>The identity $I:X \to X$ is compact $\iff$ $\dim(X) < \infty$.
##### Proof
If $I$ is compact,  $\overline{I(\overline{B(0,1)})} = \overline{B}(0,1)$ is compact, so $\dim(X) < \infty$ from before.

Conversely if $\dim(X)<\infty$, Then $\overline{B}(0,1)= \overline{I(\overline{B(0,1)})}$ is compact by [[Main Definitions|Fish's Heine-Borel]], so $I$ is compact by the previous proposition. $\square$



# Characterisation of Compact Operators

>[!Theorem]
>Let $X,Y$ be normed spaces and $T \in \mathcal{L}(X,Y)$. Then the following are equivalent.
>1. $T$ is compact
>2. If $(x_n)_{n\geq1}$ is bounded in $X$, then $(Tx_n)_{n\geq 1}$ has a convergent subsequence in $Y$.
##### Proof
###### 1 -> 2
Let $(x_n)_{n\geq 1}$ be bounded in $X$. Then $B = \{x_n \:|\: n\geq 1\}$ is bounded and so

###### 2 -> 1