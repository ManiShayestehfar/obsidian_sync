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
x>0 \:\:&: \int_{y=-\infty}^{y=zx} f_{XY}(x,y)\:dy = \int_{-\infty}^z f_{XY}(x,vx) \:x\:fv \\[5pt]
x < 0 \:\:&: \int_{y=zx}^\infty f_{XY}(x,y)\:dy\:dx = \int_{z}^{-\infty} f_{XY}(x,vx)\:x\:dv = \int_{-\infty}^z f_{XY}(x,vx)\:(-x)\:dv 
\end{align*}$$where $v= y/x$, and both $\pm x = |x|$. Therefore

![[Pasted image 20250504112506.png]]

>[!success] Conclusion
>$\implies Z = Y/X$ is a [[Continuous RV]] with pdf 
>$$f_{Y/X}(z) = f_Z(z) = h(z) = \int_{-\infty}^\infty f_{XY}(x,\underbrace{zx}_{y})|x|\:dx$$
>
>If $X,Y$ are independent then
>$$f_{Y/X}(z) = \int_{-\infty}^\infty f_X(x) f_Y(zx)|x|\:dx$$

- The joint pdf is fairly similar to the [[Conditional Expectation|sum of RVs]] case

# Examples

## Cauchy Distribution

$X,Y$ are iid $N(0,1)$ RVs, $Z=Y/X$.

![[Pasted image 20250504114345.png|600]]

- This is the density of the **Cauchy Distribution** 