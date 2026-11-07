---
tags: [data5441, ch09, inference]
aliases: [Ising reconstruction, Pseudolikelihood, Correlation network]
---
# Reconstruction from node activity

> [!abstract] Summary
> Here the links are unobserved; we observe $T$ snapshots of binary node states. The heuristic approach links the most correlated pairs. The inferential approach fits an Ising model, using the tractable pseudolikelihood because $Z(g)$ is intractable, and samples graphs with Metropolis.
> Chapter: [[Ch09 Network reconstruction]]

> [!definition] Data
> $F=(s_i^{(t)})\in\{-1,+1\}^{T\times N}$: row $t$ is one snapshot of all $N$ node states. In the tutorial, $N=50$, $T=200$, the true $L=100$, $J=0.4$, and $L$ is assumed known.

> [!definition] Heuristic: correlation
> Compute the Pearson correlation $r_{ij}$ of the columns $i$ and $j$ over $t$. Predict the $L$ pairs with the largest $r_{ij}$.

> [!proposition] Chance baseline
> Choosing $L$ of the $Y$ pairs uniformly at random recovers, on average, $L\cdot\dfrac LY=\dfrac{L^2}{Y}$ true links. For $N=50$, $L=100$: $10^4/1225\approx8.2$.

> [!definition] Inferential: Ising model on $g$
> $$P(s\mid g)=\frac{e^{-E_g(s)}}{Z(g)},\qquad E_g(s)=-J\sum_{\{i,j\}\in\mathcal L}s_is_j,\qquad Z(g)=\sum_{s\in\{\pm1\}^N}e^{-E_g(s)} .$$
> $Z(g)$ depends on $g$ and has $2^N$ terms, so the energy alone is not a valid score for comparing graphs.

> [!theorem] Node conditionals and pseudolikelihood
> Let $h_i=J\sum_jA_{ij}s_j$. Then
> $$P(s_i\mid s_{-i},g)=\frac{e^{s_ih_i}}{e^{h_i}+e^{-h_i}}=\frac1{1+e^{-2s_ih_i}},\qquad F_{PL}(g)=\sum_{t=1}^T\sum_{i=1}^N\ln\big(1+e^{-2s_i^{(t)}h_i^{(t)}}\big),$$
> where $F_{PL}$ is the negative log pseudolikelihood $-\ln\prod_{t,i}P(s_i^{(t)}\mid s_{-i}^{(t)},g)$.

> [!proof]-
> With all states other than $s_i$ fixed, $E_g(s)=-s_ih_i+(\text{terms without }s_i)$. Normalising over $s_i=\pm1$ gives $e^{s_ih_i}/(e^{h_i}+e^{-h_i})$. Dividing numerator and denominator by $e^{s_ih_i}$ gives $1/(1+e^{-2s_ih_i})$. $\square$
> The product of conditionals is **not** the joint likelihood. It is a tractable substitute.

> [!algorithm] Graph sampling with fixed $N,L$
> 1. Start from any graph with $L$ links.
> 2. Propose an edge replacement (remove one link, add one non-link); this is symmetric.
> 3. Accept with $\min\{1,e^{-\Delta F_{PL}}\}$.
> 4. After burn-in, keep the samples (including repeats). Evaluate their overlap with the truth only to benchmark.

> [!remark] Observations
> - At $J=0$ every conditional is $1/2$ and $F_{PL}=TN\ln2$, so all graphs are equally likely and the overlap returns to chance.
> - The tutorial's acceptance rate is low ($\sim0.5\%$), so check mixing.
> - In real problems the true graph is unavailable: choose $J$ by a principled fit, not by overlap with the truth.

![[tutorial-9-cell-49-plot-2.png|700]]

> [!selftest]- Self-test
> 1. Why is the pseudolikelihood used? — Because $Z(g)$ is intractable and $g$-dependent.
> 2. What overlap does random guessing give? — $L^2/Y$.

---
Related: [[Link prediction]] · [[Metropolis–Hastings]] · [[Maximum entropy and ERGMs]]
