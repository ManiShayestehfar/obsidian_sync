We usually deal with jointly distributed RVs that are either discrete $(p_{XY})$, or jointly continuous $(f_{XY})$. But there can also be a mixture of distributions.

# Examples

## Bernoulli

$B \sim \text{Bernoulli}(1/2)$,  $Z$ $\sim N(0,1)$,  and let $X = BZ$  ($X$ is neither discrete nor cont.)

## Uniform

$U \sim U(0,1)$,   $X|U=p \sim \text{Binom}(m,p)$ 

Let $X_i = \mathbb{1}_{\{\text{success at trial i}\}}$, so $X = \sum_{i=1}^m X_i$.  Note that $X_i | U = p \sim \text{Bernoulli}(p)$ (independent).


## Random Sum