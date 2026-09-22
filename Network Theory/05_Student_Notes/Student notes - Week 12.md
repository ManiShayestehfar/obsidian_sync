---
type: student-source
week: 12
status: supplementary-unverified-source
---

# Student notes - Week 12

[[Student notes index]] · [[Corrections and caveats]]

> [!warning] Secondary source
> Format conversion of Jeny Yuan’s supplied LaTeX notes (identified by the user as last year’s notes). Mathematical errors in the source are retained here, not endorsed. Use the checked 2026 lecture notes for Weeks 1–7. No 2026 lecture PDF or tutorial for this week was supplied. Missing figures are labelled. Formatting has been normalised; the original TeX is retained in `06_Sources/student_notes_original.tex`.
>
> **Specific correction:** The diffusion and linear-stability equations contain inconsistent signs; use the explicit corrected conventions in [[Corrections and caveats]].

# Dynamics on Networks: Games and Continuous Time

## Games on Networks

**Definition 1**. A game between two players $i$ and $j$ is defined by

1.  a set $A$ of possible actions or strategies $\{e_1,\dots, e_{Q}\}$

2.  a $Q\times Q$ payoff matrix $M_{e_i,e_j}$.

An individual optimal strategy is the choice of $e_i$ that maximises its own payoff $m_i$ assuming $e_j$ is fixed (Nash equilibrium).

A collective optimum will be the maximum of $M_{e_i,e_j}$, i.e. best combined payoff $M_1+M_2$ given by $\underset{e_i,e_j}{\max}{(M_1+M_2)}$. When individual optimum leads to the collective optimum this leads to a win-win situation.

The more interesting case is when this is not true. An individual optimum does not lead to the collective optimum. For example, the prisoner’s dilemma.

Here, $Q=2$ with strategies $\{e_1,e_2\} = \{\text{cooperate}, \text{defect}\}$ then $$M_{e_i,e_j} = \begin{array}{c|c|c}
 & \text{B Cooperates} & \text{B Defects} \\
\hline
\text{A Cooperates} & (1, 1) & (0, b) \\
\text{A Defects} & (b, 0) & (0, 0) \\
\end{array}$$ The collective optimum is $e_1,e_1$ (coorperate, cooperate) and $M_{1,1}+M_{1,1}=-4$. However, the individual optimum for player 1 is defect, regardless of the choice of player 2.

Question: how can cooperation be achieved and is stable?

1.  Change the payoff (regulation)

2.  Allow for new strategies

3.  The game repeats (there is memory in the system)

4.  Allowing for communication

However, the first two choices are essentially changing the premise of the game. Hence, we focus on the other two choices.

## The role of networks in achieving global cooperation

Setting of the game:

1.  Nodes start with attribute $C$ or $D$ (cooperate or defect), random distributed.

2.  In each round, a game is played on each edge, the payoff for node $i$ is then given by $$S_i = \sum_{j=1}^N A_{ij} M_{e_i e_j}$$

3.  Strategy update: pick a random neighbour $j$, if $S_j>S_i$, change to their strategy, i.e. $e_i$ switch to $e_j$

Measure: how cooperation evolves $$\rho(t) = \frac{1}{N} \sum_{i=1}^N \delta\left({e_i=c}\right)(t)$$ The above measures the fraction of the nodes that cooperates at time $t$. Hence if $$\lim_{t\to\infty} \rho(t) = 1 \implies \text{cooperation prevails}$$

Consider a toy model:

At $t=0$, the number of cooperation nodes is approximately the number of defectors. Pick two nodes $x$ that coorerates and $y$ that defects. The degree $z_x = z_y = z$. The payoff of $x$ and $y$:

$$t=0\implies s_x = \frac{z}{2} \cdot 1 + \frac z2 \cdot 0\leq s_y  = \frac z2 b + \frac z2 \cdot 0$$

Initially, the defector hubs are better off. The chance that $x$ switches to $D$ is the chance of copying $y$

For a intermediate $t$, the defector nodes will be copied, and if $x$ resisted the temptation to copy $y$, then its cooperation strategy will be quickly copied by its neighbours. Then the payoff of $x$ would be $$S_x = \left({z-1}\right)\cdot 1 + 0 \geq S_y = b+ \left({z-1}\right)\cdot0$$

<figure>
<p><strong>Figure unavailable in supplied archive: imgs/image.png</strong></p>
</figure>

This time $y$ will copy $x$ and cooperation will prevail.

Initially there is a lot of time for defectors to exploit the situation. But if the cooperators have enough time to create a community that cooperates with themselves, they can succeed in the long run. Hubs facilitate the formation of these communities. Other networks assortative communities may play a similar role.

## Continuous Time dynamical systems

For each node, associate it with a vector-valued function $x_i(t)\colon \mathbb R\to \mathbb R^d$ that evolves according to time $t$. We say $$\frac{dx_i(t)}{dt} = f_i(x_i) + \sum_{j=1}^N A_{i,j} g_i(x_i, x_j)$$ where $f_i\colon \mathbb R^d \to \mathbb R^d$ represents the internal dynamics and $g_i\colon \mathbb R^{2d}\to \mathbb R^d$ are the couplings through the network.

We connect properties of $A_{i,j}$ to the collective behaviour of $x_i(t)$.

We use the simplifications

- $d=1$

- identical internal dynamics $f_i(x_i)=f(x_i)$

- coupling $g(x,x)=0$

Examples include:

1.  Diffusion-like dynamics: $\frac{dx_i}{dt}=\beta\sum_{j=1}^NA_{ij}(x_i-x_j)$

