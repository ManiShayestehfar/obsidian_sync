---
type: student-source
week: 10
status: supplementary-unverified-source
---

# Student notes - Week 10

[[Student notes index]] · [[Corrections and caveats]]

> [!warning] Secondary source
> Format conversion of Jeny Yuan’s supplied LaTeX notes (identified by the user as last year’s notes). Mathematical errors in the source are retained here, not endorsed. Use the checked 2026 lecture notes for Weeks 1–7. No 2026 lecture PDF or tutorial for this week was supplied. Missing figures are labelled. Formatting has been normalised; the original TeX is retained in `06_Sources/student_notes_original.tex`.
>
> **Specific correction:** The targeted-removal discussion contains an incorrect maximum-degree scaling; see [[Corrections and caveats]].

# Dynamics on Networks

**Question:** How senstive is a network against perturbation?

For example,

- Communications networks. What happens if a link fails? Can the data still reach the destination?

- Power grid networks. What happens if the cables are broken? Can the energy still be transmitted by rerouting it?

In a simplified setting,

1.  Start with a graph $g$.

2.  Delete a fraction of the links of $g$, or the nodes, denoted by $q$

3.  Measure how a network property $x(g)$ depends on $q$.

If the metric changes rapidly with $q$, the network might be sensitive to this change – susceptible to this failure.

The key observable is $x(g)\cong K_1(g)\equiv \lim_{N\to \infty} \frac{N_{k=1}}{N}$ i.e. the size of the largest component. Then the network will still exist in some sense.

## Percolation

We can map these problems to those of percolation in applied mathematics.

Imagine in a sponge is full of holes and we pour some water in it. If the sponge has almost no holes, or very tiny holes, then the water has a difficult time finding a path to navigate the sponge.

In a 3d lattice some of the links could be ON or OFF, and we want to find a path following only ON edges that takes you from the top layer to the bottom layer.

The **percolation theory** is the study of the existence of such paths as a function of how many edges is ON or OFF.

For each link (*bond*) or node (*site*), we define a state: $$\phi_i=
\begin{cases}
    1 & \text{on or occupied} \\
    0 & \text{off or empty}
\end{cases}$$ where we choose $\phi_i$ such that $\langle\phi_i\rangle=p=1-q$, which is the probability of being “on".

We would like to find the probability $\pi$ such that there is a percolation path connecting both sides of the network. Usually, when $N\to\infty$ we have, for the critical value $p_c$, $$\pi=
\begin{cases}
    0 & p<p_c \\
    1 & p>p_c
\end{cases}$$

An equivalent consideration is whether we can travel through a network for an arbitrary distance if links are ON with probability $p$. First consider some examples:

- $1$d lattice $(z=2)$ for nodes. The trivial answer is yes only if $p=1, q=0$ and $P_c=1$, $q_c=0$.

