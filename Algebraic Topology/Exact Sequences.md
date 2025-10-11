- basic definitions are skipped

**Recall:** A sequence $\cdots \overset{}{\longrightarrow}A_{n+1} \overset{\alpha_{n+1}}{\longrightarrow}A_{n} \overset{\alpha_{n}}{\longrightarrow}A_{n-1} \overset{\alpha_{n-1}}{\longrightarrow}\cdots$  is a **chain complex** if $\text{im }\alpha_{n+1}\subseteq \ker \alpha_{n}$

$\implies$ A chain complex is exact $\iff$ all its homology groups are trivial. 

**An important case:**
$1 \overset{}{\longrightarrow}A \overset{\alpha}{\longrightarrow}B \to 1$ is exact $\iff$ $\ker \alpha=1$, $\text{im }\alpha =B$ $\iff \alpha$ is an isomorphism

![[Exact Sequences-1760164390043.png]]


# Short Exact Sequence of Chain Complexes

The **SES of chain complexes** is the following diagram where 
- *horizontal* subdiagrams are chain complexes
- *vertical* subdiagrams are SES of groups

![[Exact Sequences-1760164971994.png|500]]

## Theorem 1

>[!theorem] H 2.16
>A SES of chain complexes induces a long exact sequence of homology groups
>
>![[Exact Sequences-1760165061462.png|550]]
##### Proof
All squares of the diagram for SES chain complexes commute. i.e. $i,j$ are both chain maps. Chain maps induce homomorphisms of homotopy groups (by previous proposition in [[Singular Homology]]): 
$$\begin{align*}
i_*&: H_n(A) \longrightarrow H_n(B) \\
j_*&: H_n(B) \longrightarrow H_n(C)
\end{align*}$$
Need to define $\partial:H_n(C) \to H_{n-1}(A)$ called the *boundary map*.
Let $c \in C_n$ be a cycle. i.e. $c \in \ker \partial$. Since $j$ is surjective, $c = j(b)$ for some $b \in B_n$. Since the square
 ![[Exact Sequences-1760166799117.png|150]]
 commutes, we have $(j \circ \partial)(b) = (\partial \circ j)(b) = \partial(c) = 0$ so $\partial(b) \in \ker j$.

Now $ker j = \text{im } i$ (by exactness), so $\partial(b)=i(a)$ for some $a \in A_{n-1}$. Also $(i \circ \partial)(a) = (\partial \circ i)(a) = 0$ because 
![[Exact Sequences-1760167006142.png|180]]
commutes.

Since $i$ is injective, $i(\partial)=0 \implies \partial(a)=0$ so $a \in \ker \partial$ is a cycle. 

Define $\partial: H_n(C)\to H_{n-1}(A)$ by $[c] \longmapsto [a]$ for $a$ defined from $c \in \ker \partial\subseteq C_n$ as above.

*Well-definedness (for a):* Given $c$, $a$ is chosen such that $i(a) = \partial(b)$. Suppose $j(b) = j(b')=c$. Then $b'-b \in \ker j = \text{im }i$. So $b'-b=i(a')$ for some $a' \in A_n$. i.e. $b' = b + i(a')$. 
Now $\partial b'=\partial(b+i(a')) = \partial(b) + \partial(i(a')) = i(a) + i(\partial(a')) = i(a + \partial(a'))$. 
We also have that $(a + \partial a') - a = \partial a' \in \text{im }\partial_n^A$.
Hence $[a]=[a+\partial a']$ in $H_{n-1}(A)$ i.e. choice of $b$ is not necessarily unique but choosing a different $b$ still gives some representative of $[a]$ in $H_{n-1}(A)$. $\therefore [a]$ is well-defined given $c$.

*Well-definedness (for c):* If $c' \in [c]$ then $c' = c + \partial c''$ for some $c''\in C_{n+1}$. Since $j$ is surjective, $c'' =j(b'')$ for some $b'' \in B_{n+1}$. Then $c +\partial c''= j(b) + \partial(j(b'')) = j(b) + j(\partial(b'')) = j(b+\partial b'')$. Also $\partial(b + \partial b'') = \partial(b) + \partial(\partial(b'')) = \partial(b)$. 

Since $a$ only depends on $\partial b$, we get the same $a$ from $c'$ as from $c$. $\therefore [a]$ is well defined given $[c]$, and so $\partial: H_n(C) \to H_n(A)$ is well-defined.

*Homomorphism:* Let $c_1,c_2 \in C_n$ be cycles with $\partial([c_1])=[a_1]$ and $\partial([c_2])=[a_2]$. i.e. $a_1,a_2$ are defined by $c_k=j(b_k)$ where $\partial b_k = i(a_k)$ for $k=1,2$.

Then $j(b_1+b_2)=j(b_1)+j(b_2)=c_1+c_2$, $i(a_1+a_2)=i(a_1)+i(a_2)=\partial(b_1)+\partial(b_2)=\partial(b_1+b_2)$ so $\partial([c_1+c_2])= [a_1+a_2]$. 
Now $[a_1+a_2]=[a_1]+[a_2]= \partial([c_1]) + \partial([c_2])$ and therefore $\partial$ is a homomorphism.

*Exactness:* There are 6 things to check:

1. $\text{im} i_* \subseteq \ker j_*:$
2. $\text{im} j_* \subseteq \ker \partial:$
3. $\text{im} \partial \subseteq \ker i_*:$
4. $\ker j_* \subseteq \text{im } i_*:$
5. $\ker \partial \subseteq \text{im } j_*:$
6. $\ker  i_* \subseteq \text{im } \partial:$
 
## Theorem 2

>[!theorem] H 2.13
>Let $(X,A)$ be a [[Topological Space|good pair]], $i:A\to X$ is inclusion, and $j:X \to X/A$ the quotient map. 
>Then there is a long exact sequence in reduced homology:
>
>![[Exact Sequences-1760165346117.png|570]]

### Related Corollary

>[!Corollary]
>For $n,k \geq 0$, $$\widetilde{H}_k(S^n) = \begin{cases}
\mathbb{Z} & k=n  \\
0 & \text{otherwise}
\end{cases}$$
##### Proof
Fix $n \geq 1$. For $k \geq 1$ we have

![[Exact Sequences-1760165542188.png|370]]

since $D^n / S^{n-1}\cong S^n$.

Now $\widetilde{H}_k(D^n) = 0$ $\forall k \geq 0$ as $D^n$ is contractible. So $\forall n,k \geq 1$, $\widetilde{H}_k(S^n) \cong \widetilde{H}_{k-1}(S^{n-1})$.
Now $H_0(S^0) \cong \mathbb{Z} \oplus \mathbb{Z}$ (two path components). So $\widetilde{H}_0(S^0)\cong \mathbb{Z}$ so setting $k=n$ and inducting we get $\widetilde{H}_n(S^n) \cong \mathbb{Z}$   $\forall n \geq 0$.

For $k > n$ by induction: $\widetilde{H}_k(S^n) \cong \widetilde{H}_{k-n}(S^0) \cong 0$.
For $k < n$ by induction: $\widetilde{H}_k(S^n) \cong \widetilde{H}_{0}(S^{n-k}) \cong 0$.   $\square$
<mark style="background: #FF5582A6;">(NOT SURE WHY THESE ARE TRUE)</mark>



