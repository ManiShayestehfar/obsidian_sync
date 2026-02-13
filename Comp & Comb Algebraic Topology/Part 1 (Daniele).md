
# Simplicial Complex

$n \in \mathbb{N}$, $[n] := \{0,1,...,n-1\}$. A **simplicial complex** $X$ on $[n]$ is $X \subseteq \mathcal{P}([n])$ such that if $\sigma \in X$ and $\tau \subset \sigma \implies \tau \in X$.

## SCPX Example

- Standard $n$-simplex $\Delta^n = \mathcal{P}([n+1])$ with $\partial\Delta^n = \Delta^n \setminus \{01...n\}$
- Simple graphs (e.g. no self-loops or multi edges)

## Simplicial Map

A **simplicial map** is a (set) map $f: V(X_1) \to V(X_2)$ such that if $\sigma$ is a simplex in $X_1\implies$ $f(\sigma) \in X_2$.
- It should respect identity, composition, and inclusion

*Q:* If $f$ is bijective and simplicial, then is $f^{-1}$ simplicial always? *NO!* e.g
![[Part 1 (Daniele)-1771021556225.png|200]]

## Geometric Simplex

Let $\{x_0,...,x_k\}\subseteq \mathbb{R}^n$ be *affinely independent*. That is, $\{(x_i-x_0)_{i=1,...,k}\}$ is linearly independent.

A **Geometric simplex** spanned by $\{x_0,...,x_k\}$ is $$\left\{ \sum_{i=0}^n t_ix_i \:|\: t_i\geq 0\:,\: \sum_{i=0}^nt_i=1\right\}$$

## Geometric Realisation

Fix $\phi: V(X) \to \mathbb{R}^n$. The **Geometric Realisation** of $X$ w.r.t. $\varphi$ is the union
$$|X|_\phi = \bigcup_{\sigma \in X} |\sigma|_\phi$$ where each $|\sigma|_\phi$ is the geometric simplex spanned by vertices $\langle\phi(v_0), ...,\phi(v_k)\rangle$

- Assume $\phi$ is an **Affine Embedding** e.g. It is injective and $\phi(V(X))$ is affinely independent.
- So the topology should be independent of $\phi$

### Proposition

If $\phi_0,\phi_1$ are affine embeddings of $X \to \mathbb{R}^N$, then $|X|_{\phi_0} \overset{homeo}{\cong}|X|_\phi$


### Links & Stars

$X$ a scpx, $\sigma \in X$. 

- The **Link** of $\sigma$ is $\ell k(\sigma) = \{\tau \in X \:|\: \tau \cap \sigma = \varnothing\:,\:\sigma \cup \tau \in X\}$
- The **Open star** of $\sigma$ is $St(\sigma)= \{\tau \in X \:|\: \sigma \subseteq \tau\}$
- The **Closed star** of $\sigma$ is $\overline{St}(\sigma) = \{\tau \in X \:|\: \tau \cup \sigma \in X\}$
	- $\overline{St} = St \cup \ell k$


# Homology

Just refer to my notes in [[Simplicial Homology]].

Just remember that $[\partial_k]\in R^{n_{k-1} \times n_k}$
where $n_k$ is the number of $k$-simplices in the simplicial complex


# Subdivisions

**Proposition:** $|X| \cong |Sd(X)| \cong |Stellar(X)|$

*Q:* If $|X| \cong |X'|$, then is there a simplicial map $f:X\to X'$ up to subdivisions?
*Partial Answer:*

**Theorem (Brouwer):** Let $f:|X| \to |X'|$, then $\exists N \geq 0$ such that $\hat{f}: Sd^N(X) \to X'$ a simplicial map such that $\hat{f}\simeq f$.


# Triangulation

A **triangulation** of an $k$-manifold $M^k$ is a homeomorphism $t:|X| \to M$ for some finite scpx $X$.
- e.g. $D^n \longleftrightarrow|\Delta^n|$ and $S^n \longleftrightarrow |\partial\Delta^{n+1}|$

## Minimal Triangulation

Let $\cal{M}$ be the set of closed oriented connected $k$-manifolds. 
Then $\mu_k: \mathcal{M} \to \mathbb{N}$ given by $M \longmapsto \text{min \# of k-spx in a triangulation of } M$  

- This allows us to find minimal triangulations

## Euler Characteristic

$X$ a scpx. It's **Euler characteristic** is an invariant $$\chi(X) = \sum_{\sigma \in X}(-1)^{\dim \sigma} = \sum_{i=0}^{\dim X}(-1)^i c_i$$ where $c_i$ is the number of $i$-simplices in $X$.



# Posets

