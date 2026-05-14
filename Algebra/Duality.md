# Definition

>[!Definition]
>Assume $\mathbb{F}$ is an arbitrary field, $A$ an $\mathbb{F}$-algebra, and $M$ an $A$-module.
>The **dual** of $M$ is
>$$M^* = \text{Hom}_\mathbb{F}(M,F) = \{\varphi: M \to \mathbb{F}\::\: \varphi\text{ linear}\}$$

# Properties

>[!Claim]
>$M^*$ is an $\mathbb{F}G$-module via:
> if $\varphi \in M^*$ and $g \in G$, then $g\varphi \in M^*$ is the map $(g\varphi)(m) = \varphi(g^{-1}m)$ for $m \in M$.
##### Proof

**Unital:** $(1_G \varphi)(m) = \varphi(1_Gm) = \varphi(m)$

**Associativity:** if $g,h \in G$, then $((gh)\varphi)(m) = \varphi((gh)^{-1}m)= \varphi(h^{-1}g^{-1}m)= (h\varphi)(g^{-1}m)= (g(h\varphi))(m)$ 

**Linearity:** $g\varphi = \varphi \mathbf{g}^{-1}$ is a composition of linear maps which is linear. $\square$

>[!Claim]
>$$\dim M^* = \dim M$$
##### Proof
Let $\{v_1,...,v_n\}$ be a basis of $M$.
Define $\phi_i:M \to \mathbb{F}$ by $\phi_i(v_j) = \delta_{ij}$.
i.e. $\phi_i \left( \sum_{j=1}^n \lambda_i v_j \right)= \lambda_i$ 
so $\{\phi_1,...,\phi_n\}$ is a basis for $M^*$.
$\square$

>[!Warning] Remark
>If $\mathbb{F}= \mathbb{C}$, then from W10 Tutorial, we saw that $\chi_{M^*} = \overline{\chi_M}$.
>Hence $M \cong M^* \iff \chi_M(g) \in \mathbb{R}$  $\forall g \in G$.

# Self-Dual

>[!Definition]
>$M$ is **self-dual** if $M \cong M^*$ as $\mathbb{F}G$-modules

## Example

1. For $S_n$, $\chi(h) = \overline{\chi(g)} \in \mathbb{R}$. So irreducible $\mathbb{C}S_n$-modules are self-dual.
   *This suggests that self duality is necessary for irreducible $\mathbb{F}S_n$-modules.*

 

## NAF

>[!Definition]
>A **non-degenerate associative bilinear form (NAF)** on $M$ is a map $\beta: M \times M \to \mathbb{F}$ such that 
>1. *non-degeneracy:* If $x \neq 0$, then $\beta(x,';) \neq 0 \neq \beta(x,x'')$ for some $x',x'' \in M$
>2. *associativity:* $\beta(gx,y) = \beta(x,g^{-1}y)$ for some $g \in G$ and $x,y \in M$
>3. *bilinearity:* $\beta$ is linear in both inputs

## Finding Self-Dual 

>[!Proposition]
>$$M \cong M^* \iff M \text{ has a NAF}$$
##### Proof
Suppose $M \cong M^*$ and fix an isomorphism $\Theta: M \to M^* = \text{Hom}_\mathbb{F}(M,\mathbb{F})$.
If $x \in M$, let $\theta_x = \Theta(x) \in M^*$.
Define $\beta: M \times M: \to \mathbb{F}$ by $\beta(x,y)= \theta_x(y) \in \mathbb{F}$.

>[!Claim]
>$\beta$ is NAF.
###### Proof
$\beta$ is non-degenerate if $\beta(x,x') \neq -0 \neq \beta(x'',x)$