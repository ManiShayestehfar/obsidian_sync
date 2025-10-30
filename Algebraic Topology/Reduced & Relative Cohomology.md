# Reduced Cohomology Groups

Recall that for reduced homology we looked at the augmented chain complex
$$\cdots \overset{}{\longrightarrow}C_1(X) \overset{}{\longrightarrow}C_0(X) \overset{\varepsilon}{\longrightarrow}\mathbb{Z}\overset{}{\longrightarrow}0$$
This induced a cochain complex which gives the **reduced cohomology group** $\widetilde{H}^n(X,G)$, where
$$\widetilde{H}^n(X,G)\cong H^n(X,G) \quad\quad\forall n > 0$$
For $n=0:$ $\widetilde{H}^0(X,G)\cong \text{Hom}(\widetilde{H}_0(X),G)$.
This is precisely 
$$\frac{f(n)\text{'s that are constant on path-connected components of $G$}}{\text{im }\varepsilon^*: \text{ constant $f(n)$'s from $X$ to $G$}}$$
$\implies H^0(X,G)\cong \widetilde{H}^0(X,G)\oplus \text{im }\varepsilon^* \cong \widetilde{H}^0(X,G)\oplus G$


# Relative Cohomology Groups

Recall the relative homology chain complex
$$0 \overset{}{\longrightarrow}C_n(A)\overset{i}{\longrightarrow}C_n(X)\overset{j}{\longrightarrow}\underbrace{C_n(X,A)}_{\cong C_n(X)/C_n(A)}\overset{}{\longrightarrow}0$$
Define $C^n(X,A;G) := \text{Hom}(C_n(X,A),G)$ which are $f(n)$'s from singular $n$-simplices in $X$ to $G$ that vanish on simplices in $A$. 

Then "dual-ising" gives the cochain complex
$$0 \overset{}{\longleftarrow}C^n(A) \overset{i^*}{\longleftarrow}C^n(X)\overset{j^*}{\longleftarrow}C^n(X,A)\overset{}{\longleftarrow}0$$
$\implies C^n(X,A;G)$ is a subgroup of $C^n(X;G)$ 
So $\delta:C^n(X,A;G)\to C^{n+1}(X,A;G)$ (restriction to $A$) gives $H^n(X,A;G)$.

 We get the long exact sequence 
$$\cdots \overset{}{\longleftarrow}H^{n+1}(X,A;G)\overset{}{\longleftarrow}H^n(A,G) \overset{}{\longleftarrow}H^n(X,G)\overset{}{\longleftarrow}H^n(X,A;G)\overset{}{\longleftarrow}0$$
and similarly get $\widetilde{H}_0^n(X,A;G)$. So
$$\begin{align*}
\widetilde{H}^n(X,A;G) &\cong H^n(X,A;G) \quad \forall n \\[3pt]
\widetilde{H}^n(X,G) &\cong H^n(X,x_0,G) \quad \text{for some }x_0\in X
\end{align*}$$
This results in a commutative diagram (due to the universal coefficient theorem):

![[Reduced & Relative Cohomology-1761701292735.png|550]]

