# Gamma Function

Recall the Gamma function for $\alpha >0$,
$$\Gamma(\alpha) = \int_0^\infty x^{\alpha-1}e^{-x} \: dx$$
The integrands $\varphi(x)=x^{\alpha-1}e^{-x}$ has an integrable singularity at $x=0$ for $\alpha\in (0,1)$, and it is integrable at $x= \infty$ for $\alpha \in \mathbb{R}$. 
$$\begin{align*}
\Gamma(\alpha +1) &= \int_0^\infty \underbrace{x^\alpha}_{v}\:\:\underbrace{e^{-x}\:dx}_{du} \tag{$u=-e^{-x}$} \\[4pt]
&= -e^{-x}x^{\alpha}|_0^{\infty} + \int_0^\infty e^{-x}\cdot \alpha x^{\alpha-1}\:dx\\[4pt]
&= 0 + \alpha\int_0^\infty x^{\alpha-1}e^{-x}\:dx \\[4pt]
&= \alpha \Gamma(\alpha)  
\end{align*}$$
- Inductively for $n \in \mathbb{N}_{+1}$ , $\Gamma(n+1) = n!\:\Gamma(1)$. 
- Since $\Gamma(1) = \int_0^\infty e^{-x}\:dx = 1$, then $\forall n \in \mathbb{N}$, 
	$$\Gamma(n+1) = n!$$
$$\text{Stirling's Formula}: \quad n! \sim \sqrt{2\pi n}\:\left(\frac{n}{e}\right)^n$$

# Gamma Distribution

>[!info] Definition
>The **Gamma Distribution** is a 2-parameter family of distributions defined by pdf
>$$f_{\lambda,\alpha}(x) = \frac{\lambda^\alpha x^{\alpha -1} e^{-\lambda x}}{\Gamma(\alpha)} \cdot \mathbb{1}_{x\geq 0}$$
>where $\alpha > 0$ is the *shape* parameter, and $\lambda > 0$ is the *rate* parameter.