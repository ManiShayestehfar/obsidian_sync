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
Recall that $\# \text{Irr}(A) = \# \text{Irr}(\overline{A}) \leq \dim \overline{A}/[\overline{A},\overline{A}]$


