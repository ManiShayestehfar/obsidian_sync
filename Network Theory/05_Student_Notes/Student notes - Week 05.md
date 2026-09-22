---
type: student-source
week: 5
status: supplementary-unverified-source
---

# Student notes - Week 05

[[Student notes index]] · [[Corrections and caveats]]

> [!warning] Secondary source
> Format conversion of Jeny Yuan’s supplied LaTeX notes (identified by the user as last year’s notes). Mathematical errors in the source are retained here, not endorsed. Use the checked 2026 lecture notes for Weeks 1–7. Missing figures are labelled. Formatting has been normalised; the original TeX is retained in `06_Sources/student_notes_original.tex`.

# The Small World Effect

There are three properties of the small world phenomenon

- The networks are sparse: $\frac{L}{N^2} \to 0$ and $\langle z\rangle \to \mathrm{constant}$

- The clustering $C\to C^* >0$ as $N\to \infty$.

- Short distances: $\langle \langle d\rangle \rangle \sim \log N \ll N^{\beta}$.

## Watts-Strogatz Model

1.  Start with a ring with $N$ nodes connected to $Q$ ring neighbours.

    <figure>
    <p>```latex
\begin{tikzcd}
	& 8 & 1 \\
	7 &&& 2 \\
	6 &&& 3 \\
	& 5 & 4
	\arrow[no head, from=1-2, to=1-3]
	\arrow[no head, from=1-2, to=2-4]
	\arrow[no head, from=1-3, to=2-4]
	\arrow[no head, from=1-3, to=3-4]
	\arrow[no head, from=2-1, to=1-2]
	\arrow[no head, from=2-1, to=1-3]
	\arrow[no head, from=2-1, to=3-1]
	\arrow[no head, from=2-1, to=4-2]
	\arrow[no head, from=2-4, to=3-4]
	\arrow[no head, from=2-4, to=4-3]
	\arrow[no head, from=3-1, to=1-2]
	\arrow[no head, from=3-1, to=4-2]
	\arrow[no head, from=3-1, to=4-3]
	\arrow[no head, from=3-4, to=4-3]
	\arrow[no head, from=4-2, to=3-4]
	\arrow[no head, from=4-3, to=4-2]
\end{tikzcd}
```

*Original diagram source retained; Obsidian does not render TikZ.*</p>
    <figcaption><span class="math inline"><em>Q</em> = 2</span> and <span class="math inline"><em>N</em> = 8</span> links</figcaption>
    </figure>

2.  For each of the $L$ edges, rewire with probability $p$. When rewiring, we can either delete the link and add a new one randomly, or delete one end of a link and attach it to a random node.

**Question:** for which values of $Q$ and $P$ are these random graph networks small world?

1.  Sparsity: we know $$L= NQ \implies \langle z\rangle = \frac{2L}{N} = 2Q = \mathrm{constant}$$ so it is sparse by construction.

2.  Clustering:

    - For a ring (i.e. $p=0$), as $N\to\infty$ we have $$C_{ring} = C_i = \frac{\Delta_i}{\binom{z_i}{2}} \propto \frac{\binom Q2}{\binom{2Q}{2}} = \frac{Q-1}{2Q(2Q-1)} > 0$$

    - If $p>0$, we check the probability of a triangle surviving the rewiring process. The odds of each edge surviving is $1-p$. $$```latex
\begin{tikzcd}
	& \bullet \\
	\bullet && \bullet
	\arrow["{1-p}"', no head, from=1-2, to=2-1]
	\arrow["{1-p}", no head, from=1-2, to=2-3]
	\arrow["{1-p}"', no head, from=2-1, to=2-3]
\end{tikzcd}
```

*Original diagram source retained; Obsidian does not render TikZ.*$$ $$C(p) = C_{\mathrm{ring}}f(p) = C_{\mathrm{ring}}(1-p)^3$$

