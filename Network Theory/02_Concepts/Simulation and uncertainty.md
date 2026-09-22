---
type: study-note
tags: [DATA5441]
---

# Simulation and uncertainty

[[00_HOME]]

Sources: Tutorials 3–7 and Week 6. These are study clarifications of the simulation workflow.

Use one row per retained observation with step count, statistic and run identifier. Preserve the empirical graph and simulate on copies. Record the seed, model parameters, number of independent runs, number of attempted updates and measurement spacing.

For independent model draws $X_1,\ldots,X_R$, distinguish:

- Ensemble standard deviation $s$: variability of a graph statistic under the model.
- Monte Carlo standard error $s/\sqrt R$: uncertainty in your estimate of the model mean.

Compare a single empirical graph with the **ensemble distribution**, not merely with a very narrow confidence interval for its estimated mean. “Within two standard deviations” is a rough diagnostic, not automatically a calibrated test when the distribution is skewed or parameters were fitted to the same graph.

For a stationary correlated series, a useful approximation is
$$\tau_{int}=1+2\sum_{t\ge1}\rho(t),\qquad R_{eff}\approx R/\tau_{int},\qquad \mathrm{SE}(\bar X)\approx s/\sqrt{R_{eff}}.$$
Autocorrelation estimates themselves can be unstable on short runs. Batch means and independent chains provide useful checks. Thinning reduces correlation between saved samples but does not by itself remove initial bias or guarantee efficiency.

Burn-in removes initial transient observations; it is not a theorem certified by a curve’s knee. A chain can remain in a local region with a flat trace. Compare starts and several statistics. Use a mask such as `frame[frame['time'] >= burn_in_steps]`: indexing rows by an edge count confuses observations with updates when measurements are spaced apart.

To assess graph diameter or average path length, handle disconnectedness explicitly. To estimate a maximum centrality, take the maximum in **each** simulated graph before comparing its distribution to the empirical maximum.
