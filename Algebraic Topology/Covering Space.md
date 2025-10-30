# Covering Space

>[!def] 
>A **covering space** of $X$ is a space $\widetilde{X}$ together with a continuous map $p: \widetilde{X} \to X$ such that 
>1. $\exists$ open cover $\{U_\alpha\}$ of $X$ such that
>2. $\forall \alpha,\:\:p^{-1}(U_\alpha)$ is a disjoint union of open sets in $\widetilde{X}$, each homeomorphically mapped onto $U_\alpha$ by $p$.
>   
>   ![[Covering Space-1759723390379.png|170]]
>   

## Examples

1. $X=S^1,\widetilde{X} =\mathbb{R}$, $p=\mathbb{R} \to S^1$ by $t \mapsto (\cos 2\pi t,\:\sin 2\pi t)$.

![[Covering Space-1759723584644.png|200]]

Take $\{U_\alpha\}$ the smallest collection of open arcs in $S^1$ that cover $S^1$. Then $p^{-1}(U_\alpha)$ is a disjoint union of collection of open intervals in $\mathbb{R}$, with restriction of $p$ to each such interval being a homeomorphism to $U_\alpha$.

2. $X=S^1$, $\widetilde{X} = S^1$ both $\{z \in \mathbb{C}\:|\: |z| = 1\}$. Define $p_n: \widetilde{X}\to X$ by $z \mapsto z^n$ i.e. $p_n(e^{i\theta}) = e^{in\theta}$. i.e. $p_n$ wraps $S^1$ around itself $n$-times. 
   ![[Covering Space-1759726596906.png|300]]
3. $X = S^1 \vee S^1$ 
   ![[Covering Space-1759726695434.png|400]]
    are all covering spaces of $X$. And so is this infinite Cayley graph of $F(a,b)$ 
   ![[Covering Space-1759726810707.png|200]]


# Lifting Properties

>[!def] Lift
>$p: \widetilde{X} \to X$ a cover of $X.$ Let $f:Y \to X$ be a continuous map. A **lift** of $f$ is a continuous map $\widetilde{f}: Y \to \widetilde{X}$ such that $p \circ \widetilde{f}= f$. i.e. TFDC
>![[Covering Space-1759736222346.png|160]]
>

>[!proposition]
>$p$ a covering map. Let $F: Y \times I \to X$ be a homotopy with $F(y,t) = f_t(y).$ 
>Then for every lift $\widetilde{f}_0$ of $f_0$ there exists a <span style="color:rgb(146, 208, 80)">unique</span> homotopy $\widetilde{F}: Y \times I \to \widetilde{X}$ such that $\widetilde{F}(y,t)=\widetilde{f}_t(y)$ a lift of $f_t$.
>
##### Proof
Note that $F|_{Y \times \{0\}} = f_0(y)$.
*we show:* There is a unique continuous $\widetilde{F}$ such that $F|_{Y \times \{0\}} = f_0(y)$, and $\widetilde{F}$ lifts $F$. i.e.
![[Covering Space-1759737524546.png|200]]
commutes.

Let $\{U_\alpha\}$ be an open cover of $X$ such that $p^{-1}(U_\alpha)$ is a disjoint union of open subsets of $\widetilde{X}$, each mapped homeomorphically onto $U_\alpha$ by $p$ for each $\alpha.$ 

For each $(y,t) \in Y \times I$, $F(y,t)\in U_\alpha$ for some $\alpha$, so $(y,t) \in F^{-1}(U_\alpha)$. Since $F$ is continuous, $F^{-1}(U_\alpha)$ is open so there exists an open rectangle $N_{y,t} \times V_{y,t} \subseteq F^{-1}(U_\alpha)$ containing $(y,t)$, and thus $F(N_{y,t} \times V_{y,t})\subseteq U_\alpha$. WLoG assume $F(N_{y,t} \times \overline{V}_{y,t})\subseteq U_\alpha$ as well.

