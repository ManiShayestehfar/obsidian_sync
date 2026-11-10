---
tags: [data5441, ch05, models]
aliases: [Barabási–Albert, BA model, Rich get richer]
---
---
# Preferential attachment (Barabási–Albert)

> [!abstract] Core idea
> The **Barabási–Albert (BA) model** gives a mechanism for the broad degree distributions seen in [[Power laws]]: the network **grows**, and new nodes preferentially attach to existing nodes that already have many links. The resulting continuum prediction is $P(z)\propto z^{-3}$.
>
> **Key formulas:** $\pi_i=z_i/(2L)$; $\langle z\rangle\to2m$; $z_i(t)\approx m\sqrt{t/t_i}$; $P(z)\approx2m^2z^{-3}$ ($\gamma=3$).
>
> Course: **DATA5441 Week 5**, lecture PDF pp. **71–73**. Prerequisite: [[Power laws]].

## 1. Why do hubs form?

The [[Power laws|WWW measurements]] show degree distributions with long tails, unlike the narrow Poisson degrees of sparse Erdős–Rényi graphs. **What kind of network formation can naturally produce hubs?**

The BA answer is the combination of:

- **Growth:** add new nodes over time.
- **Preferential attachment:** nodes with more existing links are more likely to receive new links (*rich get richer*).

This is a **generative model**, rather than a way to measure or fit a fixed graph.

![[Assets/ba-growth-and-age.png|780]]

*Left: schematic preferential attachment. The larger hub has more links, so it attracts new links with higher probability. Right: the continuum prediction at fixed $m=2$; an earlier arrival has a larger predicted degree at the same observation time.*

## 2. Definition of the BA model