- Bethe Lattice (a tree where all nodes have degree 3). Denote $\theta$ to be the probability of travelling through an infinite path as $N\to \infty$. Then $\theta(p)=?$

  Let $\omega := 1-\theta$ be the probability of stopping. If we stop, it is because of one of two possibilities:

  - the link is OFF with probability $1-p$.

  - The link is ON but it leads to a dead end.

  The probability of stopping for each link is then $1-p+p\omega$. For the two outgoing links, it is $(1-p+p\omega)^2$. The self consistent equation is $$\omega=(1-p+p\omega)^2\implies \omega=1 \text{ or }\left(1-\frac{1}{p}\right)^2\,,$$ then $$\theta = 1-\omega = \left({\underbrace{0}_{\text{trivial solution}},\underbrace{1-\left|{\frac{1}{p}-1}\right|^2}_{\theta^*,\text{ non-trivial solution}}}\right)$$ and $$\theta`^*=1-\frac{1}{p}-1+\frac{2}{p}=\frac{1}{p}\left(2-\frac{1}{p}\right)$$ If $0\leq \theta^*\leq 1$ then at $p=\frac{1}{2}$ we have $\theta^*=0$, and at $p>\frac{1}{2}$, we have $\theta^*>0$. Hence the critical value $p_c=\frac{1}{2}$.

So the percolation result is that $K_1$ decreases concavely with $q$ until $q_c$ where it reaches 0, then is 0 for $q>q_c$.

I wish it only took babies 9 weeks to come out and then half of them die upon birth.

## Giant Component and Robustness of Random Graphs

### Random Graph with Fixed Degree Distribution $P(z)$

We consider percolation to be equivalent to the onset of a giant component, which happens when a node $i$ is connected to $j$ and has at least one additional link. The expectation of degree of $z_i$ conditioned on a link between $i$ and $j$: $$\langle z_i\mid i\leftrightarrow j\rangle\geq 2$$ which can be written as $$\label{eq:star_w10}
\sum_{z=1}^\infty z P(z\mid i\leftrightarrow j)\geq 2 \tag{*}$$ Using Bayes formula: $$P(z_i\mid i\leftrightarrow j)=P(i\leftrightarrow j\mid z_i)\frac{P(z)}{P(i\leftrightarrow j)}$$ where $p(z)$ is the degree distribution. We also have that same $P(i\leftrightarrow j)=\frac{\langle z\rangle}{N-1}$ and $P(i\leftrightarrow j\mid z_i)=\frac{z_i}{N-1}$ so inserting back into [[Student notes - Week 10|source cross-reference: eq:star_w10]], we get $$\sum_{z=1}^\infty z\frac{z_i}{N-1}\frac{N-1}{\langle z\rangle}P(z)=\sum_{z}\frac{z^2P(z)}{\langle z\rangle}=\frac{\langle z^2\rangle}{\langle z\rangle}\geq 2$$

<u>Consider the example</u> of the Poisson RG. The property of the Poisson distribution is that $\sigma_z^2=\langle z\rangle$ (equivariance), so $$\langle z^2\rangle - \langle z\rangle^2=\langle z\rangle \implies \frac{\langle z^2\rangle}{\langle z\rangle}=1 + \langle z\rangle\geq 2\implies \langle z\rangle\geq 1$$

### Random Deletion of Nodes or Links (Failure) in a RG with $P(z)$

We go from $P(z)\to P(z')$ after deleting links with probability $q$. We are then interested in computing $P(z')$, using the previous formula: $$P(z')=\sum_{z=1}^\infty P(z)P(z\to z')$$ where $$P(z\to z')=\binom{z}{z'}(1-q)^{z'}q^{z-z'}$$ so to compute the components we have $$\begin{cases}
    \langle z'\rangle &= \sum_{z'=1}^\infty z' P(z')= (1-q)\langle z\rangle \\ 
    \langle z'^2\rangle &= \sum_{z'=1}^\infty z'^2P(z')= (1-q)^2\langle z^2\rangle+\langle z\rangle q(1-q)
\end{cases}$$ which if we insert into [[Student notes - Week 10|source cross-reference: eq:star_w10]] we have $$\frac{\langle z'^2\rangle}{\langle z'\rangle} = \frac{(1-q)^2\langle z^2\rangle+\langle z\rangle q(1-q)}{(1-q)\langle z\rangle}\geq 2$$ solving for $q$: $$\begin{aligned}
(1-q)\frac{\langle z^2\rangle}{\langle z\rangle}+q\geq 2 &\implies q\left(1-\frac{\langle z^2\rangle}{\langle z\rangle}\right)\geq 2-\frac{\langle z^2\rangle}{\langle z\rangle} \\
&\implies q\leq\frac{1+1-\frac{\langle z^2\rangle}{\langle z\rangle}}{1-\frac{\langle z^2\rangle}{\langle z\rangle}}=1+\frac{1}{1-\frac{\langle z^2\rangle}{\langle z\rangle}}=1-\frac{1}{\frac{\langle z^2\rangle}{\langle z\rangle}-1}
\end{aligned}$$ So the critical value of $q$ is $$q_c=1-\frac{1}{\frac{\langle z^2\rangle}{\langle z\rangle}-1}\implies p_c=1-q_c=\frac{1}{\frac{\langle z^2\rangle}{\langle z\rangle}-1}$$

<u>Consider some examples</u> from the previous tutorial cases:

- In the simplest case of the $K$-regular graph (this includes the Bethe Lattice result) we have $$P(z) = \delta(z-3) \implies \langle z\rangle = \sum z\delta(z-3) = 3 \,, \langle z^2\rangle = 9\,.$$ Then the critical value is $$q_c= 1-\frac{1}{3-1} = \frac12\,.$$

- In the Poisson RG of the W10 tutorial, we had $\langle z\rangle = 4$. Then $$q_c=1-\frac{1}{\langle z\rangle +1-1}=1-\frac{1}{4}=\frac{3}{4}$$

- For the general random scale-free network ($P(z)\sim z^{-\gamma}$ for $2\leq \gamma\leq 3$, remember the BA graph is the case where $\gamma=3$) we have $\langle z^2\rangle\to\infty$ as $N\to\infty$, so the critical value $$q_c\to 1$$ hence there is no percolation threshold in scale-free networks (i.e. they are robust against random failures).

## Networks Under Attack

What happens if the nodes are not deleted randomly, but instead we attack the high-degree nodes, ie. the hubs?

For the setup, consider starting with a graph (RG with $P(z)$), and removing a fraction $q$ of nodes either randomly or from highest to smallest degree.

We can again consider the formula $$q_c=1-\frac{1}{\frac{\langle z^2\rangle}{\langle z\rangle}-1}$$ but the problem with this formula is that it was computed for links, not nodes, and for random removal, not targeted attacks.

The idea for this is to compute finite $N$ results: $$z_{\max}\sim\frac{1}{N^{\gamma-1}}$$ and delete the top node $$z_{\max}^{(n)}\to z_{\max}'(N-1)$$ which removes $z_{\max}$ edges. Then we can use the previous formula.

For scale-free networks $$P(z)\sim z^{-\gamma} \quad\text{for }2\leq\gamma\leq 3$$ the conclusion is that

1.  They are robust against failures ($q_c=1$).

2.  They are fragile against top-node attacks ($q_c\leq 1$).