Fix $y_0 \in Y$. Then $\{y_0\}\times I$ is compact, so finitely many of $N_{y,t}\times V_{y,t}$ cover $\{y_0\}\times I$. 

We can show that there exists a neighbourhood of $y_0$ in $Y$ and a partition $0=t_0<t_1<...<t_{m-1}<t_m =1$ of $I$ such that for $0 \leq i \leq m$, there exists $U_i = U_{\alpha_i}$ such that $F(N \times [t_i,t_{i+1}]) \subseteq U_i$.  We can induct on $i$ to construct $\widetilde{F}$ on $N \times I$.

*Base case:* $i=0$, put $\widetilde{F}|_{N \times \{0\}} = \widetilde{f}_0|_N$.
*Inductive assumption:* Assume we have constructed $\widetilde{F}$ on $N \times [0,t_i]$. Now there exists an open $\widetilde{U}_i \subseteq \widetilde{X}$ such that $p|_{\widetilde{U}_i}$ is a homeomorphism onto $U_i$, and $\widetilde{U}_i$ contains $\widetilde{F}(y_0,t_i)$. We may assume $\widetilde{U}_i$ contains $\widetilde{F}(N \times \{t_i\})$.

Now define $\widetilde{F}|_{N\times [t_i,t_{i+1}]} = (p|_{U_i})^{-1} \circ F|_{N \times [t_i,t_{i+1}]}$. Then TFDC:

![[Covering Space-1759739264000.png|400]]

After finitely many repetitions, get lift $\widetilde{F}: N \times I\to \widetilde{X}$ for some neighbourhood of $y$.


*Uniqueness:* First consider <span style="color:rgb(0, 176, 240)">the special case</span> $Y = \{y_0\}$. i.e. $F:\{y_0\}\times I \to X$. Suppressing $Y$ from notation, then $F:I \to X$ is a path in $X$.

Suppose $\widetilde{F}:I \to \widetilde{X}$, $\widetilde{F}':I \to \widetilde{X}$ are lifts of $F:I \to X$ such that $\widetilde{F}(0) = \widetilde{F}'(0)$. Consider partition $0=t_0<t_1<...<t_m = 1$ such that for all $0\leq i\leq m$, $F([t_i,t_{i+1}])\subseteq U_i$. 
Assume inductively that $\widetilde{F}=\widetilde{F}'$ on $[0,t_i]$. Since $[t_i,t_{i+1}]$ is connected and $\widetilde{F},\widetilde{F}'$ are continuous and $\widetilde{F}([t_i,t_{i+1}])$ and $\widetilde{F}'([t_i,t_{i+1}])$ are each contained in a single open set from the disjoint union $p^{-1}(U_i)$ (same one for both because $\widetilde{F}(t_i) = \widetilde{F}'(t_i)$). Call this open set $\widetilde{U}_i$.

Now $p$ is injective on $\widetilde{U}_i$ and $p \circ \widetilde{F} = p \circ \widetilde{F}'$ on $I$, so we get $\widetilde{F}=\widetilde{F}'$ on $[t_i,t_{i+1}]$. So if $Y=\{y_0\}$, then for all lifts $\widetilde{f}_0$ of $f_0$ there exists a unique $\widetilde{F}$ for any $F$.

