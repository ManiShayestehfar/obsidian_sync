>[!example] Theorem
>Suppose $V$ is an $A$-module such that 
>$$V = V_0 \supset V_1 \supset ... \supset V_r \supset 0 \quad \text{and}\quad V = V_0' \supset V_1' \supset ... \supset V_s' \supset 0$$
>are two composition series of $V$. Then:
>1. $r=s$, and 
>2. For each irreducible $A$-module $D$
>   $$\#\{0 \leq i < r \:|\: V_i /V_{i+1} \cong D\} \:\:=\:\: \#\{0 \leq i < s \:|\: V_i' /V_{i+1}' \cong D\}$$
>   i.e. the *length* of a composition series only depends on $V$ 
##### Proof
We prove by induction on $\dim V$.  If $\dim V = \{0,1\}$ then we are done. Assume we have the composition series
$$V = V_0 \supset V_1 \supset ... \supset V_r \supset 0 \quad \text{and}\quad V = V_0' \supset V_1' \supset ... \supset V_s' \supset 0.$$
We want to show that $r=s$ and $V_i/V_{i+1}$ and $V_i'/V_{i+1}'$ match (up to multiplicity and isomorphism)

---
**Base Case:** $r=s=1$

If $V_1=V_1'$, then we are done by induction as $\dim V_1 < \dim V$. So assume $V_1 \neq V_1'$.

Since $V_1$ and $V_1'$ are *maximal submodules*, their quotients (by [[A-Module|Isomorphism Theorem 4]]) $E=V/V_1$ and $E'=V/V_1'$ are *irreducible*. Therefore $V = V_1 + V_1'$.

By the [[A-Module|2nd Isomorphism Theorem]], 
$$\begin{align*}
E = V/V_1 = (V_1 + V_1')/V_1 &\cong V_1'/(V_1 \cap V_1') \\[4pt]
E' = V/V_1' = (V_1+V_1')/V_1' &\cong V_1/(V_1\cap V_1')
\end{align*}$$
So both $E,E'$ are isomorphic to the quotients above the intersection $V_1 \cap V_1'$, and again by Theorem 4, $V_1\cap V_1'$ is a maximal submodule of $V_1$ and $V_1'$.  

The composition factors of $V$, $E$, are given by the following diagram:

![[Jordan-Holder Theorem-1749185907551.png|270]]

So now we just need to understand the composition factors below the diamond.

**Induction:** $r=s=t$

Choose a composition factor for $V_1\cap V_1' = W_2 \supset W_3 \supset ... \supset W_t \supset 0$. Extending upwards gives
$$\begin{align*}
V_1 &\supset W_2 \supset ... \supset 0 \\
V_1' &\supset W_3 \supset ... \supset 0
\end{align*}$$
So both $V_1,V_1'$ have composition series of length $t+1$ and their composition factors include $E' = V/V_1'$ and $E = V/V_1$, as well as the $t$ factors from the shared submodule $V_1 \cap V_1'$. 

So from this we have $r = \text{length of series for } V = V_1 \to ... \to 0 = t$ so $r = t$. Similarly $s=t$
Therefore $r = s = t$.  $\square$

**Last Part of proof**

If $D \neq E,E'$ then it can only appear as a composition factor of $V_1 \cap V_1'$. So by induction the composition multiplicity (count) of $D$ in $V$ does not depend on the choice of filtration. 

If $D=E,E'$, since the diagram is symmetric, the composition factor appear once on opposite sides of the diamond and so again the composition multiplicity is fixed.

Hence not matter how you choose the composition series, the simple factors (with multiplicity) are the same. $\square$ 


