>[!def] Filtration
>Let $V$ be and $A$-module. Then a **filtration** of $V$ is the series of submodules
>$$V = V_0 \supset V_1 \supset ... \supset V_r \supset 0$$

>[!def] Composition Series
>A **composition series** for $V$ is a filtration such that each of the quotient modules $V_i / V_{i+1}$ is an irreducible $A$-module for $1 \leq i \leq r$.
>
>An $A$-module $D$ is a **composition factor** of $V$ if $D \cong V_i / V_{i+1}$ for some composition series of $V$. 


 >[!lemma]
 >Suppose $V$ is an $A$-module. Then $V$ has a composition series
##### Proof

If $V$ is irreducible we are done. Suppose $V$ is not irreducible. Then we can find a maximal proper submodule $V_0$ of $V$. Such submodule exists since:
1. The Ascending Chain Condition holds, and
2. $V/V_0$ is irreducible by construction

hence $V \supset V_0 = V_1 \supset V_2 \supset ... \supset V_r \supset 0$ is a composition series of $V$. $\square$ 

>[!lemma] 
>Suppose that $D$ is an irreducible $A$-module. Then $D$ is a composition of factor. i.e. $D \cong V_i / V_{i+1}$ for some composition series of $V$.
##### Proof

By the proof [[A-Module|here (see Some Propositions 1)]] , $D \cong A/M$ for some maximal submodule $M$ of $A$. By the last lemma, $M$ has a composition factor $M = M_0 \supset M_1 \supset ... \supset M_r \supset 0$. Hence, we extend the filtration to $A \supset M$ which is a composition series of $A$ with first composition factor $A/M \cong D$, as required $\square$ 

>[!warning]
>If $V$ is irreducible it has a unique composition series. If $V$ is reducible then it can have many different filtrations and composition series. See [[Jordan-Holder Theorem]] for more.