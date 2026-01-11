
# Nilpotent Ideal

An ideal $I$ of $A$ is **nilpotent** if $I\neq0$ and $I^n=0$ for some $n>0$.

>[!proposition]
>Suppose $I$ is a submodule of $A$ such that $I^n\neq0$. Then $I$ contains an idempotent.
##### Proof
Let $J$ be the smallest/minimal non-nilpotent ideal contained in $I$ (so every ideal of $J$ is nilpotent). Let $K$ be a minimal ideal of $J$ such that $JK\neq0$. $K$ exists because $J^2 \neq 0$ since $J$ is not nilpotent.
Let $x \in K$ such that $Jx\neq0$, Then $K=Jx$ by minimality of $K$. Hence there exists an element $e \in J$ such that $x = ex$. Consequently $x = ex=e^2x=\cdots$. In particular $e$ is nonzero.

If $e^2 = e$ then $e$ is idempotent and we are done. Otherwise, let $N = \{a\in J\:|\: ax=0\}$. Then $e - e^2 \in N$, so $N$ is a nonzero ideal of $J$. Also $N \neq J$ since $e \not\in N$. However, $J$ is a minimal non-nilpotent ideal, so $N$ must be nilpotent.

Set $e_0=e$ and $e_{i+1}=3e_i^2-2e_i^2$.
**Claim:** If $i\geq 0$, then $e_i-e_i^2\in N^{2^i}$ and $x = e_ix=e_i^2x=\cdots$

To prove this, we use induction on $i$. 
- If $i=0$ then $e_0=e$, $e_0-e_0^2\in N$, and $x=e_ix=e_i^2x=\cdots$ so the claim is true.
- By induction assume the claim for $e_i$. Therefore $e_{i+1}x=(3e_i^2-2e_i^2)x=x$ and ![[Ring-1767874849382.png]]
  where the last line follows by induction since $e_i-e_i^2 \in N^{2i}$. This completes the proof of claim.

Now we are done because $e_i\neq0$ for i since $x=e_ix$. On the other hand, $N$ is nilpotent, so $N^k=0$ for some $k>0$. In particular $N^{2^i}=0$ for $i >0$ so $e_i-e_i^2=0$ for $i >0$. That is, $e_i=e_i^2$ is an idempotent (and $e_i=e_{i+1}$) as soon as $N^{2^i}=0$.  $\square$

## Properties

1. If $I,J$ are nilpotent, then so is $I + J$.
2. Every submodule of $A$ contains a unique maximal nilpotent ideal
  *proof:* Take $N$ and $N'$ to be two maximal nilpotent ideals of a submodule $V$ of $A$. Then by result (1) above, $N + N'$ is also a nilpotent ideal of $V$. Hence $N = N + N' = N'$ by maximality.



# Radical Ideal

The **radical ideal** $\text{Rad } A$ of $A$ is its unique maximal nilpotent submodule.
If $V$ is an $A$-module then the **radical** of $V$ is $\text{Rad }V = (\text{Rad }A)V$.

- Let $V$ be an $A$-module and define $\text{Rad }^kV:= (\text{Rad }A)^k V$. Then $$V = \text{Rad }^0V\supseteq \text{Rad}^1V\subseteq \text{Rad }^2V \cdots \supseteq \text{Rad }^n V \supseteq 0.$$
  because $(\text{Rad }A)^n= 0$ for some $n >0$ since $\text{Rad }AS$ is a nilpotent ideal. 


## Lemma

>[!lemma] 
>1. The radical $\text{Rad }A$ of $A$ is a two-sided ideal
>2. Suppose $P$ is a principal indecomposable $A$-module. Then $\text{Rad } P = P \cap \text{Rad }A \subsetneq P$ is the maximal nilpotent submodule of $P$, which is a proper ideal of $P$.
##### Proof
1. TBD
2. From Property (2) above, $P$ has a unique maximal nilpotent submodule $N$. Certainly $N \subseteq P \cap \text{Rad }P$. 
   For the other direction, $P \cap \text{Rad }P$ is a nilpotent submodule of $P$, and therefore it is contained in $N$. Thus the result.


## Theorem

Let $A$ be a finite dimensional $\mathbb{F}$-algebra.

>[!theorem] 
>1. Suppose $P$ is a principal indecomposable $A$-module. Then $\text{Rad }P$ is the unique maximal proper submodule of $P$. Consequently, $P/\text{Rad }P$ is an irreducible $A$-module.
>2. Suppose that $P$ and $Q$ are principal indecomposable $A$-modules. Then $P \cong Q \iff P/\text{Rad }P \cong Q/\text{Rad }Q$.
>3. Suppose $D$ is an irreducible $A$-module. Then $D \cong P/\text{Rad }P$ for some principal indecomposable $A$-module $P$.


