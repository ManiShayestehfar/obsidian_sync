---
type: student-source
week: 11
status: supplementary-unverified-source
---

# Student notes - Week 11

[[Student notes index]] · [[Corrections and caveats]]

> [!warning] Secondary source
> Format conversion of Jeny Yuan’s supplied LaTeX notes (identified by the user as last year’s notes). Mathematical errors in the source are retained here, not endorsed. Use the checked 2026 lecture notes for Weeks 1–7. No 2026 lecture PDF or tutorial for this week was supplied. Missing figures are labelled. Formatting has been normalised; the original TeX is retained in `06_Sources/student_notes_original.tex`.

**Goal:** connect the network structure properties to dynamical properties over the networks.

**Setting:** we have a state $\phi_i(t)$ of node $i$ that evolves over time and depends on $\phi_j(t^*)$ for $A_{i,j}\neq 0$ and $t^* \leq t$.

# General Setting, Binary Models

Consider a *sparse simple* graph $g$ with $N$ nodes, and let $k_i$ be the degree of node $i$. The on/off state is denoted $\phi_i\in[0,1]$. Nodes will change from state 0 to state 1 with rate (probability per unit of time) $F$, and from 1 to 0 with rate $R$. The rates depend on $k_i$ and on $m_i=\sum_{i=1}^N A_{ij}\phi_j$, the number of neighbours in $\phi=1$. (Binary state dynamics)

The main quantity of interest is how many nodes in the network.

- $\rho(t)=\frac{1}{N} \sum_{i=1}^N \phi_i(t)$ ie the fraction of nodes in state $1$ as $\to \infty$.

Some examples:

- Voter Models: probability of switching is $m/k$ or $1-m / k$ proportional to the fraction of the $m$ neighbours with the opposite opinion

- Majority vote with $Q=0$ update to the opinion of most of your neighbours.

Consider the case of a large random graph with high polarisation. We want to know if consensus is achieved as $t\to\infty$, that is $$\lim_{t\to \infty} \rho(t) = 1 \text{ or } 0$$ Consider SI, SIS models ($S$ is susceptible, denote 0, $I$ is infected , denote 1) We want to consider $\rho_\infty$ where $\rho_\infty = 0$ means there is no infection/outbreak and $\rho_\infty =1$ means all are infected

## Methods to Investigate Dynamics on Networks

### Direct Numerical Simulations

A specific update rule needs to be specified to fully define the model.

- Synchronous update: all nodes have their states updated at the same time ($t\to t+\Delta t$).

- Alternatively, we can update asynchronously in which case one node is updated at each time step. This is a different way of counting time ($t'\to t'+\Delta t'$ where $N\Delta t'=\Delta t$). We can select nodes randomly or sequentially.

### Approximating Through Differential Equations

As $N\to \infty$, we have $\Delta t = 1\implies \Delta t' = dt = \frac1N$ in the asynchronous case. Then $\rho(t)=\sum_{i=1}^N\frac{\phi_i(t)}{N}$.

The order 0 approximation/mean-field approximation is (for degree class $k$) $$\frac{d}{dt}\rho_k=-\rho_k\sum_{m=0}^k R_{k,m}B_{k,m}(\omega)+(1-\rho_k)\sum_{m=0}^k F_{k,m}B_{k,m}(\omega) \quad$$ where recall $R_{k,m}$ and $F_{k,m}$ are transition probabilities, $\rho_k(0)=\rho(0)$ is the initial condition, and $$B_{k,m}(q)=\binom k m q^m(1-q)^{k-m}$$ If $\omega\equiv$ probability of a node being infected $=\langle\frac{k\rho_k}{\langle k \rangle}\rangle$.

Key simplifying assumption: no correlation between the state of a node and the state of the neighbours. In sparse random graphs models we can often use the mean-field approximation

## Cascades

In particular, cascades of failures or innovation spreading. For example

- Blackouts in power-grids

- Adaptation of innovations

- Spreading of memes like 6 7 (-Eduardo G. Altmann (with the hand signs))

