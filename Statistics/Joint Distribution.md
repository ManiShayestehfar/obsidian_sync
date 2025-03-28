Suppose two measurements $X$ and $Y$ are take for each $\omega \in \Omega$

The join pmf of $X$ and $Y$ is 
$$p_{XY}(x,y) = P(X=x,Y=y)\quad x,y\in \mathbb{R}$$
where $\{X=x, Y=y\} = \{\omega: X(\omega)= x, Y(\omega)=y\}$ .

If $X$ and $Y$ are discrete RV:

![[Pasted image 20250304231100.png|600]]
Similarly
![[Pasted image 20250304231214.png]]

- $p_X$ and $p_Y$ are called the **marginal [[Probability Mass Function|pmf]]**.
- The RV $X$ is [[Independence|independent]] from $Y$ if the [[Distributions|distribution]] of $X$ is the same, regardless of which value $Y$ attains

## Examples

### Simple Example
A fair coin is tossed 3 times

- $\Omega = \{HHT, HTH, ...\}$
- $|\Omega| = 2^3 = 8$ 

Let $X = 1_{\{\text{heads on first toss}\}} = \# \:\: \text{of heads in first toss}$,  $Y = \text{total}\:\#\:\text{of heads}$.

![[Pasted image 20250304231833.png]]

>[!info] Definition
>The **joint pmf factors** of the [[Random Variables| random variables]] $X_1,...,X_n$ is 
>$$p_{X_1,...,X_n}(x_1,...,x_n) = P(X_1=x_1,...,X_n=x_n)$$

>[!tip] Claim 1
>The discrete [[Random Variables| random variables]] $X_1,...,X_n$ are independent if the joint pmf factors:
>$$p_{X_1,...,X_n}(x_1,...,x_n) = p_{X_1}(x_1)...p_{X_n}(x_n)\quad \forall x_1,...,x_n \in \mathbb{R}$$ 



 