2.  Kuramoto model: $\frac{d\theta}{dt}=\omega_i+\frac{K}{\langle z\rangle}\sum_{j=1}^NA_{ij}\sin(\theta_i-\theta_j)$ for $\theta\in[0,2\pi]$, where $\omega_i$ is the natural frequency of the oscillator. In the model it is typically distributed randomly from an unimodal density function.

### Kuramoto Model and Synchronisation

Define a macroscopic order parameter $r(t)$, such that $$r(t)e^{I\psi(t)}=\frac1N\sum_{j=1}^Ne^{I\theta_j(t)}$$ where $I:=\sqrt{-1}$ is the imaginary number because $i$ is taken by $j$!

- If all $\theta_j$ are independent, then $r(t)=0$

- If all $\theta_j$ are perfectly synchronised, then $r(t) =1$

- $0\leq r\leq 1$ is the phase coherence, partial synchronisation

We are interested in the long term dynamic of $r(t)$, i.e. $$r_\infty = \lim_{t\to\infty} r(t), \qquad \text{ for } N\to\infty$$ Kuramoto was able to show that for all-to-all networks, we see a phase transition curve similar to that of existence of giant component in ER random graph. Let $K_c$ be the critical value for all-to-all networks.

For random graphs with arbitrary distribution, the phase transition happens at $K_c^*$, given by $$K_c^* = K_c\frac{\left\langle{z}\right\rangle}{\left\langle{z^2}\right\rangle}$$

### Linear Stability of fixed point solution

Consider the DE $$\frac{dx_i}{dt}=f(x_i)+\sum_{j=1}^NA_{ij}g(x_i,x_j)$$ with dimension $d=1$. Let $x^*$ be the fixed point. We have $$\frac{dx_i}{dt}=f(x^*)=0\quad\text{for all }(x_i^*=x^*)$$ Then, $g(x,x)=0\implies g(x^*,x^*)=0\implies x^*$ is a fixed point of the coupled dynamics.

Question: how does the stability of $x^*$ depend on $A_{ij}$ in the simplest case where $g(x_i,x_j)=g(x_i)-g(x_j)$?

We consider a small perturbation: let $\vec{x} = \vec{x}^* + \vec{\epsilon}$, then $$\frac{d{x_i}}{dt}=\frac{d(x_i^*+\epsilon_i)}{dt}=\frac{d\epsilon_i}{dt}=f(x^*+\epsilon_i)+\sum_{j=1}^NA_{ij}g(x^*+\epsilon_i,x^*+\epsilon_j)$$

Consider the Taylor expansion around $x^*$: $$\begin{aligned}
\frac{d\epsilon_i}{dt}&\approx f(x^*)+\epsilon_i\underbrace{\frac{df}{dx}(x^*)}_{\equiv\alpha}+\sum_{j=1}^NA_{ij}g(x^*,x^*)+\sum_{j=1}^NA_{ij}\epsilon_i\underbrace{\frac{\partial g}{\partial x_i}(x^*,x^*)}_{\equiv\beta} + \sum_{j=1}^NA_{ij}\epsilon_j\underbrace{\frac{\partial g}{\partial x_j}(x^*,x^*)}_{\equiv\beta} \\
&\approx \alpha\epsilon_i+\epsilon_i\beta\sum_{j=1}^NA_{ij}-\beta \\
&= \alpha\epsilon_i+\beta(\epsilon_iz_i-\sum_{j=1}^NA_{ij}\epsilon_j)\\
&= \alpha\epsilon_i + \beta\sum_{j=1}^N(\delta_{ij}z_i-A_{ij})\epsilon_j
\end{aligned}$$ In vector notation this is $$\frac{d\boldsymbol\epsilon}{dt} \approx (\alpha I + \beta \mathbb L)\boldsymbol{\epsilon}$$ where $I$ is the identity matrix and $\mathbb L = \boldsymbol{z} I - \mathbb A$ is the graph Laplacian. The fixed point $\boldsymbol{x}^*$ is stable if all eigenvalues of $\alpha \mathbb I+ \beta \mathbb L$ are smaller than $0$.

We take that $\vec{v_r}$ is an eigenvector of $\mathbb{L}$ with eigenvalue $\lambda_r$ for granted.

**Proposition 1**. $\vec{v_r}$ is an eigenvector of $\alpha I-\beta\mathbb{L}$ with eigenvalue $(\alpha+\beta\lambda_r)$ for any $\alpha,\beta\in \mathbb{R}$

*Proof.* Follows directly from computation ◻

Hence, the *stability condition* is $$\alpha+\beta\lambda_r>0, \qquad \text{ for all }\lambda_r \text{ eigenvalues of } \mathbb{L}$$ Suppose $\lambda_1\leq\cdots\leq \lambda_N$, the *Master Stability condition* is $\alpha+\beta\lambda_N<$. Therefore, $$\frac{1}{\lambda_N} >\frac{-\beta}\alpha \qquad \text{for }\alpha<0$$ Recall that

- *Properties of the dynamics:* $\alpha = \frac{\hspace{1.5pt}\mathrm{d}{f}}{\hspace{1.5pt}\mathrm{d}{x}}\left({x^*}\right)$, $\beta = \frac{\partial g}{\partial x}\left({x^*,x^*}\right)$

  $\alpha<0$ is the stability of the internal dynamics, a necessary condition for the stability of $x^*$ in the network, but NOT sufficient.

- *Network property:* $\lambda_N$ is the largest eigenvalue of $\mathbb{L}$.
