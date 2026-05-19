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
>2. $\dim S^\perp = \dim M - \dim S$
>3. $(S^\perp)^\perp = S$
>4. If $X,Y$ are submodules of $M$, then $(X+Y)^\perp = X^\perp \cap Y^\perp$
>5. If $X \subseteq Y$ are submodules, then $Y^\perp \subseteq X^\perp$.
##### Proof
###### 1.
Since $\beta$ is linear in the second input, then $S^\perp$ is a vector space if: $m \in S^\perp$ and $g \in G$, then for $s \in S$, $\beta(x,gm) = \beta(g^{-1}s,m)=0$ since $g^{-1}s \in S \implies gm \in S^\perp \implies S^\perp$ is an $\mathbb{F}G$-modules.

###### 2.
Let $\{v_1,...,v_m\}$ is a basis of $M$ such that $\{v_1,...,v_s\}$ is a basis of $S$. 
Then $m \in S^\perp \iff \beta(x,m) = 0$ for all $x \in S$ $\iff \beta(v_i,m)=0$ for $1 \leq i\leq s$.
Set $\phi_i = \beta(b_i,-) \in M^*$ for $1 \leq i \leq m$, then $\{\phi_1,...,\phi_n\}$ is a basis of $M^*$ by the proposition before.
$x \in S^\perp \iff x \in \ker \phi_i$ for $1 \leq i \leq s$.
Hence $\{\Theta^{-1}(\phi_{s+1}),...,\Theta^{-1}(\phi_m)\}$ is a basis of $S^\perp$.
Thus $\dim S^\perp = m-s = \dim M - \dim S$ $\square$

###### 3.
Want $(S^\perp)^\perp = S$.
By definition, $(S^\perp)^\perp = \{m \in M \:|\: \beta(x,m) = 0 \:\:\forall x \in S^\perp\}$.
If $x \in S^\perp$, then $\beta(s,x)=0$ for all $s \in S$.
But since $\beta(x,s)=0$ for all $s \in S$ (since $\beta$ is SNAF), then $S \subseteq (S^\perp)^\perp$.

But $\dim(S^\perp)^\perp = \dim M - \dim S^\perp = \dim M - (\dim M - \dim S) = \dim S$. 
So $(S^\perp)^\perp = S$. $\square$

###### 4.
$(X+Y)^\perp = \{m \in M \:|\: \beta(a,m) = 0 \:\: a \in X+Y\} = \{m \in M \:|\: \beta(x+y,m) = 0 \:\: x \in X,y \in Y\}$
$= \{m \in M \:|\: \beta(x,m) = 0,\:\: \eta(y,m)=0 \:\: x \in X,y \in Y\} = X^\perp \cap Y^\perp$. $\square$

###### 5.
$Y^\perp = \{m \in M \:|\: \beta(y,m) =0 \:\forall y \in Y\}\subseteq X^\perp$ since $X \subseteq Y$.  $\square$



>[!Proposition]
>Suppose $U \subseteq S \subseteq M \cong M^*$ (self-dual). Then 
>$$S/U \cong (U^\perp/S^\perp)^*$$
##### Proof
Define a map $\Theta:S \to (U^\perp/S^\perp)^*$ by $\Theta(x) = \theta_x: U^\perp/S^\perp \to \mathbb{F}$
where $\theta_x(u+S^\perp) = \beta(x,u)$ for all $u \in U^\perp$.

>[!Claim]
>$\Theta$ is a $\mathbb{F}G$-module isomorphism.

###### Well-definedness
$$\begin{align*}
u+S^\perp = y + S^\perp &\implies u-y \in S^\perp \\[3pt]
&\implies \beta(x,u-y) = 0 \qquad (x \in S^\perp) \\[3pt]
&\implies \beta(x,u) = \beta(x,y) \\[3pt]
&\implies \theta_x(u+S^\perp) = \theta_x(y+S^\perp).
\end{align*}$$

###### Linearity
- $\theta_x$ is linear because $\beta$ is linear in the second position implies
$$\theta_s \in (U^\perp/S^\perp)^* = \text{Hom}_\mathbb{F}(U^\perp/S^\perp, \mathbb{F}).$$

- $\Theta$ is linear because $\beta$ is also linear in the first position: $\Theta(gs) = \theta_{gs}$. And
  $\theta_{g\cdot x}(u+ S^\perp) = \beta(g\cdot x,u) = \beta(x,g^{-1}\cdot u) = \theta_s(g^{-1}\cdot x) = g \cdot \theta_x(u+S^\perp)$.

Thus $\Theta$ is an $\mathbb{F}G$-module homomorphism.
###### Kernel
$$\begin{align*}
\ker \Theta &= \{s \in S \:|\: \theta_s=0\}\\[2pt]
&= \{s \in S \:|\: \beta(s,x)=0 \:\:\:\: \forall x \in U^\perp\}\\[2pt]
&= S \cap (U^\perp)^\perp \\[2pt]
&= S \cap U = U
\end{align*}$$
By the first isomorphism theorem,
$$S/U = S/\ker \Theta \cong \text{im }\Theta \subseteq (U^\perp/S^\perp)^$$