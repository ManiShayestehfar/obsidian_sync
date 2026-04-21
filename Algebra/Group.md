>[!def]
>A **group** is an ordered pair $(G, \ast)$ where:
>
>1. **Closure:** For every $a, b \in G$, the result of the operation $a \ast b$ is also in $G$.
>2. **Associativity:** For every $a, b, c \in G$,
   >$$
   (a \ast b) \ast c = a \ast (b \ast c)$$
>3. **Identity Element:** There exists an element $e \in G$ (called the identity) such that for every $a \in G$,
 >$$
   e \ast a = a \ast e = a.
   >$$
>4. **Inverse Element:** For every $a \in G$, there exists an element $a^{-1} \in G$ such that $$
   a \ast a^{-1} = a^{-1} \ast a = e.
   $$
   
- If the operation $\ast$ is **commutative** (i.e., $a \ast b = b \ast a$ for all $a, b \in G$), then the group is called an **abelian group**.

## Normal Subgroup

A **Normal Subgroup** $H \leq G$ is defined if $gH = Hg$ for all $g \in G$. We write $H \trianglelefteq G$.  

### Simple Group

A group $G$ is **simple** if it has no proper normal subgroups

# Order

>[!Definition]
>For $g \in G$, the **order** of $g$, 
>$$|g|:= \min\{m \geq 0 \:|\: g^m = 1_G\}$$

- For $x \sim y$  $(y = gxg^{-1}) \implies |x|=|y|$.

## Lagrange's Theorem

>[!Theorem]
> Let $G$ be a finite group and suppose $H$ is a subgroup of $G$. Then $|H| \:|\: |G|$.
> 



# Conjugacy

## Conjugate Group Elements

>[!Def]
>Two elements $x,y \in G$ are **conjugate** if $x = gyg^{-1}$ for some $g \in G$.

- Conjugacy is an equivalence relation, written as $x \sim y$.

## Conjugacy Class

>[!Def]
>If $x \in G$, then $\mathscr{C}_x = \{gxg^{-1} \:|\: g \in G\} = \{y \in G \:|\: x \sim y\}$ is the **conjugacy class** of $x \in G$.
>

So
$$G = \bigsqcup_{\substack{x \text{ conj.} \\ \text{class reps}}} \mathscr{C}_g \tag{Disjoint union}$$
where $x \sim y \iff \mathscr{C}_x = \mathscr{C}_y$.

### Examples

1. $G$ any group. Then $\mathscr{C}_{1_G} = \{g \cdot 1_G\cdot g^{-1}\:|\: g \in G\} = \{1_G\}$
2. $G$ any abelian group, and $x \in G$, then $\{gxg^{-1}\:|\: g \in G\} = \{x\}$
3. $G=S_3$, then the conjugacy classes are 
$$\{1\}, \{(12),(13),(23)\}, \{(123),(321)\}$$
	- *Note:* $\text{Irr}(\mathbb{C}S_3)=\{1_G,\varepsilon_g, W \cong \mathbb{F}_3\}$

### Notation

For $x\in G$, $\overline{x}= \sum_{y \in \mathscr{C}_x}y = \sum_{x \sim y}y = \left(\sum_{g \in G} gxg^{-1}\right)$ where the last sum is unnecessarily huge

### Propositions

>[!Proposition]
>Let $\mathscr{C}_1,...,\mathscr{C}_{x_t}$ be conjugacy classes of $G$.
>Then $\{\overline{x_i}\:|\: 1 \leq i \leq t\}$ is a basis for $Z(\mathbb{F}G)$

