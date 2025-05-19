>[!info] Definition: Filtration
>Let $V$ be and $A$-module. Then a **filtration** of $V$ is the series of submodules
>$$V = V_0 \supset V_1 \supset ... \supset V_r \supset 0$$

>[!info] Definition: Composition Series
>A **composition series** for $V$ is a filtration such that each of the quotient modules $V_i / V_{i+1}$ is an irreducible $A$-module for $1 \leq i \leq r$.
>
>An $A$-module $D$ is a **composition factor** of $V$ if $D \cong V_i / V_{i+1}$ for some composition series of $V$. 


 >[!tip] Lemma
 >Suppose $V$ is an $A$-module. Then $V$ has a composition series
##### Proof

If $V$ is irreducible we are done. Suppose $V$ is not irreducible. Then we can find a maximal proper submodule $V_0$ of $V$. Such submodule exists since:
1. The Ascending Chain Condition holds, and
2. $V/V_0$ is irreducible by construction

