>[!Definition]
>Assume $\mathbb{F}$ is an arbitrary field, $A$ an $\mathbb{F}$-algebra, and $M$ an $A$-module.
>The **dual** of $M$ is
>$$M^* = \text{Hom}_\mathbb{F}(M,F) = \{\varphi: M \to \mathbb{F}\::\: \varphi\text{ linear}\}$$

>[!Claim]
>$M^*$ is an $\mathbb{F}G$-module via:
> if $\varphi \in M^*$ and $g \in G$, then $g\varphi \in M^*$ is the map $(g\varphi)(m) = \varphi(g^{-1}m)$ for $m \in M$.
##### Proof

**Unital:** $(1_G \varphi)(m) = \varphi(1_Gm) = \varphi(m)$

**Associativity:** if $g,h \in G$, then $((gh)\varphi)(m) = \varphi((gh)^{-1}m)= \varphi(h^{-1}g^{-1}m)= (h\varphi)()$ 