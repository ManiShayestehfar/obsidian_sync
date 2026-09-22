---
type: study-note
tags: [DATA5441]
---

# Small worlds and preferential attachment

[[00_HOME]]

Sources: Week 5; Newman §§12.11.8 and 13.1.

Watts–Strogatz modifies a ring with $Q$ neighbours on each side. Shortcuts can strongly reduce distances while many local triangles survive. In the non-wrapping regime $N>3Q$, the $2Q$ neighbours of a vertex contain $3Q(Q-1)/2$ edges, so
$$C(0)=\frac{3Q(Q-1)/2}{\binom{2Q}2}=\frac{3(Q-1)}{2(2Q-1)}.$$
For $Q=2$, this is $1/2$; for $Q=1$, there are no triangles. The approximation $C(p)\approx C(0)(1-p)^3$ counts surviving original triangles and omits other effects.

A lattice with shortcuts demonstrates existence of short routes. Kleinberg’s navigation problem asks whether a local routing procedure can find them. These are different research questions.

Barabási–Albert instead changes the network by growth and preferential attachment. A new vertex brings $m$ edges, giving asymptotic mean degree $2m$. The continuum equation $dk/dt\approx k/(2t)$ leads to $k_i(t)\approx m\sqrt{t/t_i}$, survival tail $\Pr(K\ge k)\approx(m/k)^2$ and density exponent three.

An ER graph matched to a realised BA graph’s edge count uses
$$q=\frac{L_{BA}}{\binom N2};$$
$q\approx2m/(N-1)$ neglects seed corrections. Similar density does not imply similar degree tails or clustering. In a tree-seeded $m=1$ BA model, clustering is zero exactly.

**Model-choice question:** short routes plus local clustering motivate WS; broad degrees through cumulative advantage motivate BA; preserved empirical degrees motivate a configuration null. No single observed signature uniquely identifies its generating mechanism.
