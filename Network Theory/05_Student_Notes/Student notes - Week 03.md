---
type: student-source
week: 3
status: supplementary-unverified-source
---

# Student notes - Week 03

[[Student notes index]] · [[Corrections and caveats]]

> [!warning] Secondary source
> Format conversion of Jeny Yuan’s supplied LaTeX notes (identified by the user as last year’s notes). Mathematical errors in the source are retained here, not endorsed. Use the checked 2026 lecture notes for Weeks 1–7. Missing figures are labelled. Formatting has been normalised; the original TeX is retained in `06_Sources/student_notes_original.tex`.

# Random Graph Models

## Network Models

There are **simple network models** (single graph), and **random network models**. We can use random networks as a null model to test our graph and our metrics.

**Definition 1** (Random Graph). A random graph (RG) is a set $\Omega$ of graphs and probabilities $p(g)$ for all $g\in\Omega$ such that $0\leq p(g)\leq 1$ and $\sum_{g\in\Omega}p(g)=1$.

Some measures $x(g)$ on a random graph: $g\in\Omega\rightarrow\mathbb{R}$

- Expected $x$ of a random graph: $\bar{x}=\sum_{g\in\Omega}p(g)x(g)$

- Standard deviation: $\sigma_x=\sqrt{(\overline{x^2}) - (\overline{x})^2}$

- Probability of $x=x^*$: $p(x^*)=\sum_{g\in\Omega} p(g)\delta(x(g)-x^*)$

Remark: for $N\rightarrow\infty$, we often have $\sigma_x\rightarrow 0$ and $p(x^*\neq\bar{x})\rightarrow 0$. We say $\bar x := x(\text{random graph)}$ is the *value of the measure* evaluated on the random graph.

Take a random graph with $N$ nodes. We have $|\Omega|=2^Y$, $Y=\frac{N(N-1)}{2}$, and $p(g)=\frac{1}{|\Omega|}$.

Consider $x \colon \Omega \to \mathbb N$ given by $x(g) = L$ (number of links in $g$). Then $$\bar{L}=\sum_{g\in\Omega}p(g)L(g)=\frac{1}{|\Omega|}\sum_{g\in \Omega}L(g)=\sum_{L=0}^Yp(L)\cdot L$$ where $p(L)\equiv\frac{N(L)}{|\Omega|}$ for $N(L)$ the number of $g\in\Omega$ with $L$ links: $N(L)=\binom{Y}{L}=\frac{Y!}{(Y-L)!L!}$, so $$\bar{L} = \frac{1}{2^Y}\sum_{L=0}^Y L\binom{Y}{L}=\frac{1}{2^Y}2^{Y-1}Y=\frac{Y}{2}=\frac{N(N-1)}{4}=\frac{L_{\max}}{2}\,.$$ This network is relatively *dense* as we have $L\sim N^2$. Moreover, $p(L)\rightarrow 0$ for any $L\neq\bar{L}$ as $N\rightarrow\infty$.

Consider $L^*=\alpha Y$ for $0\leq\alpha\leq 1$. We have $$p(L^*)=\frac{1}{|\Omega|}\sum_{g\in\Omega}\delta(L-L^*) = \frac{\binom{Y}{L^*}}{2^Y} = \frac{1}{2^Y}\frac{Y!}{(Y-L^*)!L^*!}$$ Using the *Stirling approximation* that $\ln q!\approx q\ln q - q$, if we apply $\ln$ to both sides $$\ln p(L^*) = -Y\ln 2 + (Y\ln Y - Y) - (Y-L^*)\ln(y-L^*) + (Y-L^*)  -L^*\ln L^*+L^*$$ and sub $L^* = \alpha Y$ back in, we get $$\ln p(L^*) = -Y[\ln 2 + (1-\alpha)\ln (1-\alpha) + \alpha\ln \alpha]\,.$$ If we set $B(\alpha) := \ln 2 + (1-\alpha)\ln (1-\alpha) + \alpha\ln \alpha$, the minimum of $B(\alpha)$ occurs at $\alpha = \frac{1}{2}$, then $B(\frac{1}{2})=0$. For $\alpha\neq \frac{1}{2}$, we have $B(\alpha)>0$ and $\ln p(L^*) \to -\infty$ as $Y\to \infty$.

One type of random graph model is the **Poisson random graph model**, defined as such: $$G(N,q):
\begin{cases}
    N & \text{is the number of nodes} \\
    q & \text{is the fixed probability of each link}