<span style="color:rgb(0, 176, 240)">For general y:</span> 
$\forall y \in Y$, $\widetilde{F}|_{N_y \times I}$ is unique when restricted further to $\{y\}\times I$. So $\widetilde{F}|_{N_y\times I}$ and $\widetilde{F}'|_{N'_y\times I}$ agree on $(N'_y \cap N_y)\times I$. So we get a unique lift $\widetilde{F}$ to all of $Y \times I$. $\widetilde{F}$ is continuous because it is continuous on each $N_y\times I$ by the [[Pasting Lemma]].  $\square$


# Path-lifting Property

>[!cor] 
>Let $p$ be a covering map. 
>1. **path-lifting property:** For every path $g: I \to X$ and each lift $\tilde{x}_0 \in \widetilde{X}$ of $x_0 = g(0)$, there is a *unique* path $\widetilde{g}:I \to \widetilde{X}$ that lifts $g$ such that $\widetilde{g}(0)=\tilde{x}_0$.
>2. If $f_t:I \to X$ is a homotopy of paths, then for every lift $\tilde{f}_0$ of $f_0$, there is a *unique* homotopy of paths $f_t:I\to X$ such that $\widetilde{f}_t$ lifts $f_t$.

##### Proof 
###### Part 1
Set $Y = \{y_0\}$. For $t \in I$, define $f_t:Y \to X$, $y_0\mapsto g(t)$. Then $f_t$ is continuous and $F:\{y_0\}\times I \to X$ given by $(y_0,t)\mapsto f_t(y_0)$ is continuous so $F$ is a homotopy. 
Define $\widetilde{f}_0:\{y_0\}\to X$ by $\widetilde{f}_0(y_0)= x_0$. Then $\widetilde{f}_0$ is a lift of $f_0$. We therefore know that there exists a unique lifted homotopy $\widetilde{f}_t$ such that each $\widetilde{f}_t$ lifts $f_t$.

![[Covering Space-1759747750900.png|250]]

Define $\widetilde{g}:I \to \widetilde{X}$ by $\widetilde{g}(t)=\widetilde{f}_t(y_0)$. Then $\widetilde{g}$ is a path and $\widetilde{g}$ lifts $g$, and $\widetilde{g}(0)=\widetilde{x}_0$, unique by uniqueness of $\widetilde{f}_t$.

###### Part 2
Same as above but we replace $Y$ with $I$.


# Covering Spaces & Fundamental Groups

>[!proposition] 
>Let $p:(\widetilde{X},\widetilde{x}_0) \to (X,x_0)$ be a covering map. Then the induced homomorphism $p_*: \pi_1(\widetilde{X},\widetilde{x}_0) \to \pi_1(X,x_0)$ is *injective*.
>
>Also the image $p_*(\pi_1 (\widetilde{X},\widetilde{x}_0)) \trianglelefteq \pi_1 (X,x_0)$ consists of homotopy classes of loops based at $x_0$ in $X$ whose lifts to $\widetilde{X}$ starting at $\widetilde{x}_0$ are loops in $\widetilde{X}$.
##### Proof
*injectivity:* Let $[\widetilde{f}_0] \in \ker p_*$ which we want to show is trivial.
Let $f_0 = p \circ \widetilde{f}_0$. Then $p_*([\widetilde{f}_0]) = [p \circ \widetilde{f}_0] = [f_0]= 1_{\pi_1(X,x_0)}$ where the last equality comes from the kernel assumption.

So we have a homotopy $f_t:I \to X$ from $f_0$ to the constant loop at $x_0$, say $f_1$. By the corollary above (part 2), there exists a unique lift $\widetilde{f}_t$ of $f_t$ such that $f_1$ is the constant loop at $\widetilde{x}_0$. So $\widetilde{f}_0$ is nullhomotopic in $\widetilde{X}$. i.e. $[\widetilde{f}_0] = 1_{\pi_1(\widetilde{X},\widetilde{x}_0)}$. $\therefore\:p_*$ is injective.

<mark style="background: #FF5582A6;">PROOF OF THE REST.</mark>  $\square$ 


## Examples

1. $p_3:S^1\to S^1$, $z \mapsto z^3$ induces $(p_3)_*: \mathbb{Z}\to \mathbb{Z}$, $k \mapsto 3k$ so the image is $3\mathbb{Z}\trianglelefteq\mathbb{Z}.$ 
2. $p:\mathbb{R} \to S^1$, $t \mapsto (\cos 2\pi t, \sin 2\pi t)$, so image of $p_*$ is the trivial subgroup.
3. $\pi_1(\mathbb{R}P^2) \cong \mathbb{Z}/2\mathbb{Z}$. We know $\pi_1 (T^2)\cong \mathbb{Z}^2$. Any $p: \mathbb{R}P^2 \to T^2$ covering would induce an injective homomorphism, but non exist (same for the other direction), so no coverings here.


# Number of Sheets

>[!lemma]
>If $p$ is a covering and $X$ is *connected*, then the preimage $p^{-1}(x)$ for $x \in X$, has the same cardinality.

>[!def] Number of Sheets 
>For $X$ connected, and $p:\widetilde{X}\to X$ a cover, the cardinality of $p^{-1}(x)$ for some $x \in X$ is the **number of sheets** of the cover.

## Examples

1. $p_3:S^1 \to S^1$, $z \mapsto z^3$ is 3-sheeted
2. $p:\mathbb{R}\to S^1$, $t \mapsto (\cos 2\pi t, \sin 2\pi t)$ has infinitely many sheets.
   
3. ![[Covering Space-1759749357895.png|350]]


## Propositions

>[!proposition]
>Suppose $p:(\widetilde{X},\widetilde{x}_0) \to (X,x_0)$ is a cover, and $X, \widetilde{X}$ are path-connected. Then the $\#$ of sheets of this cover = index of $p_*(\pi_1(\widetilde{X},\widetilde{x}_0))$ in $\pi_1(X,x_0)$.
##### Proof
For the following proof assume $G = \pi_1(X,x_0)$, and $H = p_*(\pi_1(\widetilde{X},\widetilde{x}_0))$.
Let $[g]\in G$ with lift $\widetilde{g}:I \to \widetilde{X}$ starting at $\widetilde{x}_0$. Let $[h]\in H$. Then the lift $\widetilde{h}$ of $h$ starting at $\widetilde{x}_0$ is a loop at $\widetilde{x}_0$. So the composition of paths $\widetilde{h} \cdot \widetilde{g}$ in $\widetilde{X}$ ends at the same points as $\widetilde{g}$ does.

![[Screenshot 2025-10-07 at 10.00.15 am.png|400]]

Define $\Phi: Hg \to p^{-1}(x)$ via $H[g] \mapsto \widetilde{g}(1)$. We show that $\Phi$ is bijective. 

*Surjective:* $\widetilde{X}$ path-connected. So can join $\widetilde{x}_0$ to any element of $p^{-1}(x_0)$ via a path $\tilde{g}$. Then $p \circ \widetilde{g}$  is a loop $g$ in $X$ at $x_0$. Then $\Phi(H[g]) = \widetilde{g}(1)$.   $\therefore \Phi$ is surjective. 

*Injective:* Suppose $\Phi(H[g_1]) = \Phi(H[g_2]) \implies \widetilde{g}_1(1) = \widetilde{g}_2(1)$, so $\widetilde{g}_1 \cdot \bar{\tilde{g_2}}$ is a loop in $\widetilde{X}$ based at $\widetilde{x}_0$. 
Then $g_1 \cdot \bar{g}_2$ is a loop in $X$ based at $x_0$. Hence $[g_1 \cdot \bar{g}_2]$ is a loop in $X$ based at $x_0$. Hence $[g_1 \cdot \bar{g}_2]$ is in the image of $p_*$, i.e. $[g_1 \cdot \bar{g}_2] = [g_1][g_2]^{-1} \in H$ $\implies H[g_1] = H[g_2]$.  $\square$ 



]# Lifting Criterion

