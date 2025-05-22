We usually deal with jointly distributed RVs that are either discrete $(p_{XY})$, or jointly continuous $(f_{XY})$. But there can also be a mixture of distributions.

# Examples

## Bernoulli

$B \sim \text{Bernoulli}(1/2)$,  $Z$ $\sim N(0,1)$,  and let $X = BZ$  ($X$ is neither discrete nor cont.)

## Uniform

$U \sim U(0,1)$,   $X|U=\rho \sim \text{Binom}(m,\rho)$ 

Let $X_i = \mathbb{1}_{\{\text{success at trial i}\}}$, so $X = \sum_{i=1}^m X_i$.  Note that $X_i | U = \rho \sim \text{Bernoulli}(\rho)$ (independent).

$p_{X|U}(x|u) = \binom{m}{x} u^x(1-u)^{m-x}\cdot \mathbb{1}_{x \in \{0,1,...,m\}}$

So $E(X|U=u) = mu$  and $E(X|U) = mU$. 

## Random Sum
$X_1,...,X_n \sim F_X$ and define $T = \sum_1^N X_i$. In all such cases $F_{XY} = P(X\leq x, Y\leq y)$ is well-defined. 

$F_{T|N}(t|n) = F_{S_n}(t)$ where $S_n = \sum_1^n X_i$, which is true if we change $T=s$ to $T\leq s$ in the proof in [[Random Sums]].

If $X_i \in L^1$ then $E(T|N=n) = nE(X_i)$ and so $E(T|N) = NE(X_i)$.

## Convolution
If the ind. RVs $X_i$ have densities $f_i$ then $\sum_{i=1}^n X_i$ has density $((f_1 \star f_2) \star f_3) ... \star f_n = f_1 \:\star\: ... \:\star\: f_n$.   

If $F_X$ has a density $f_X$ (where $X_i$ are cont. RVs), then $F_{T|N}$ has a density given by
$$f_{S_n} \equiv f_X \:\star \:...\:\star\:f_X$$