3.  Short distances: $d_\mathrm{diameter}$

    - $p=0$ we have $d_{\mathrm{diam}} \approx N/2Q$.

    - For $p>0$ we write $d_{\mathrm{diam}} (p) = d_{\mathrm{diam}}(\mathrm{ring})g(p)$

      Intuition: for $p\to1$, $d_\mathrm{diameter}\sim \ln N$. For small $p$, a *rewired edge* act as a *shortcut*. Hence, $g(p)$ decays as soon as a few $("B")$ shortcuts appear, $B(N)$ grown slower than $N$.

      The number of shortcuts is given by $pL =  pQN \geq B$ for $N\gg1$. Short distances appear for $p>\frac{B}{QN} \implies\frac{B}{QN}\ll1$, i.e. the $p$ required for short distances goes to zero.

      In the limit $N\to\infty$, we have that $\frac{C}{C_\mathrm{ring}}=(1-p)^3$

      <figure>
      <p><strong>Figure unavailable in supplied archive: imgs/watts-strogatz.png</strong></p>
      </figure>

      Key idea is that there is a region of $p$-values such that the diameter decreases sharply because of the existence of shortcuts, but the clustering does not decrease yet. So if we start from a ring graph and add a few random links, the clustering is not strongly affected, but the distance is strongly affected.

## Scale-Free Networks

How does $\frac{\sigma_z}{\langle z\rangle}$ grow with $N$?

The degree distribution is such that $p(z)=\frac{1}{N}\sum_{i=1}^N \delta(z_i-z)$. If $p(z) \sim z^{-\gamma}$ (fat tail), then $$\langle z^2\rangle\approx \int_1^\infty z^2z^{-\gamma}dz=z^{3-\gamma}\bigr|_1^\infty\to \infty \qquad \text{for }\gamma\leq 3$$

So for $2<\gamma\leq 3$, $$\begin{cases} \langle z\rangle & \text{is defined (sparsity)} \\ \langle z^2\rangle & \text{diverges}\end{cases} \implies \frac{\sigma_z}{\langle z\rangle} = \frac{\sqrt{\langle z^2\rangle}}{\langle z\rangle}\to\infty$$

How is $\left\langle{z^2}\right\rangle$ diverging with $N$? Suppose we have the pdf of $z$ is given by $z^{-\gamma}$. We argue that the expected *maximum value* by taking $N$ samples is $\frac{1}{N}$.

Hence, although $\left\langle{z^2}\right\rangle$ diverges, we have that for a finite sample of $z$’s, the expected degree is finite.

The expected maximum of $z$ over $N$ samples $z_{\max}$: $$p(z_{\max})=\frac{1}{N} \sim z_{\max}^{-\gamma}\implies z_{\max}\sim N^{\frac{1}{\gamma}}$$ $$\left\langle{z^2}\right\rangle\approx c\left.\int_1^{z_{\max}}z^{-\gamma+2}dz\propto (z^{-\gamma+3})\right|_1^{z_{\max}}=N^\beta$$ where $$\beta = \frac{-\gamma+3}{\gamma} = -1+\frac{3}{\gamma} \qquad \text{that is, grows with $N$ for }\gamma<3$$

## Empirical Conjecture

We see some variations of the interpretation of *fat tails*

- **Weakest interpretation:** $\exists\alpha>2$ such that $\left\langle{z^\alpha}\right\rangle\to \infty$ as $N\to\infty$

- **Weak interpretation:** $\frac{\sigma_z}{\left\langle{z}\right\rangle}\xrightarrow[N\to\infty]{}\infty$

- **Strong interpretation (power-law distribution):** $p(z)=Az^{-\gamma}$ for $2\leq \gamma\leq 3$ and large $z$. Then, $\log p(z)\approx -\gamma\log z + \log A$ (linear behaviour)

## Preferential Attachment Model

1.  Start at $t=0$ with $N_0\ll N$ nodes randomly connected.