>[!proposition]
>Suppose we have a cover $p:(\widetilde{X},\widetilde{x}_0) \to (X,x_0)$ and a continuous map $f:(Y,y_0)\to (X,x_0)$. If $Y$ is *path-connected* and *locally path-connected*, then a lift
> $$\widetilde{f}:(Y,y_0)\to (\widetilde{X},\widetilde{x}_0)\:\:\text{exists}\iff f_*(\pi_1(Y,y_0))\subseteq p_*(\pi_1(\widetilde{X}, \widetilde{x}_0))$$
##### Proof

 ==DO THE PROOF (SEE HATCHER PROP 1.33)==


# Unique Lifting Property

>[!proposition] 
>$p:(\widetilde{X},\widetilde{x}_0) \to (X,x_0)$ a covering space, and let $f:(Y,y_0)\to (X,x_0)$ be a continuous map with lifts $\widetilde{f}_1, \widetilde{f}_2: (Y,y_0)\to (\widetilde{X}, \widetilde{x}_0)$. 
>Suppose $Y$ is connected. Then $\widetilde{f}_1(y_0) = \widetilde{f}_2(y_0) \implies \widetilde{f}_1 = \widetilde{f}_2$.
>

##### Proof

 ==DO THE PROOF (SEE HATCHER PROP 1.34)==


