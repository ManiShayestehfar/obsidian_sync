
![[partition.png|450]]

>[!success] Theorem
> If the events $\{B_n\}$ form a *countable* partition of  $\Omega$, then $\forall A \in \mathcal{F}$
> $$P(A) = \sum_n P(A|B_n)P(B_n)$$ 
##### Proof
$P(A) = P(A\cap \Omega) = P(A \cap \sqcup_n B_n)$.

Using[[Basic Definitions| Distributive laws]] 
$$\begin{align*} P(A) &= P\left(\bigsqcup_n (A \cap B_n) \right) \\[5pt]
&= \sum_n P(A \cap B_n) \\[5pt] &= \sum_n P(A|B_n) P(B_n) \quad \square \end{align*} $$
