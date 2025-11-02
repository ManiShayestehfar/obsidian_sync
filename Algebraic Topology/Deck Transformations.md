# Definition

>[!def] 
>Let $p: \widetilde{X} \to X$ be a covering space. The **deck transformations** of this cover, $\text{Homeo}(\widetilde{X},p)$, are the homomorphisms $f:\widetilde{X} \to \widetilde{X}$ such TFDC
>
>![[Screenshot 2025-10-07 at 3.18.18 pm.png|160]]
>i.e. $p \circ f = p$ or i.e. automorphisms of covering spaces

- Deck transformations of a given cover forms a group under composition
- Deck transformations essentially play the role of "shuffling" the covering space.

## Examples

1. Let $p: \mathbb{R} \to S^1$ via $t \mapsto (\cos 2\pi t, \sin 2\pi t)$. Let $T_n:\mathbb{R} \to \mathbb{R}$ be translation by $n \in \mathbb{Z}$ i.e. $T_n(x) = x+n$. Then $p \circ T_n = p$ so $T_n \in \text{Homeo}(S^1,p) \cong \mathbb{Z}$.

2. $p_3:S^1 \to S^1$ via $z \mapsto z^3$ where $S^1 = \{z \in \mathbb{C} \:|\: |z| = 1 \}$. Then $\varphi: S^1 \to S^1$ via $z \mapsto \exp{2\pi i /3}z$ is a deck transformation. Note that $\varphi^3 = \text{id}_{S^1}$. In fact $\text{Homeo}(S^1,p) \cong \mathbb{Z}/3\mathbb{Z}$. 


# Properties

>[!lemma] 
>An element $\tau \in \text{Homeo}(\widetilde{X},p)$ is completely determined by where it sends a single point. 
##### Proof
TFDC: 
![[Screenshot 2025-10-07 at 3.29.19 pm.png|250]]

with the unique lifting property which implies the result directly. $\square$ 