# Isomorphism of Covering Spaces

>[!def] 
>An **isomorphism of covering spaces**, $p_1:\widetilde{X}_1\ \to X, p_2:\widetilde{X}_2 \to X$  is a homomorphism $f:\widetilde{X}_1 \to \widetilde{X}_2$ such that TFDC:
>
> ![[Screenshot 2025-10-07 at 2.05.50 pm.png|150]]

## Examples

1. $\widetilde{X}_1 = \widetilde{X}_2 = \mathbb{R}$, $X=S^1$.
   Then define $p:\mathbb{R} \to S^1$, $q:\mathbb{R} \to S^1$, $f:\mathbb{R} \to S^1$ given by $p(t)= \exp(2\pi i t), q(t)=\exp(it),$ and $f(t) = 2\pi t$ respectively. Then $p,q$ are covers and $f$ is a homeomorphism.

2. Isomorphism of covers gives an equiv. relation on covers of a space $X$. These can be considered as *basepoint-preserving* isomorphisms i.e.
   ![[Screenshot 2025-10-07 at 2.09.17 pm.png|300]]
   
## Propositions

>[!proposition]
>$X$ is *path-connected* and *locally path-connected*, then two path-connected covering spaces $p_1,p_2$ are isomorphic via an isomorphism $f:\widetilde{X}_1 \to \widetilde{X}_2$ taking a basepoint $\widetilde{x}_1 \in p^{-1}(x_0)$ to a basepoint $\widetilde{x}_2 \in p_2^{-1}(x_0) \iff p_{1*}(\pi_1(\widetilde{X}_1,\widetilde{x}_1)) = p_{2*}(\pi_1(\widetilde{X}_2,\widetilde{x}_2))$
##### Proof
###### $(\Rightarrow)$ 
Assume $f:(\widetilde{X}_1, \widetilde{x}_1) \to (\widetilde{X}_2, \widetilde{x}_2)$ an isomorphism. Since $f$ is a homeomorphism, both $f_*$ and $(f^{-1})_*$ are isomorphisms. Then 
![[Screenshot 2025-10-07 at 2.21.01 pm.png|270]]

commutes. i.e. $p_1 = p_2 \circ f$ and $p_2 = p_1 \circ f$.

This implies $(p_1)_* = (p_2)_* \circ f$ and $(p_2)_* = (p_1)_* \circ f$. Hence $(p_1)_*$ and $(p_2)_*$ have the same image in $\pi_1(X,x_0)$.

###### $(\Leftarrow)$ 
Consider 
![[Screenshot 2025-10-07 at 2.26.42 pm.png|230]]

By lifting criterion, since $(p_1)_*(\pi_1(\widetilde{X}_1,\widetilde{x}_1))\subseteq (p_2)_*(\pi_1(\widetilde{X}_2,\widetilde{x}_2))$, then there is a lift $\widetilde{p}_1$ of $p_1$ such that $\text{Fig 1.}$ of below commutes.

![[Screenshot 2025-10-07 at 2.37.51 pm.png]]

Similarly for $\widetilde{p}_2$ a lift of $p_2$ $\text{Fig 2.}$ commutes. So we have lifts given by $\text{Fig 3.}$ 

