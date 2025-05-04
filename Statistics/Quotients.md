Suppose $X,Y$ have a joint density $f_{XY}$ and let $Z= Y/X$.

>[!Quote] Question
>What is the distribution of $Z$? Is it well-defined?

Let $A_z = \{(x,y)\in \mathbb{R}^2 : y/x \leq z\}$, then 
$$F_Z(z) = P(Y/X \leq z) = P((X,Y)\in A_z) = \iint_{A_z} f_{XY}(x,y)\:dx\:dy$$
1. $x>0: (x,y) \in A_z \iff y/x \leq z \iff y \leq z\cdot x$ 
2. $x<0: (x,y) \in A_z \iff y/x \leq z \iff y \geq z\cdot x$

![[Pasted image 20250504102745.png]]

$$F_Z(z) = \int_{x=-\infty}^0 \int_{y=zx}^\infty f_{XY}(x,y)\:dy\:dx \quad+\quad \int_{x=0}^\infty \int_{y=\infty}^{y=zx} f_{XY}(x,y)\:dy\:dx$$
$$\begin{align*}
x>0 \:\:&: \int_{y=\infty}^{y=zx} f_{XY}(x,y)\:dy = \int_{-\infty}^z f_{XY}(x,vx) 
\end{align*}$$