Threshold model (watts, PNAS 2002) Initial condition $\phi_i(0) =0$ for almost all nodes $i$ $$\phi_i(t+1) =\begin{cases}
        1 & \text{if } \frac{m_i}{k_i}>q_i\\
        0 & \text{else}
    \end{cases}$$ here $m_i/k_i \equiv$ fraction of neighbours who adopted and $q_j \equiv$ parameter for threshold adoption, fixed in $t$ for each $i$. In simulation will be drawn iid from some distribution $f(q)$. We are interested in $\rho_\infty = \lim_{t\to\infty} \frac 1 N \sum_{i=1}^N\phi_i(t)$. For $N\to\infty$ we are interested in two cases:

- $\rho_\infty=0$, no cascade

- $\rho_\infty>0$, global cascade

A **vulnerable node** is a node $i$ for which $\frac{1}{k_i}>q_i$ (aka a node susceptible to infection with 6 7). A sufficient condition for a *global cascade* in the threshold model is to have the vulnerable nodes percolate through the network.

The fraction of nodes with degree $k$ that are vulnerable is $\rho_kP(k)$, where $$\rho_k=\mathbb{P}_F\left(q< \frac 1 k\right), \qquad F(q)=\int_0^qf(q^*)dq^*$$ Last week we saw that $$\frac{\langle k^2\rangle_{\text{vulnerable}}}{\langle k\rangle_{\text{vulnerable}}} = \frac{\sum_{k=1}^\infty k^2\rho_kP(k)}{\sum_{k=1}^\infty k\rho_kP(k)}\geq 2$$ is a sufficient condition for a cascade in a RG model with $P(k)$.

## Epidemic Spreading

**SIS (Susceptible, Infected, Susceptible) model:**

When the susceptible nodes interact with the infected nodes, then they can become infected too. So we go from `SI` pair to `II` configuration. This happens with a rate $\lambda$. However, an infected node recovers spontaneously with rate $\mu$.

**SIR (Susceptible, Infected, Recovered) model**

Nodes which recently recover from infection shouldn’t get infected for some time, because of some immunity. Now we have state `I` transitions to $\verb|R|$ (recovery state) with rate $\mu$. Once you have recovered you do not take part of the epidemic (can’t get sick again).