Since $\widetilde{p}_2 \circ \widetilde{p}_1$ fixes $\widetilde{x}_1$, and so does the $\text{id}$, by the unique lifting property, we get $\widetilde{p}_2 \circ \widetilde{p}_1 = \text{id}_{\widetilde{X}_1}.$ Analogously $\widetilde{p}_1 \circ \widetilde{p}_2 = \text{id}_{\widetilde{X}_2}.$ Thus $\widetilde{p}_1,\widetilde{p}_2$ are inverse homomorphisms, so these covers are isomorphic. $\square$

# Covering Space & Subgroups Correspondence

>[!thm]
>Let $X$ be *path-connected*, *locally path-connected*, *semi-locally simply-connected*. 
>Then there is a bijection $$\begin{Bmatrix}
> \text{Base-point preserving} \\ \text{isomorphism classes} \\ \text{of path-connected}  \\ \text{covering spaces} 
>\end{Bmatrix} \longleftrightarrow \begin{Bmatrix} \text{subgroups}  \\ \text{of}\:\: \pi_1(X,x_0) \end{Bmatrix}$$
>given by $(p:(\widetilde{X},\widetilde{x}_0) \to (X,x_0)) \mapsto p_*(\pi_1(\widetilde{X},\widetilde{x}_0))$.
>If we ignore base points of covers, we get a bijection $$\begin{Bmatrix}
> \text{Isomom. classes of } \\ \text{path-connected} \\ \text{covering spaces}  
>\end{Bmatrix} \longleftrightarrow \begin{Bmatrix} \text{Conjugacy classes} \\ \text{of subgroups}  \\ \text{of}\:\: \pi_1(X,x_0) \end{Bmatrix}$$
>

**Recall:** *Conjugacy classes* of $g \in G$ is the subset $\{hgh^{-1}\:|\: h \in G\}$ of $G$.


# Universal Cover

>[!def] 
>A simply connected covering space of $X$ is a **universal cover**.

## Examples 

1. $p: \mathbb{R} \to S^1$, via $t \mapsto \exp{2\pi i t}$  is a universal cover.
2. An infinite tree cover of $S^1 \vee S^1$ is a universal cover.


## Existence of Universal Cover

>[!thm] 
>$X$ is *path-connected*, *locally path-connected*, and *semi-locally simply connected*. Then there exists a simply-connected cover $\widetilde{p}: \widetilde{X} \to X$ i.e. a universal cover
##### Proof

==DO THIS PROOF (pg. 35-37)==



# Normal/Regular Covering Space

>[!def] 
>$p:\widetilde{X} \to X$ a covering space is **normal/regular** if $\forall x \in X$, $\forall \tilde{x}_1,\tilde{x}_2 \in p^{-1}(X)$, there exists $\varphi \in \text{Homeo}(\widetilde{X},p)$ such that $\varphi(\tilde{x}_1) = \tilde{x}_2$. 
>i.e. the group of deck transformations acts *transitively* on each *fibre* of $p$.
- *transitive:* group action $\rho: G \to \text{Sym}(X)$: $\forall x,y \in X$  $\exists g \in G$ such that $\rho(g)(x)=y$.
- *fibre:* preimage of a point.

## Examples

1. $p: \mathbb{R} \to S^1$, $t \mapsto (\cos 2\pi t, \sin 2\pi t)$ is normal. If $p_1(t)=p_2(t)$, then $t_1-t_2 \in n\mathbb{Z}$ so $t_1 = t_2 +n = \tau_n(t_2)$ with $\tau_n \in \text{Homeo}(\mathbb{R},p)$.

2. $p: S^1 \to S^1$, $z \mapsto z^3$ is normal

3. ![[Screenshot 2025-10-07 at 3.38.11 pm.png|250]] 
   example deck transformation: $a'\leftrightarrow a'',\:b'\leftrightarrow b'',\:v'\leftrightarrow v''$. This is a normal cover.

## Non-example

![[Screenshot 2025-10-07 at 3.40.07 pm.png|200]]


# Normaliser 

