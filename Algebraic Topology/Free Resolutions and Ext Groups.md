
# Free Resolutions

>[!def] 
>Given an $R$-module $M$, and abelian group $H$, a **free resolution** is an exact sequence 
>$$\cdots \overset{}{\longrightarrow}F_2 \overset{f_2}{\longrightarrow}F_1 \overset{f_1}{\longrightarrow}F_0 \overset{f_0}{\longrightarrow}H \overset{}{\longrightarrow}0$$
>where each $F_i$ is free.

## Example

1. $H$ is an abelian group, we can always find $F_0,F_1$ free groups such that $$\cdots 0 \overset{}{\longrightarrow}F_1 \overset{}{\longrightarrow}F_0 \overset{}{\longrightarrow}H \overset{}{\longrightarrow}0$$
   is exact with $F_i=0$ for $i \geq 2$.

2. If $H$ is an $R$-module, we can always find a free resolution. 
3. If $R$ a field, then $$0 \overset{}{\longrightarrow}F_0 \overset{}{\longrightarrow}H \overset{}{\longrightarrow}0$$
   is exact.


>[!def]
>Given a free resolution $F$ of an abelian group $H$, get the cochain complex
>$$\cdots \overset{}{\longleftarrow}F_1^* \overset{f_1^*}{\longleftarrow}F_0^* \overset{f_0^*}{\longleftarrow}H^* \overset{}{\longleftarrow}0$$
>ignore the last term $$\cdots \overset{}{\longleftarrow}F_1^* \overset{g_1^*}{\longleftarrow}F_0^* \overset{g_0^*}{\longleftarrow}0.$$
>The **Ext groups** are given by $\text{Ext}_\mathbb{Z}^n(H;G):= \ker g_{n+1}^*/\text{im }g_n^*$


>[!lemma] H Lemma 3.1
>Given free resolution $(F,H)$, $(F',H')$
>1. Every homomorphism $\alpha: H\to H'$ can be extended to a chain map
>   ![[Free Resolutions and Ext Groups-1761694727384.png|430]]
>2. Any two such chain maps are homotopic.
>3. $\text{Ext}_R^n(H;G, F) \cong \text{Ext}_R^n(H';G,F')$

- From (3) we know that $\text{Ext}$ groups are well-defined
- Call $\text{Ext}_R^1(H;G) = \text{Ext}(H;G)$ for $H$ an abelian group.

## Examples 

1. $\text{Ext}_R^0(A,B)\cong \text{Hom}_R(A,B)$ for $A,B$ being $R$-modules.

2. $\text{Ext}_R^i(A,B) =0$ for $i > 0$ if $A$ is a free $R$-module.

3. $\text{Ext}_\mathbb{Z}^i (A,B) = 0$ for all $i > 2$ if $A,B$ are abelian groups.

## Properties

1. $\text{Ext}(H \oplus H' ; G) \cong \text{Ext}(H;G) \oplus \text{Ext}(H';G)$ 
2. $\text{Ext}(H;G) = 0$ if $H$ is free
3. $\text{Ext}(\mathbb{Z}/n\mathbb{Z};G) \cong G / nG$
4. $\text{Ext}(H;\mathbb{Z})\cong T_H$ where $T_H$ is the torsion subgroup of $H$

## Universal Coefficient Theorem

>[!Theorem] H Theorem 3.2 - Universal Coefficient Theorem
>Let $C$ be a chain complex of free abelian group with homology $H_n(C)$. 
>Then, the cohomology groups $H^n(C;G)$ coming from the cochain complex $\text{Hom}(-,G)$ are determined by split exact sequences $$ 0 \overset{}{\longrightarrow}\text{Ext}(H_{n-1}(C);G)\overset{}{\longrightarrow}H^n(C;G) \overset{}{\longrightarrow}\text{Hom}(H_n(C); G)\overset{}{\longrightarrow}0$$

**Note:** This sequence comes from the short exact sequence $$0 \overset{}{\longrightarrow}\text{im }\partial_{n-1}\overset{}{\longrightarrow}\ker \partial_n \overset{}{\longrightarrow}H_n(C) \overset{}{\longrightarrow}0$$where both $\text{im }\partial_{n-1}$ and $\ker \partial_n$ are both free abelian (since they come from $C_n$ which is free abelian)

>[!corollary] H Corollary 3.3
>Suppose $H_n(C)$ and $H_{n-1}(C)$ are finitely generated. Then $H^n(C;\mathbb{Z})\cong \underbrace{H_n(C)}_{=T_n} \oplus T_{n-1}$
>where $T_n \subseteq H_{n-1}(C), T_n\subseteq H_n(C)$

**Naturality:** $\alpha: C \to C'$ chain map, get the following commutative diagram: 
![[Free Resolutions and Ext Groups-1761695007031.png|600]]

**Note:** The splitting $p$ is not natural as it depends on the choice of $p: C_n \to \ker \partial_n$ 

>[!corollary] H Corollary 3.4
>If a chain map between chain complexes of free abelian groups induces an isomorphism on the homology groups, then it induces an isomorphism on the cohomology groups. 
>$\alpha:C \to C'$, and $\alpha_*:H_n(C)\overset{\sim}{\longrightarrow}H_n(C')$
>Then $\alpha^* : H^n(C')\overset{\sim}{\longrightarrow} H^n(C)$


