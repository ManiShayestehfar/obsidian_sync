
>[!info] Definition
>A function $P$ defined on a set of all events is a **Probability Measure/Function** if:
>
>1. $P(\Omega) = 1$
>2. $P(A) \geq 0$ for every event $A$
>3. If $A_1,A_2,...$ are mutually disjoint events (i.e for $i\neq j$, $A_{i}\cap A_{j} = \emptyset$), then
>$$P\left(\bigcup_{n=1}^{\infty} A_{n}\right) = \sum\limits_{n=1}^{\infty}P(A_{n})$$
>
>
>
 
- Properties 1 and 3 of the definition beg the existence of [[Banach-Tarski Paradox]].

- If $A,B$ are disjoint events then $P(A\cup B) = P(A) + P(B)$ 


>[!tip] Claim 1
>Notice that Property 3 is also *finitely* true. i.e
>$$P\left(\bigcup_{i=1}^{n} A_{i}\right) = \sum\limits_{i=1}^{n}P(A_{i})$$
##### Proof
Step 1: By definition $\Omega \in \mathcal{F} \implies \mathcal{F}^{c}\equiv \emptyset \in \mathcal{F}$
Step 2: Since a finitely many collection of sets is certainly countable, then Property 3 of [[Sigma-Algebra|Sigma-Algebras]] holds for finitely many disjoint sets.
Step 3:  Assuming $\Omega \neq \emptyset$, then $\Omega \cup \emptyset = \Omega$. Then:
$$1 = P(\Omega) = P(\Omega \cup \emptyset) = P(\Omega) + P(\emptyset) = 1 + P(\emptyset),$$
and therefore $P(\emptyset) = 0$.

Finally, for $j \geq n+1$, $A_{j}= \emptyset$. Applying Property to this collection $\{A_1,...,A_{n}, \emptyset, \emptyset, ...\}$, and remembering that $P(\emptyset ) = 0$, provides the proposition's result. $\square$  


for example for $n=2$, $P(A \cup B) = P(A) + P(B)$

#### What if $A$ and $B$ are not disjoint?

> [!tip] Claim 2
> $\forall A,B\in \mathcal{F}$,   $P(A \cup B) = P(A) + P(B) - P(A \cap B)$
##### Proof
Write $A\cup B$ as disjoint union: $A \cup B = A \sqcup (B\backslash A)$, where 
$$B\backslash A = B \cap A^{c}\in \mathcal{F}\quad{\color{teal} \text{(this can  be shown)}}$$ 
Hence, $P(A \cup B) = P(A) + P(B\backslash A)$. Similarly you can define $B$ as 
$$\begin{align*}B &= (B\backslash A)\sqcup(B\cap A) \\[3pt] \implies P(B) &= P(B\backslash A) + P(B\cap A)   \end{align*}$$
and $\therefore P(A \cup B) = P(A) + P(B) - P(A \cap B).\quad \square$