>[!def] 
>$G$ a group. $H \leq G$. The **normaliser** of $H$ in $G$ is $N_G(H) = \{g \in G \:|\: gHg^{-1} = H\}$  

>[!proposition] 
>Let $p$ be a covering space with $X,\widetilde{X}$ *path-connected*, and $X$ *locally path-connected*. Let $G = \pi_1(X,x_0)$ and $H = p_*(\pi_1(\widetilde{X},\widetilde{x}_0))$ so $H \leq G$. Then
>
>1. $p$ is a normal cover $\iff$ $H$ is a normal subgroup of $G$. 
> 	  In particular if $\widetilde{X}$ is a universal cover, then $p$ is a normal cover.
>2. $\text{Homeo}(\widetilde{X},p) \cong N_G(H)/H$
> 	  in particular if this is a normal cover, then $\text{Homeo}(\widetilde{X},p) \cong G/H = \pi_1(X,x_0)/H$. So if $\widetilde{X}$ is a universal cover, we get $\text{Homeo}(\widetilde{X},p) \cong \pi_1(X,x_0)$.
> 	  i.e. group of the deck transformations of a universal cover of $X$ is isomorphic to the $\pi_1$ of $X$.
> 	  
##### Proof
###### Part 1
$\widetilde{x}_1,\widetilde{x}_2 \in p^{-1}(x_0)$.
Changing basepoint of $\pi_1(\widetilde{X})$ from $\widetilde{x}_1$ to $\widetilde{x}_2$ corresponds t o conjugating $H$ by $[\gamma]\in \pi_1 (X,x_0)$ where $\gamma$ lifts to a path $\widetilde{\gamma}$ from $\widetilde{x}_1$ to $\widetilde{x}_2$. So $[\gamma]\in N_G(H) \iff p_*(\pi_1 (\widetilde{X},\widetilde{x}_1)) = p_*(\pi_1 (\widetilde{X},\widetilde{x}_2)) \iff \exists \:\text{lifts}\: \widetilde{f}:(\widetilde{X},\widetilde{x}_1) \to (\widetilde{X},\widetilde{x}_2)$ and $\widetilde{g}:(\widetilde{X},\widetilde{x}_2) \to (\widetilde{X},\widetilde{x}_1)$ such that $p \circ \widetilde{f} = p$ and $p \circ \widetilde{g}=p$ (from lifting criterion).
i.e. $\widetilde{f},\widetilde{g}$ are deck transformations and since $\widetilde{g}\circ \widetilde{f}$ fixes $\widetilde{x}_1$ and $\widetilde{f} \circ \widetilde{g}$ fixes $\widetilde{x}_2$, then $\widetilde{f},\widetilde{g}$ are inverses.

Thus $[\gamma] \in N_G(H) \iff$ there is a deck transformation sending $\widetilde{x}_1$ to $\widetilde{x}_2$. Thus $H$ is normal in $G \iff$ the cover $p$ is normal.

###### Part 2
Want to show $\text{Homeo}(\widetilde{X},p) \cong N_G(H)/H$. We show there is a surjective homomorphism $\varphi: N_G(H) \to \text{Homeo}(\widetilde{X},p)$ with $\ker \varphi=H$. Then by 1st isomorphism theorem we have the result.

Define $\varphi$ for $[\gamma] \in N_G(H) \leq \pi_1(X,x_0)$ by $\varphi([\gamma])= \widetilde{f}$  i.e. $\widetilde{f}$ is a deck transformation., taking $\widetilde{\gamma}(0)=\widetilde{x}_1$ to $\widetilde{\gamma}(1) = \widetilde{x}_2$ where $\widetilde{\gamma}$ lifts $\gamma$.

