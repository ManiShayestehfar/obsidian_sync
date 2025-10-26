
>[!lemma] Algebraic MV-sequence
>Consider the commutative diagram of abelian groups with exact rows and $f_n''$ isomorphisms:
>![[Mayer-Vietoris Sequence-1761458109267.png|600]]
>Then, there exists an exact sequence
>$$\cdots \overset{}{\longrightarrow}C_n' \overset{(i_n,f_n')}{\longrightarrow}C_n \oplus D_n' \overset{(f_n-j_n)}{\longrightarrow} D_n \overset{\Delta_n}{\longrightarrow}C_{n-1}' \overset{(i_{n-1},f_{n-1}')}{\longrightarrow}\cdots$$
>where $\Delta_n := \partial_n \circ (f_{n}'')^{-1} \circ q_n: D_n \to C_{n-1}'$

Take $A,B,X$ where $X = \text{int }A \cup \text{int }B$. Consider the following diagram:
![[Mayer-Vietoris Sequence-1761469589200.png]]
##### Proof (of Alg. MV-Seq)

We prove the exactness of $C_{n-1}'$. We need to prove that $\text{im }\Delta_n = \ker(i_{n-1},f_{n-1}')$

1. **Claim:** $(i_{n-1},f_{n-1}') \circ \Delta_n = 0$. See that
   $i_{n-1}\circ \Delta_n = \underbrace{i_{n-1} \circ (\partial_n}_{=0} \circ (f_n'')^{-1}\circ q_n)$ , and
   $f_{n-1}'\circ \Delta_n = f_{n-1}' \circ \partial_n \circ (f_{n}'')^{-1} \circ q_n = \partial_n' \circ q_n = 0$.
   Hence $\text{im }\Delta_n \subseteq \ker(i_{n-1}, f_{n-1}')$.

2. **Claim:** $\ker(i_{n-1}, f_{n-1}')\subseteq \text{im }\Delta_n$. 
   Take $c_{n-1}' \in \ker(i_{n-1},f_{n-1}')$. Then $i_{n-1}(c_{n-1}')=0$ and $f_{n-1}'(c_{n-1}') = 0$. Hence there exists $c_n'' \in C_n''$ such that $\partial_n(c_n'') = c_{n-1}'$. Then from commutativity of the diagram
   $0  = f_{n-1}(c_{n-1}')=f_{n-1}'(\delta_{n-1}(c_n'')) = \partial_n'(f_n''(c_n''))$. hence $f_n''(c_n'') \in \ker \partial_n' = \text{im }q_n$.
   i.e. there exists $d_n \in D^n$ such that $q_n(d_n)= f''(c_n'')\implies \Delta_n(d_n)= \partial_n(f_n''^{-1}(q_n(d_n))) = \partial_n(c_n'') = c_{n-1}'$. $\square$



>[!def] Unreduced MV-seq
>Applying the algebraic MV-seq from before, gives us the **(unreduced) MV-seq**
>![[Mayer-Vietoris Sequence-1761469992697.png]]

- Another way to look at it: $[\alpha] = x+y$ where $x \in C_n(A)$ and $y \in C_n(B)$. Then $\partial(x+y) = 0 \implies \partial x = -\partial y$ so $x,y$ both must lie in $C_n(A\cap B)$. So we have the map $[\alpha]\longmapsto \partial x$.
- The sequence in exact.

>[!def] Reduced MV-seq
>![[Mayer-Vietoris Sequence-1761470219147.png]]

**Note:** The $H_1$-terms of the sequence gives the abelian version of the [[Van Kampen's Theorem]] 




# Example

Take $X=S^n$, $A = U,B= L$. 
$A\cap B= S^{n-1}\neq \emptyset$
$X = \text{int }A \cup \text{int }B$.

Note that $U \cong D^n \cong L$. Then 
$\widetilde{H_i}(A) \cong \widetilde{H_i}(B) \cong 0$
$\implies \widetilde{H_i}(X) \cong \widetilde{H}_{i-1}(A\cap B)$
$\implies \widetilde{H_i}(S^n) \cong \widetilde{H}_{i-1}(S^{n-1})$
Hence we can calculate the homology groups of $S^n$ by induction.

