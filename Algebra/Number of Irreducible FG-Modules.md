# p'-Conjugacy Classes

Fix prime $p >0$.

>[!Definition]
>A **$p'$-element** of $G$ is any element $x \in G$ such that $p \nmid |x|$ 

>[!Definition]
>A **$p'$-conjugacy class** is a conjugacy class consisting of $p'$-elements.

## Brauer's Theorem

>[!Theorem] Brauer's Theorem
>Let $\mathbb{F}$ be a field of characteristic $p \geq 0$. Then 
>$$\# \text{Irr}(\mathbb{F}G) \:\leq\: \# p'\text{-conjugacy classes}$$
>with equality of $\mathbb{F}G$ is Schurian.
##### Proof
NEED TO PROVE


# Strategy To find $\# \text{Irr}(A)$

$\mathbb{F}G$ is not necessarily semisimple. In turn, we can consider $\overline{\mathbb{F}G} = \mathbb{F}G/ \text{Rad}\mathbb{F}G$.
But $\text{Rad}\overline{\mathbb{F}G} = 0$ so $\overline{\mathbb{F}G}$ is semisimple. 

>[!failure] Notation
>$$R = \text{Rad }A\qquad,\qquad T = [A,A] \qquad,\qquad S = R+T \qquad,\qquad \overline{A} = A/R = A/\text{Rad }A$$

>[!Proposition]
>Let $A$ be a finite dimensional $\mathbb{F}$-algebra. Then
>$$\# \text{Irr}(A) \leq \dim A/S$$
>with equality if $A$ is Schurian.
##### Proof
Recall that $\# \text{Irr}(A) = \# \text{Irr}(\overline{A}) \leq \dim \overline{A}/[\overline{A},\overline{A}]$ (with equality if $A$ is Schurian  $\iff$ $\overline{A}$ is Schurian)
Now,
$$\begin{align*}
[\overline{A}, \overline{A}] &= \langle (a+R)(b+R) - (b+R)(a+R) \:|\: a,b \in A \rangle \\[3pt]
&= \langle (ab-ba) + R \:|\: a,b \in A \rangle \\[3pt]
&= (T+R)/R.
\end{align*}$$
Hence $[\overline{A}, \overline{A}] = S/R$. Thus 
$$\overline{A} / [\overline{A}, \overline{A}] = (A/R)/(S/R) \cong A/S$$
by the second isomorphism theorem.
Hence $\# \text{Irr}(A) \leq \dim A/S$.  $\square$


Now specialise to: $A = \mathbb{F}G$.

Fix a choice $\{x_1,...,x_t\}$ of conjugacy class representatives such that $\{x_1,...,x_s\}$ is the set of $p'$-conjugacy reps.

>[!Success] Goal
>$\{x_1+S,...,x_s + S\}$ is a basis of $\mathbb{F}G/S$.
>i.e. $p \mid |x_i|$

>[!Lemma]
>$\{x_1+T,...,x_t+ T\}$ is a basis of $\mathbb{F}G/T$
##### Proof
The elements of $G$ give a basis for $\mathbb{F}G$