\end{cases}$$ Here $p_g$ is defined implicitly as $$p(g)=(1-q)^{Y-L}q^L \quad \text{where}\quad L=L(g)$$ then $$\bar{L} = \sum_{g\in\Omega}p(g)L(g)=qY$$ To fit $G(N,q)$ to an observed network $g^*$ with $N^*$ nodes and $L^*$ edges, fix $N=N^*$. The n $$\bar{L}=L^*\implies q=\frac{2L^*}{N^*(N^*-1)} = \frac{\langle z\rangle}{N^*-1}$$

Properties of the Poisson RG as $N\rightarrow\infty$:

- For fixed $q$, we have $\langle z\rangle \sim N$ (specifically $\langle z\rangle = q(N-1)$), which produces *dense* networks.

- For fixed $\langle z\rangle$, we have $q \sim \frac{1}{N}$ (specifically $q=\frac{\langle z\rangle}{N-1}$), which produces *sparse* networks.

- Degree distribution: the probability of having a node with degree $z$ follows a binomial distribution $p(z)=\binom{N-1}{q}q^z(1-q)^{N-1-z}$. Then for $N>>z$ and $q\ll 1$ such that $q(N-1)=\langle z\rangle=\text{constant}$, this becomes a Poisson distribution: $$p(z)\approx\frac{1}{z!}e^{-q(N-1)}(q(N-1))^z$$

- Variance: $\sigma_z^2=\langle z^2\rangle - \langle z\rangle^2=\langle z\rangle = q(N-1)$

- Degree variability: $\frac{\sigma_z}{\langle z\rangle}=\frac{1}{\sqrt{\langle z\rangle}}=\begin{cases} \rightarrow 0 & \text{if dense ie $q$ const.} \\ \rightarrow \text{const.} < 1 & \text{if sparse, ie $\langle z\rangle$ const.}  \end{cases}$

- Clustering: $\langle C\rangle \approx C_{net}$ because $\frac{\sigma_z}{\langle z\rangle}<1$. Then $C=q=\frac{\langle z\rangle}{N-1}=\begin{cases} \rightarrow \text{const.} & \text{if dense} \\ \rightarrow 0 & \text{if sparse} \end{cases}$

- Distances (largest component): under the assumption of sparsity ($\sigma_z/\langle z\rangle$ constant) for $N(d)$ nodes at distance $d$ from node $i$, $N(d)\approx \langle z\rangle^d$. This stops when $N(d)=N$ at $d=d_{diam}$. Then $d_{diam}\approx\frac{\ln N}{\ln \langle z\rangle}$ (plus a positive constant).

- Number of components and size of largest component: let $N_c$ be the number of components and $K_k$ for $k=1,...,N_c$ be the fraction of nodes in component $k$. The fraction $U$ of nodes not in $k=1$ is approximately equal to the probability of a node not being connected to $k=1$ when $N\rightarrow\infty$ and $\langle z\rangle=\text{const.}$

  The options of a node $i$ not being connected to $k=1$ via node $j$ are either that $i$ is not connected to $j$ (probability $1-q$), or that $i$ is connected to $j$ but $j$ is not connected to $k=1$ (probability $qU$). Then we get the self-consistent equation $$U=(1-q+qU)^{N-1} \quad (\text{for all }j\neq i)$$ Taking the log of both sides, noting $1-q+qU=1-\frac{\langle z\rangle}{N-1}(1-U) =: 1-\varepsilon$, and using the sparse limit (when $q\ll 1$, $N>>1$, and $\langle z\rangle=\text{const}$) that $\ln(1-\varepsilon)\approx -\varepsilon$ where $\varepsilon\ll 1$, we get the implicit equation $$U=e^{-\langle z\rangle(1-U)}\implies 1-K_1=e^{-\langle z\rangle K_1}$$ which, if we solve graphically, we get that $K_1=0$ and $K_1=K^*$ for $\langle z\rangle > 1$, or simply $K_1=0$ for $\langle z\rangle <1$.

**Recap:**

In the limit as $N\to \infty$, we have

- Poisson RG: dense case $q=\langle z\rangle/(N-1)$ is constant. Then the variation $\sigma_z/\langle z\rangle = 1/\sqrt{\langle z\rangle} \to 0$. The clustering $C_{\mathrm{net}} \approx q$ is a constant.

- Poisson RG: sparse case $\langle z\rangle$ constant, $q\to 0$. Then the variation $\sigma_z/\langle z\rangle$ is a constant, and we estimate $d_{\mathrm{diam}}$ with RG $\approx$ tree with $\langle  z\rangle$, so $d_{\mathrm{diam}} \approx \log N/\log \langle z\rangle$. The clustering $C_{\mathrm{net}} \approx q \sim 1/N\to 0$.

- $k$-regular. The variation $\sigma_z/\langle z\rangle = 0$, distances $\approx \log N$, and clustering satisfies $C_{\mathrm{net}} \approx q \sim 1/N$
