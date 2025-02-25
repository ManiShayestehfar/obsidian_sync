
>[!info] Definition
>A collection of subsets of $\Omega, \mathcal{F},$ is a $\sigma-$algebra if:
>1. $\Omega \in \mathcal{F}$
>2. $A \in \mathcal{F} \implies A^{c}\in \mathcal{F}$ 
>3. $A_1,A_{2,...}\in \mathcal{F} \implies \bigcup_{n=1}^{\infty}A_{n}\in \mathcal{F}$ (w.r.t a countable union)

- Let $\Omega = \{1,2,3,4,5,6\}$. Then $\mathcal{F}$ = power set of $\Omega$ = $2^{\Omega}$  

>[!tip] Proposition
>if $A,B \in \mathcal{F}$, then $A \cap B \in \mathcal{F}$
>
>**Proof**
>$A,B \in \mathcal{F} \overset{(2)}{\implies} A^c , B^c \in \mathcal{F} \overset{(3)}{\implies} A^{c}\cup B^{c}\in \mathcal{F} \overset{\small \text{de M.}}{\implies} (A\cap B)^c \in \mathcal{F} \overset{(2)}{\implies} A\cap B \in \mathcal{F}$