We are interested in $N\to \infty$, $\langle z\rangle = \text{``const."}$ with random graph interactions. We are looking for equations for $$\begin{cases}
    s &\equiv \frac{\#\text{ of nodes with $\phi_i = S$} }{N} \\
    r &\equiv \frac{\#\text{ of nodes with $\phi_i = R$}}{N} \\
    \rho &\equiv \frac{\#\text{ of nodes with $\phi_i = I$}}{N}
\end{cases}$$ Note that $s+r+\rho=1$ for all $t$.

We use an order $0$ Mean Field Approximation where susceptible nodes meet other nodes by chance.

Nodes have a typical number of connections $\langle z\rangle$. We take $$\text{Contacts to infected nodes per unit of time} = \langle z\rangle \rho$$ Then we have the 3 ODEs $$\begin{cases}
    \frac{ds}{dt} &= -\lambda s\underbrace{\langle z  \rangle \rho}_{\text{rate of decay} }\\
    \frac{d\rho}{dt} &=  \lambda s\underbrace{\langle z  \rangle \rho}_{\text{rate of decay} } - \mu \rho\\
    \frac{dr}{dt} &= \mu\rho
\end{cases}$$ where we note that $\rho+s+r=1$ for all $t$, and that $\frac{d}{dt}(\rho+s+r)=0$. We have the initial conditions $$\begin{cases}
    \rho(t=0)&=1-S_0 \ll 1 \\
    s(t=0)&=S_0\approx 1 \\
    r(t=0)&=0
\end{cases}$$ At time $t\to \infty$ the number of infectious will be zero, and the number of susceptible and recovered should stabilise.

Let’s solve $$\frac{ds}{dr} = -\frac{\lambda \langle z\rangle}{\mu} s \implies s(r) = s_0\exp \left(-\frac{\lambda \langle z\rangle}{\mu} r\right)$$ is a linear separable ODE.

We have the general solution $$s=s_0 e^{-\frac{\lambda\langle z\rangle}{\mu}r}$$ and particular solution $$s(0)=s_0\approx 1 \quad\text{and}\quad r(0)=0 \implies s(r)=e^{-\frac{\lambda\langle z\rangle}{\mu}r}$$ for $t\to\infty$, $$s(r)\to s_\infty=e^{-\frac{\lambda\langle z\rangle}{\mu}r_\infty}$$ Since $r+s+\rho = 1$ where $\rho_\infty\to 0$, we have an implicit solution for $r_{\infty}$ given by $$r_\infty = 1-s_\infty = 1- \exp\left({-\frac{\lambda\langle z\rangle}{\mu}r_\infty}\right)$$ This is akin to the problem of finding a giant component in Poisson random graph, see end of [[Student notes - Week 03|source cross-reference: section:wk3_networkModels]]. The condition for the existence of the non-trivial solution (epidemic) is that $$\left.\frac{d \text{RHS}}{dr_\infty}\right|_{r_\infty=0}>1 \implies \frac \lambda \mu > \frac{1}{\langle z\rangle}$$ which makes $\frac{\lambda}{\mu}=\frac{1}{\langle z\rangle}$ an **epidemic threshold**.

Now let’s consider whether we can include degree variability in the model. The order 1 mean-field approximation is as such:

- RG with a fixed degree distribution $P(z)$

- Each degree class $z$ is treated separately

That is, the SIR are given by $$\left\{{s(t),\rho(t),r(t)}\right\} = \sum_{z=1}^{z_{\max}} P(z) \left\{{s_z(t),\rho_z(t),r_z(t)}\right\}$$ The number of connections to infected nodes per time unit is $$\theta(t) = \sum_{z=1}^{z_{\max}} P(z)\frac{z\rho_z(t)}{\left\langle{z}\right\rangle}$$ Then the ODEs become $$\begin{cases}
    \frac{ds_z}{dt} &= -\lambda s_z z\theta(t) \\
    \frac{d\rho_z}{dt} &= \lambda s_z z\theta(t)-\mu\rho_z \\
    \frac{dr_z}{dt} &= \mu\rho_z
\end{cases}$$ with the same initial conditions for $s_z,\rho_z,r_z$ for all $z$. So as before, we write $$s(t)=e^{-\lambda z\int\theta(t)dt}$$ and the condition for the existence of a non-trivial solution is $$\frac{\lambda}{\mu} > \frac{\langle z\rangle}{\langle z^2\rangle}$$

There is a connection to Percolation

1.  Each node is "ON" infectious for a time $T\sim 1/\mu$

2.  Probability of transmission ot a neighbour $$p=1-(1-\lambda dt)^{T/dt} \approx 1-e^{-\lambda dt T/dt} \approx \lambda / \mu$$ where $\lambda / \mu \approx 0$.

From last week, we derived the critical percolation threshold is give by $$p_c =\frac{1}{\frac{\left\langle{z^2}\right\rangle}{\left\langle{z}\right\rangle}-1} \approx \frac{\left\langle{z}\right\rangle}{\left\langle{z^2}\right\rangle} \qquad \text{for } \left\langle{z^2}\right\rangle \gg \left\langle{z}\right\rangle$$ Since $p\approx \frac{\lambda}{\mu}>p_c \approx \frac{\left\langle{z}\right\rangle}{\left\langle{z^2}\right\rangle} \implies \frac{\lambda}{\mu} > \frac{\left\langle{z}\right\rangle}{\left\langle{z^2}\right\rangle}$

Key idea: for a scale free network, there is an infinite second moment, so as $N\to\infty$ there is no epidemic threshold ($\frac{\left\langle{z}\right\rangle}{\left\langle{z^2}\right\rangle}\to0$), so all viruses lead to an outbreak (there exist super-spreader individuals).
