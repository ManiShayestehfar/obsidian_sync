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
>1. *non-degeneracy:* If $x \neq 0$, then $\beta(x,x') \neq 0 \neq \beta(x'',x)$ for some $x',x'' \in M$
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
- $\beta$ is non-degenerate if $\beta(x,x') \neq 0 \neq \beta(x'',x)$.
  If $x \neq 0$, then $\theta_x\neq0$ as $\Theta$ is an isomorphism.
  Then $\beta(x,y) = \theta_x(y) \neq 0$ for some $y$.
  
  On the other hand, we can find a basis of $M$ of the form $\{x,v_2,...,v_n\}$.
  Let $\{\phi_1,...,\phi_n\}$ be the dual basis. So $\phi_1(x) \neq 0$.
  Let $x'' = \Theta^{-1}(\phi_1) \implies \beta(x'',x) = \phi_1(x)\neq 0$.
  Hence $\beta$ is non-degenerate.
  
- $\beta$ is associative since $\Theta$ is a $\mathbb{F}G$-module homomorphism. So $\Theta(gx) = g\Theta(x)\implies \theta_{gx} = g \theta_x \implies \theta_{gx}(m) = (g\theta_x)(m) = \theta_x(g^{-1}m)$.
  So $\beta(gx,m) = \theta_{gx}(m) = \theta_x(g^{-1}m) = \beta(x,g^{-1}m)$.
  
  Clearly $\beta$ is linear in the first input because $\Theta$ is linear and, is linear in the second input because $\theta_x$ is linear. $\square$


Conversely, suppose $\beta:M \times M \to \mathbb{F}$ is a NAF. Define $\Theta: M \to M^*$ via $x \mapsto \theta_x$ where $\theta_x \in M^*$ is given by $\theta_x(y) = \beta(x,y)$.
Reversing the steps from the NAF proof above shows that $\Theta$ is an isomorphism.
$\square$


## SNAF

>[!Definition] 
>A **Symmetric NAF (SNAF)** is a NAF $\beta: M \times m \to \mathbb{F}$ such that $\beta(x,y) = \beta(y,x)$ for all $x,y \in M$.
>

Let $S$ be an $\mathbb{F}G$-submodule of $M$, which has a SNAF.
Define $S^\perp = \{m \in M \:|\: \beta(s,m) = 0 \:\:\:\forall s \in S\}$.
 
>[!Proposition]
>Let $S$ be a submodule of $M$.
>1. $S^\perp$ is an $\mathbb{F}G$-module
>2. $\dim S^\perp = \dim M = \dim S$
>3. $(S^\perp)^\perp = S$
>4. If $X,Y$ are submodules of $M$, then $(X+Y)^\perp = X^\perp \cap Y^\perp$
>5. If $X \subseteq Y$ are submodules, then $Y^\perp \subseteq X^\perp$.
##### Proof
###### 1.
Since $\beta$ is linear in the second input, then $S^\perp$ is a vector space if: $m \in S^\perp$ and $g \in G$, then for $s \in S$