> [!definition] Barabási–Albert model (course notation)
> Start with a small **connected** seed graph containing $N_0$ nodes and $L_0$ edges. At each integer time $t=1,2,\ldots$:
> 1. Add **one new node**.
> 2. Give it **$m$ links** to $m$ existing nodes ($m\le N_0$ in the lecture's construction).
> 3. Select attachment targets preferentially, with probability proportional to current degree:
>    $$\boxed{\pi_i(t)=\frac{z_i(t)}{\sum_jz_j(t)}=\frac{z_i(t)}{2L(t)}.}$$
>
> The equality uses the **handshaking lemma**, $\sum_jz_j=2L$.

For example, if existing nodes have degrees $2$ and $8$, their attachment weights are in the ratio **$1:4$**; the degree-$8$ node is four times as likely to receive a given preferential attachment in the one-link sampling rule.

The seed ensures the network is initially connected; adding nodes with at least one link **preserves connectivity**. The standard simple-graph construction prevents loops and repeated links.

### Sparsity by construction

After $t$ new nodes, we have exactly

$$N(t)=N_0+t,\qquad L(t)=L_0+mt.$$

Thus, with $N_0,L_0$ fixed and $t\to\infty$,
$$\boxed{\langle z\rangle=\frac{2L(t)}{N(t)} \approx \frac{2m}{m}\longrightarrow2m.}$$
So the BA graph remains **sparse**, even though some of its individual nodes become very highly connected.

## 3. How a node's degree grows

A node $i$ was introduced at time $t_i$, so its initial degree is $z_i(t_i)=m$. At each time step, the expected number of new links it receives is approximately $m\pi_i$.

> [!proposition] Continuum (mean-field) degree-growth law
> For $t\gg t_i$ and $L(t)\approx mt$, the BA approximation predicts
> $$\boxed{z_i(t)\approx m\sqrt{\frac{t}{t_i}}.}$$

> [!proof]- Derivation from the attachment rule
> Replace the discrete expected degree increment by a derivative:
> $$\frac{dz_i}{dt}\approx m\pi_i(t)=\frac{mz_i(t)}{2L(t)}\approx\frac{z_i(t)}{2t}.$$
> Separate variables and integrate:
> $$\frac{dz_i}{z_i}=\frac{dt}{2t}\quad\Longrightarrow\quad\log z_i=\tfrac12\log t+c\quad\Longrightarrow\quad z_i(t)=A\sqrt t.$$
> Apply the birth condition $z_i(t_i)=m$, giving $A=m/\sqrt{t_i}$. Hence
> $$z_i(t)\approx m\sqrt{t/t_i}.\qquad\square$$

**Interpretation:** at the same $t$, a node born four times earlier has approximately twice the predicted degree. This is a **statistical age advantage**; it does **not** mean every old node must be more connected than every young node in each random realisation.

## 4. Why the degree distribution has exponent $\gamma=3$

The growth law tells us each node's degree as a function of its birth time. To get $P(z)$, ask: **What fraction of nodes are old enough to have degree at least $z$?**

> [!proposition] BA degree tail (continuum approximation)
> $$\boxed{\Pr(Z\ge z)\approx\frac{m^2}{z^2},\qquad P(z)\approx2m^2z^{-3}.}$$
> Therefore the BA exponent is **$\gamma=3$**.

> [!proof]- Convert birth times into the degree distribution
> For an observation time $t$ and $z\ge m$,
> $$z_i(t)\ge z\ \Longleftrightarrow\ m\sqrt{\frac{t}{t_i}}\ge z\ \Longleftrightarrow\ t_i\le \frac{m^2t}{z^2}.$$
> There is one new node per time step, so among the approximately $t$ nodes, the fraction with birth time at most $u\le t$ is approximately $u/t$. Thus
> $$P_>(z)=\Pr(Z\ge z)\approx\frac{m^2t/z^2}{t}=\frac{m^2}{z^2}.$$
> Treat $z$ as continuous and differentiate the tail:
> $$P(z)\approx-\frac{d}{dz}P_>(z)=\boxed{2m^2z^{-3}}.\qquad\square$$

> [!tip] Fast way to remember the exponent
> **Preferential attachment → $z_i(t)\propto t_i^{-1/2}$ → $P_>(z)\propto z^{-2}$ → $P(z)\propto z^{-3}$.**
>
> These are continuum asymptotics; a discrete finite BA graph does not have an exactly smooth density.

## 5. What the model explains — and what it misses

| Property | Prediction / limitation |
|---|---|
| **Sparsity** | Yes: $\langle z\rangle\to2m$ |
| **Hubs and broad degrees** | Yes: $P(z)\propto z^{-3}$ rather than Poisson |
| **Relative degree variability** | Much larger than ER; since $\gamma=3$, $\langle z^2\rangle$ grows logarithmically with system size in the usual cutoff approximation |
| **Connectivity** | Preserved if the seed is connected and every new node attaches to at least one old node |
| **High clustering** | **No:** clustering decreases towards $0$ for large $N$; in particular, $m=1$ with a tree seed produces a tree |
| **Flexible degree exponent** | **No:** the basic model fixes $\gamma=3$ |

### Connection back to the WWW picture

The WWW plot in [[Power laws]] has historical empirical exponents **$\gamma_{\mathrm{in}}\approx2.1$** and **$\gamma_{\mathrm{out}}\approx2.45$**, both differing from $3$. Moreover, the **WWW is directed**, whereas the basic BA model in this lecture is **undirected**. Thus BA gives a **simple plausible mechanism for heavy tails**, *not* an exact reproduction of those WWW measurements.

The lecturer also points out an **age bias**: $z_i(t)\propto t_i^{-1/2}$ favours early arrivals. Real networks can instead favour recent or newly popular nodes; adding an **ageing or fitness factor** to the attachment probability is one possible extension.

## 6. Exam applications

> [!exam] Matching BA with a sparse ER network (Trial Exam 1, Q6; Trial Exam 2, Q4)
> Let the ER network have $\langle z\rangle\approx12$. To match the number of edges asymptotically, choose
> $$\langle z\rangle_{\mathrm{BA}}\approx2m=12\quad\Longrightarrow\quad\boxed{m=6}.$$
>
> **Which model has larger $\sigma_z/\langle z\rangle$?** BA: its heavy-tailed degrees allow hubs, whereas ER degrees are approximately Poisson. **Do either of the basic models reproduce non-vanishing clustering as $N\to\infty$?** No.

> [!question]- Self-test
> 1. **Why does $\pi_i=z_i/(2L)$?** Attachment weight is proportional to degree; all degrees sum to $2L$.
> 2. **What is the average degree after many steps?** $2m$.
> 3. **If $t_i=25$, $m=2$, and $t=100$, what is $z_i(t)$?** Approximately $2\sqrt{100/25}=4$.
> 4. **Where does the exponent $3$ come from?** Degree $z$ corresponds to birth time $t_i\propto z^{-2}$, giving CCDF $z^{-2}$ and PMF $z^{-3}$.
> 5. **Why is BA not a perfect model of the WWW?** Basic BA is undirected, its exponent is fixed at $3$, and it does not reproduce high clustering.

> [!code]- Minimal NetworkX check (Week 5 tutorial)
> ```python
> import networkx as nx
> import numpy as np
>
> G = nx.barabasi_albert_graph(n=N, m=m, seed=13)
> z = np.array([d for _, d in G.degree()])
> print(z.mean(), z.std() / z.mean())
> ```

---
Related: [[Power laws]] · [[Small-world networks]] · [[Erdos-Renyi graphs]] · [[Clustering]]
