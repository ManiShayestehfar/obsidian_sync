# Week 1

2. Example of ring $R$ with zero divisors that are not nilpotent: $\mathbb{Z}/n\mathbb{Z}$ where $n$ is not prime
3. $a,b \in \mathbb{Z}_+$, then 
  $$(a) + (b) = (d) \iff f = \gcd(a,b)$$
4. $R$ and integral domain, then$$R[x]\text{\: is an ID}\implies R[x]\text{\: is an ID}\implies R[x_1,...,x_n]\text{\: is an ID}$$
5. 

|                 |       Prime Ideal        |    Maximal Ideal    |
| :-------------: | :----------------------: | :-----------------: |
| $\mathbb{C}[x]$ |       $(0), (x-c)$       |       $(x-c)$       |
| $\mathbb{R}[x]$ | $(0), (x-c), (x^2+bx+c)$ | $(x-c), (x^2+bx+c)$ |

6.  $K[x]$ is a PID $\iff$ $K$ a field

7. $R$ a ring. $x\in R$ nilpotent and $u \in R$ a unit. then $x+u$ is a unit.

8. $f = a_0+a_1x+...+a_nx^n \in R[x]$. Then $f$ is a unit $\iff$ $a_0$ a unit and $a_1,...,a_n$ are nilpotent

9. $f = \sum_{k=0}^\infty a_kx^k \in R [[x]]$ 

10. $\mathbb{R}[[x]]$ is a local ring

11. $p \in \mathbb{Z}$ prime, then $\mathbb{Z}/p^n\mathbb{Z}$ for $n\geq 1$ is a local ring with residue field $\mathbb{Z}/p\mathbb{Z}$.

12. $x \in R$ is *idempotent* if $x^2= x$. If $R$ is a local ring, then the only idempotents are $x=0,1$.


# Week 2

1. $R$ has exactly one prime ideal $\iff$ All elements of $R$ units or nilpotent $\iff$
	$R/N$ is a field

2. a) $K[[x]]$ is a PID with all ideals in the form $I = (x^m)$ for some $m\geq 1$.
	b) $Nilrad(K[[x]]) = 0$ but $J(K[[x]]) = (x)$. They are not equal and not both equal to zero.

3. -

| $R$                       | $Nilrad(R)$              | $J(R)$                   |
| ------------------------- | ------------------------ | ------------------------ |
| $K[x]/(x^3)$              | $(x)/(x^3)$              | $(x)/(x^3)$              |
| $\mathbb{Z}/18\mathbb{Z}$ | $\mathbb{Z}/6\mathbb{Z}$ | $\mathbb{Z}/6\mathbb{Z}$ |
Using correspondence thm is useful here

4. $J,K,L \leq R$. Then the properties below hold:
![[Commutative Algebra-1755428989278.png|400]]
5. None

6. $I,J \leq R$. Then the properties below hold:
![[Commutative Algebra-1755429068387.png|450]]

7. $I,J \leq R$. If $\sqrt{I}, \sqrt{J}$ are coprime (i.e. $\sqrt{I} + \sqrt{J} = R$), then $I,J$ are coprime as well.

8. $I_1,I_2 \leq R$, $J_1,J_2 \leq S$ and we have homomorphism $f: R \to S$. Then the properties below hold:
![[Commutative Algebra-1755429331874.png|350]]

