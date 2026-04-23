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
We aim to show this in the proof below.

# Strategy To find $\# \text{Irr}(A)$

$\mathbb{F}G$ is not necessarily semisimple. In turn, we can consider $\overline{\mathbb{F}G} = \mathbb{F}G/ \text{Rad}\mathbb{F}G$.
But $\text{Rad}\overline{\mathbb{F}G} = 0$ so $\overline{\mathbb{F}G}$ is semisimple. 

>[!failure] Notation
>$$R = \text{Rad }A\qquad,\qquad T = [A,A] \qquad,\qquad S = R+T \qquad,\qquad \overline{A} = A/R = A/\text{Rad }A$$

## Upper bound

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


**Now specialise to:** $A = \mathbb{F}G$.

Fix a choice $\{x_1,...,x_t\}$ of conjugacy class representatives such that $\{x_1,...,x_s\}$ is the set of $p'$-conjugacy reps.

## Finding Basis

>[!Success] Goal
>$\{x_1+S,...,x_s + S\}$ is a basis of $\mathbb{F}G/S$.
>i.e. $p \mid |x_i| \iff s < i \leq t$

>[!Lemma]
>$\{x_1+T,...,x_t+ T\}$ is a basis of $\mathbb{F}G/T$
##### Proof
###### Spanning 
The elements of $G$ give a basis for $\mathbb{F}G$, so $\{g +T \:|\: g \in G\}$ spans $\mathbb{F}G/T$.
If $x \sim y$, then $y = gxg^{-1}$ for some $g \in G$.
So 
$$y + T \quad=\quad gxg^{-1}+T \quad=\quad x+ \underbrace{(gxg^{-1} - g^{-1}gx)}_{\in T} + T \quad = \quad x+T$$
So $\{x_1+T,...,x_t+T\}$ spans $\mathbb{F}G/T$.

###### Linear Independence
Suppose 
$$\sum_{i=1}^t \lambda_i(x_i+T) = 0$$
in $\mathbb{F}G/T$ for some $\lambda_i\in \mathbb{F}$. Let $\mathscr{C}_j$ be the conjugacy class of $x_j$, for $1 \leq j \leq t$. Define the linear indicator map:
$$\mathbb{1}_j: \mathbb{F}G \to \mathbb{F}, \qquad \mathbb{1}_j(g) = \begin{cases}
1 & g \in \mathscr{C}_j  \\
0 & \text{otherweise}
\end{cases}$$
Then $\mathbb{1}_j(gh-hg) = \mathbb{1}_j(gh) - \mathbb{1}_j(h^{-1}(hg)h) = \mathbb{1}_j(gh) - \mathbb{1}_j(gh) = 0$ since $\mathbb{1}_j$ is constant on conjugacy classes.
Hence $\mathbb{1}_j(a) = 0$ for all $a \in T$. So we have a well-defined map $\overline{\mathbb{1}_j}: \mathbb{F}G/T \to \mathbb{F}$ given by $\overline{\mathbb{1}_j}(x+T) = \mathbb{1}_j(x)$.
Consequently,
$$0 = \overline{\mathbb{1}}_j\left( \sum_{i=1}^t \lambda_i (x_i +T)\right) = \sum_{i=1}^t\lambda_i \overline{\mathbb{1}}_j(x_i+T) = \lambda_j.$$
That is, $\lambda_j =0$ for all $j$. Hence $\{x_1+T ,...,x_t+T\}$ is linearly independent.
Thus the set is also a basis of $\mathbb{F}G/T$.   $\square$


## Necessary Lemmas