2.  At each $t>0$, add one node and connect to $m$ existing nodes for $m\leq N_0 \ll N$.

3.  The probability of linking to node $i$ is proportional to the degree of the node: $\pi_i=\frac{z_i}{\sum_i z_i}=\frac{z_i}{2L(t)}$

As $t\to\infty$, we have

- $N=N_0+t\approx t$, since $N_0\ll N$

- $L(t)=L_0+mt\approx mt$ as $L_0\ll mt$

But what about $P(z)$?

Let’s focus on one node $i$ created at time $t_i\ll t$ such that $z_i\gg m$. Hence, $$\frac{\hspace{1.5pt}\mathrm{d}{z_i}}{\hspace{1.5pt}\mathrm{d}{t}} = m\pi(z_i) =\frac{mz_i}{2L(t)} \approx \frac{z_i}{2t}$$ This is a first order separable ODE with the *general solution*: $$\int \frac{1}{z_i}\hspace{1.5pt}\mathrm{d}{z_i} = \int\frac{1}{2t}\hspace{1.5pt}\mathrm{d}{t}\implies \ln z_i=\frac{1}{2}\ln t+c\implies z_i=A\sqrt{t} \quad\text{where }A=e^c\text{ is a constant}$$ The initial condition is the node created at time $t_i$, i.e. $z_i(t=t_i) = m = A\sqrt{t_i}$. Hence, the *particular solution* is $$A=\frac{m}{\sqrt{t_i}} \implies z_i(t) =m \sqrt{\frac{t}{t_i}}$$ So then $$z_i>z\implies m\sqrt{\frac{t}{t_i}}>z\implies m^2\frac{t}{t_i}>z^2\implies t_i<\frac{m^2t}{z^2}$$ Hence, we have complement CDF of the degree distribution in terms of $t$, given by $$P\left(z_i(t)>z\right) = P\left(t_i<\frac{m^2}{z^2}t\right) =\frac{m^2}{z^2}t\cdot\frac{1}{N}=\frac{m^2}{z^2}$$

Then the degree distribution is $$p(z)=\frac{\partial p(z_i>z)}{\partial z}\sim \frac{\partial}{\partial z}\frac{m^2}{z^2}\sim\frac{1}{z^3} \quad\text{in the }\gamma=3\text{ case}$$

To summarise, we have

- $\langle z\rangle = 2L/N$

- For Barabasi-Albert it depends on two parameters $m$ and $N$, so $L=mt$ and $N=t$

- For Poisson random graph, depends on the parameters $p$ and $N$ and $L=p\binom N2$.

Some positive characteristics of the Barabasi-Albert preferential attachment model

- Always creates a simple connected component

- BA networks have a large $\sigma_z/\langle z\rangle$, and a power law for $p(z)$, which is exhibited by real world networks.

Some limitations are

- $\gamma =3$ is a restriction for the scale factor. Most empirical cases have a slope $2 < \gamma < 3$ so the model might not be a good fit for the real world network. To resolve this we might need a modification of $\pi_i(z)$.

- Older models are always the hubs $z_i \sim \sqrt{t/t_i}$ in the Barabasi-Albert. But sometimes there is a tendency to focus on recent trends. This can be resolved by some sort of ageing effect $\pi(z_i, t-t_i)$.

- The clustering coefficient $C(N)\to 0$, more slowly than the Poisson random graph, but $C(N)\sim N^{-\beta}$ for some $\beta \in (0,1)$.

Power law distribution appear also in other network quantities (e.g. Betweeness centrality)

Why scale free? Suppose $p(z) = cz^{-\gamma}$ then if we rescale $z$ by a factor $\alpha$ then the map $z\mapsto \alpha z$ has degree distribution $p(\alpha z ) = c(\alpha z)^{-\gamma} = c\alpha^{-\gamma}z^{-\gamma} = \tilde c z^{-\gamma}$ is again a power law distribution so it is invariant under scaling transformations. There is no characteristic scale for the network.
