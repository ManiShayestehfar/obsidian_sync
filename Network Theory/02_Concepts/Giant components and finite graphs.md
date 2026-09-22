---
type: study-note
tags: [DATA5441]
---

# Giant components and finite graphs

[[00_HOME]]

Sources: Week 3; Newman §§11.5–11.7, 12.2, 12.6.

In sparse ER with limiting mean degree $c$, early exploration is approximated by a Poisson branching process. If $u$ is its extinction probability,
$$u=e^{c(u-1)},\qquad S=1-u=1-e^{-cS}.$$
The physical solution is the smallest extinction probability, equivalently the largest $S\in[0,1]$. $S=0$ always solves the equation; a positive solution appears for $c>1$. This is the limiting fraction in the giant component, not the probability that the finite graph is connected.

At $c=2$, solving gives $S\approx0.7968$. The remaining vertices still exist outside the giant component. Near the threshold, writing $c=1+\epsilon$ and expanding gives $S\approx2\epsilon$ to leading order. This approximation requires small positive $\epsilon$.

For $c>1$ away from criticality, typical distances within the giant component are logarithmic in $N$. The rough estimate $\log N/\log c$ omits finite-size constants and fails at the critical point. A fixed-degree $k$-regular graph instead has outward branching $k-1$ after the first step. Do not substitute $c-1$ for ER’s Poisson excess-degree mean $c$.

Whole-graph connectivity has a much higher sparse ER scale, around mean degree $\log N$. Thus “has a giant component”, “has short typical routes within it” and “is connected” are distinct claims.

**Numerical pitfall:** iteration of $S\leftarrow1-e^{-cS}$ started exactly at zero stays there even for $c>1$. Use a positive initial value or a root method that separates the nonzero solution. Report $L_{max}/N$ across independent finite graphs when estimating the giant fraction.