>[!Lemma]
>1. If $a,b \in A$, then $(a+b)^p = a^p + b^p \:(\text{mod } T)$.
>2. If $T^{[p]} = \{a^p \:|\: a \in T\}$. Then $T^{[p]} \subseteq T$
>3. Let $T_p := \{a \in \mathbb{F}G \:|\: a^{p^n} \in T \:\: \exists\: n \geq0\}$. Then $T_p = S$.
##### Proof
###### 1.
By definition $(a+b)^p$ is a sum of $2^p$ terms of the form $a_1a_2...a_p$ where each $a_i \in \{a,b\}$. Now $a_2...a_pa_1 \equiv a_2...a_pa_1 + a_1(a_2...a_p) - (a_2...a_p)a_1 = a_1a_2...a_p\:\: (\text{mod }T)$. Extending the argument shows
$$a_1a_2...a_p + a_2a_3...a_pa_1 + \cdots + a_pa_1...a_{p-1} \equiv p(a_1a_2...a_p)\: (\text{mod }T).$$
This accounts for all other terms $a_1...a_p$ in $(a+b)^p$ for which all the cyclic permutations of $a_1...a_p$ are distinct as words in $a$ and $b$. All terms except $a^p$ and $b^p$.
Hence, $(a+b)^p \equiv a^p + b^p \: (\text{mod }T)$ as claimed.
###### 2.
By part (1), it is enough to show $(ab-ba)^p \in T$,  for  $a,b \in \mathbb{F}G$, since these elements span $T$.
By part (1) again if $a,b \in \mathbb{F}G$, then
$$(ab-ba)^p \equiv (ab)^p + (-ba)^p= (ab)^p-(ba)^p = a(ba...) - (ba...)a \equiv 0\:\: (\text{mod }T)$$
where the second equality follows because $p>0$ (and $-1=1$ in characteristic $2$).
Hence $(ab-ba)^p \in T$. As $T$ is spanned by these elements, the proof is complete.

###### 3.
**Reverse inclusion $(S \subseteq T_p)$:**
By part (2), $T_p = \{a \in \mathbb{F}G \:|\: a^{p^n} \in T \text{ for }n \gg 0\}$.
Therefore if $a,b \in T_p$, then $a^{p^n},b^{p^n} \in T$ for $n \gg 0$. 
Hence, using part (1)
$$(a+b)^{p^n} \equiv (a^p + b^p)^{p^{n-1}} \equiv \cdots \equiv a^{p^n} + b^{p^n} \equiv 0 \:\: (\text{mod }T).$$
Hence, $a+n \in T_p$ by part (2). In particular, $T_p$ is a vector space.
Now $T \subseteq T_p$ by definition, and $R = \text{Rad}\mathbb{F}G \subseteq T_p$ since $R$ is nilpotent.
Therefore, $S = R+T \subseteq T_p$ since $T_p$ is closed under addition.

**Forward inclusion:**
Suppose $a \in \mathbb{F}G$, with $a^{p^n}\in T$ for $n \geq 0$.
Then 
$$(a+R)^{p^n} = a^{p^n}+R \in (T+R)/R = S/R = [\overline{\mathbb{F}G},\overline{\mathbb{F}G}].$$
where the last equality comes from the fact that $S/R = [\overline{A},\overline{A}]$.

Now $\overline{\mathbb{F}G} = \mathbb{F}G/\text{Rad} \mathbb{F}G$ is semisimple, so by [[Artin-Wedderburn Decomp|Artin-Wedderburn]], 
$$\overline{\mathbb{F}G} \cong \bigoplus_{D \in \text{Irr}(\overline{\mathbb{F}G})} \text{Mat}_{d}(\mathcal{O}_D)$$
where $\mathcal{O}_D = \text{End}_{\mathbb{F}G}(D)$ is commutative, and $a_D$ as defined before.
Also 
$$[\overline{\mathbb{F}G},\overline{\mathbb{F}G}] = \bigoplus_{D \in \text{Irr}(\overline{\mathbb{F}G})} \mathfrak{sl}_{d}(\mathcal{O}_D),$$
where $\mathfrak{sl}_D(\mathcal{O}_D) = \{X \in \text{Mat}_{d}(\mathcal{O}_D) \:|\: \text{tr}(X) = 0\}$.
Suppose $\mathbb{F} = \overline{\mathbb{F}}$ is algebraically closed and let $\lambda_1,...,\lambda_d$ be eigenvalues of a matrix $M \in \text{Mat}_d(\overline{\mathbb{F}})$. 
Consider the Jordan canonical form of $M$ and consider $M^k$ for $k >0$:

![[Screenshot 2026-04-23 at 3.27.46 pm.png|600]]
Then, since $\overline{\mathbb{F}}$ is a field of characteristic $p >0$,
$$\text{tr}(M^{p^n}) = \sum_{i=1}^d \lambda_i^{p^n} = \left(\sum_{i=1}^d \lambda_i\right)^{p^n} = (\text{tr}(M))^{p^n}.$$
So $\text{tr}(M^{p^n})= \text{tr}(M)^{p^n}$.

>[!Remark] Remark
>If $\mathbb{F}$ is *not* algebraically closed then this identity still holds because we can embed $\mathbb{F}$ into its algebraic closure.

If $\text{tr}(M)^{p^n}=0$, then $\text{tr}(M) = 0$, so $M^{p^n} \in [\text{Mat}_d(\mathbb{F}),\text{Mat}_d(\mathbb{F})]$ only if $M \in [\text{Mat}_d(\mathbb{F}),\text{Mat}_d(\mathbb{F})]$.
Under Artin-Wedderburn isomorphism, the element $a + R$ can be written as a linear combination of such matrices, so $a + R \in [\overline{\mathbb{F}G},\overline{\mathbb{F}G}]$ since $(a+R)^{p^n} \in [\overline{\mathbb{F}G},\overline{\mathbb{F}G}]$.
That is, $a+ R \in (T+R)/R$, so that $a \in T+R = S$.
Hence $T_p \subseteq S$, which completes the proof. $\square$ 


>[!Lemma]
>1. If $x \sim y$, then $x^k\sim y^k$ for $k \in \mathbb{Z}$
>2. If $g \in G$, then there exists $x,y \in G$ such that $g = xy=yx$ such that $p \nmid |x|$ and $|y| = p^m$ for some $m \geq 0$.
##### Proof 
NEED TO PROVE (pretty easy)

## Proving the Goal

>[!Theorem]
>Let $G$ be a finite group. Then 
>$$\# \text{Irr}(\mathbb{F}G) \leq \# \:p'\text{-conjugacy classes of } G,$$
>with equality if $\mathbb{F}G$ is Schurian.
##### Proof
Since $\# \text{Irr}(\mathbb{F}G) \leq \dim \mathbb{F}G/S$ (with equality of $\mathbb{F}G$ is Schurian), it is enough to prove $\{x_1+S,...,x_s+S\}$ is a basis for $\mathbb{F}G/S$.

Recall $\{x_1,...,x_s\}\subseteq \{x_1,...,x_t\}$ which is a set of conjugacy class reps for $\mathbb{F}G$.
We saw that $\{x_1+T,...,x_t+T\}$ is a basis for $\mathbb{F}G/T$.
Since $T \subseteq S = R+T$, $\{x_1+S,...,x_t+S\}$ spans $\mathbb{F}G/T$.

###### Spanning Set
Now if $g \in G$, then by the lemma above, $g = xy=yx$ where $p \nmid |x|$ and $|y| = p^m$.
Hence $g^{p^m}=(xy)^{p^m}= x^{p^m}y^{p^m}= x^{p^m}$ precisely because $|y|=p^m$.
Then $(g-x)^{p^m}=g^{p^m} -x^{p^m} \:\:(\text{mod }T)=0\:\:(\text{mod }T)$. Hence $(g-x)^{p^m}\in T$, which means $g-x \in T_p = S$. i.e. $g + S = x+ S$ and so $\{x_1+S,...,x_s+S\}$ spans $\mathbb{F}G/S$.

###### Linear Independence
Suppose $\sum_{i=1}^s \lambda_i$
