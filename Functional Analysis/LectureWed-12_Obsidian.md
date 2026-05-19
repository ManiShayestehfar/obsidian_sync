# Koopman Operators, Ergodicity of Irrational Rotations and von Neumann Ergodic Theorem

## 1 Koopman operators






## 2 Ergodicity of irrational rotations



> [!Proof]
> First, $T_\alpha$ preserves normalized Lebesgue measure. Indeed, under the parametrization $z = e^{2\pi i t}$, $t \in \mathbb R/\mathbb Z$, the map $T_\alpha$ becomes $t \mapsto t + \alpha \pmod 1$. Lebesgue measure on $\mathbb R/\mathbb Z$ is translation-invariant, so $T_\alpha$ preserves $m$.
>
> Let $U : L^2(\mathbb T, m) \to L^2(\mathbb T, m)$ be the Koopman operator $Uf = f \circ T_\alpha$. Thus $(Uf)(z) = f(ze^{2\pi i\alpha})$.
>
> For each $n \in \mathbb Z$, define $e_n(z) = z^n$. The functions $(e_n)_{n \in \mathbb Z}$ form an orthonormal basis of $L^2(\mathbb T, m)$.
>
> We compute the action of $U$ on this basis: $Ue_n(z) = e_n(ze^{2\pi i\alpha}) = (ze^{2\pi i\alpha})^n = e^{2\pi i n\alpha}z^n = e^{2\pi i n\alpha}e_n(z)$.
>
> Now suppose that $f \in L^2(\mathbb T, m)$ is $U$-invariant: $Uf = f$. Write the Fourier expansion $f = \sum_{n \in \mathbb Z} \widehat f(n)e_n$ in $L^2(\mathbb T, m)$, where $\widehat f(n) = \langle f, e_n \rangle$.
>
> Applying $U$ gives
>
> $$
> Uf = \sum_{n \in \mathbb Z} \widehat f(n)e^{2\pi i n\alpha}e_n.
> $$
>
> Since $Uf = f$, uniqueness of Fourier coefficients gives, for every $n \in \mathbb Z$, $e^{2\pi i n\alpha}\widehat f(n) = \widehat f(n)$. Equivalently, $(e^{2\pi i n\alpha} - 1)\widehat f(n) = 0$.
>
> If $n \neq 0$, then $n\alpha \notin \mathbb Z$ because $\alpha$ is irrational. Hence $e^{2\pi i n\alpha} \neq 1$. Therefore $\widehat f(n) = 0$ for every $n \neq 0$.
>
> Thus the only possibly nonzero Fourier coefficient of $f$ is $\widehat f(0)$. Therefore $f = \widehat f(0)e_0$ in $L^2(\mathbb T, m)$. Since $e_0(z) = 1$, the function $f$ is constant almost everywhere.
>
> By the previous proposition, $(\mathbb T, m, T_\alpha)$ is ergodic.

## 3 von Neumann Ergodic Theorem

> [!Theorem] Theorem 2 (von Neumann Mean Ergodic Theorem)
> Let $H$ be a Hilbert space and let $U : H \to H$ be a unitary operator. Define
>
> $$
> A_N := \frac{1}{N}\sum_{n=0}^{N-1} U^n.
> $$
>
> Let $I := \{x \in H : Ux = x\}$ be the space of invariant vectors, and let $P_U$ be the orthogonal projection onto $I$. Then for every $v \in H$, $A_Nv \to P_Uv$ in norm.

> [!Proof]
> Since $I = \ker(I - U)$, the subspace $I$ is closed.
>
> We first show that $I^\perp = \overline{\operatorname{ran}(I - U)}$. Indeed, for every bounded operator $T$ on a Hilbert space, $(\operatorname{ran} T)^\perp = \ker T^*$.
>
> Applying this to $T = I - U$ gives $(\operatorname{ran}(I - U))^\perp = \ker((I - U)^*)$. Since $(I - U)^* = I - U^*$, we obtain $(\operatorname{ran}(I - U))^\perp = \ker(I - U^*)$.
>
> Because $U$ is unitary, $\ker(I - U^*) = \ker(I - U) = I$. Hence $(\operatorname{ran}(I - U))^\perp = I$.
>
> Taking orthogonal complements, $I^\perp = \overline{\operatorname{ran}(I - U)}$.
>
> Now let $v = P_Uv + (v - P_Uv)$. Since $P_Uv \in I$, $A_N(P_Uv) = P_Uv$.
>
> It remains to prove that $A_N(v - P_Uv) \to 0$. Since $v - P_Uv \in I^\perp$, it is enough to prove convergence to $0$ on $\operatorname{ran}(I - U)$.
>
> Let $y = (I - U)z$. Then
>
> $$
> A_Ny = \frac{1}{N}\sum_{n=0}^{N-1} U^n(I - U)z
> = \frac{1}{N}\sum_{n=0}^{N-1}(U^n - U^{n+1})z.
> $$
>
> The sum telescopes:
>
> $$
> \sum_{n=0}^{N-1}(U^n - U^{n+1})z = z - U^Nz.
> $$
>
> Hence $A_Ny = \frac{z - U^Nz}{N}$. Since $U$ is unitary, $\|U^Nz\| = \|z\|$. Therefore
>
> $$
> \|A_Ny\| \leq \frac{2\|z\|}{N} \to 0.
> $$
>
> Thus $A_Ny \to 0$ for every $y \in \operatorname{ran}(I - U)$.
>
> Finally, since $\|A_Nx\| \leq \|x\|$, the convergence extends to the closure $\overline{\operatorname{ran}(I - U)} = I^\perp$. Hence $A_N(v - P_Uv) \to 0$.
>
> Therefore $A_Nv = A_N(P_Uv) + A_N(v - P_Uv) \to P_Uv$. This proves the theorem.