To see $\varphi$ is a homom: Suppose $\varphi([\gamma])=\widetilde{f}$ with $\widetilde{f}(\widetilde{x}_1)= \widetilde{x}_2$, $\varphi([\gamma'])= \widetilde{f}'$ with $\widetilde{f}'(\widetilde{x}_1)=\widetilde{x}_2'$. Both $\gamma,\gamma'$ are loops corresponding to deck transformations taking $\widetilde{x}_1$ to $\widetilde{x}_2$, $\widetilde{x}_1$ to $\widetilde{x}_2'$ respectively.

Then $\gamma\cdot \gamma'$ lifts to the path $\widetilde{\gamma}\cdot (\widetilde{f}\circ \widetilde{\gamma}')$ from $\widetilde{x}_1$ to $\widetilde{f}(\widetilde{x}_2') = \widetilde{f}(\widetilde{f'}(\widetilde{x}_1))$ via $\widetilde{x}_2$.
Thus $\widetilde{f}\circ \widetilde{f}'$ is the deck transformation corresponding to $[\gamma][\gamma']$, hence $\varphi([\gamma][\gamma'])= \varphi([\gamma\cdot\gamma']) = \widetilde{f}\circ \widetilde{f}' = \varphi([\gamma])\varphi([\gamma'])$. 
$\therefore \varphi$ is a homomorphism and surjectivity comes from Part 1.

*Kernel:* Suppose $\varphi([\gamma])=\widetilde{f}$ with $\widetilde{f}(\widetilde{x}_1)=\widetilde{x}_2$. If $[\gamma]\in \ker \varphi$, then $\varphi([\gamma])$ is the identity deck transformation, which corresponds to $\widetilde{\gamma}$ a loop in $\widetilde{X}$. i.e. $\widetilde{\gamma}$ such that $[\gamma]=p_*([\widetilde{\gamma}]) \subseteq H$.


## Examples

$p: \mathbb{R}\to S^1$. Then $[\gamma]\in \pi_1(S^1,1)$. So $\gamma$ lifts to a path in $\mathbb{R}$ from $\widetilde{x}_1=0$ to $n$, where $[\gamma]$ represents $n \in \mathbb{Z}$. The deck translation corresponding to $[\gamma]$ is the translation $\tau_n$.



# Group Actions and Covering Spaces

Suppose group $G$ acts on a space $Y$ by homeomorphisms such that 
$$\begin{equation}
\forall y \in Y,\:\exists\: U \in \mathcal{N}(y)\: \text{s.t. if}\:\: g_1U \cap g_2U\neq \emptyset\:\:\text{for}\: g_1,g_2\in G \implies g_1=g_2 \tag{*}
\end{equation}$$

>[!proposition] 
>If $(\ast)$ holds, then:
>1. The quotient map $p: Y \to Y/G$ via $y \mapsto G_y=\{g\cdot y \:|\:g \in G\}$ is a normal cover
>2. If $Y$ is *path-connected*, then $G=\text{Homeo}(Y,p)$
>3. If $Y$ is *path-connected* and *locally path-connected*, then $G \cong \pi_1 (Y/G)/p_*(\pi_1 (Y))$
>   In particular, if a group $G$ acts by homeomorphisms and satisfies $(\ast)$, then $G=\text{Homeo}(Y,p)$, and $G \cong \pi_1(Y/G)$. i.e. the deck transformations of $Y$ w.r.t the quotient map, from the fundamental group of the quotient $Y/G$.

## Examples

1. $G=\mathbb{Z}$ acting on $\mathbb{R}$ by translation, $n \mapsto \tau_n$. This action satisfies $(\ast)$, so we get quotient map $\mathbb{R}\to S^1$, $x \mapsto \{x+n\:n \in \mathbb{Z}\}$ which is a normal cover. We have $G = \mathbb{Z}\cong \text{Homeo}(\mathbb{R},p)\cong \pi_1 (S^1)$.
2. $\mathbb{Z}^2$ acting on $\mathbb{R}^2$ by $(m,n)\cdot (x,y)=(x+m,y+n)$. Quotient space is a torus $T^2$ which satisfies $(\ast)$ so we get $\pi_1 (T^2)\cong \mathbb{Z}^2 \cong \text{Homeo}(\mathbb{R}^2,p)$.


