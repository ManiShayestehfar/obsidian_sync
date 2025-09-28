Let $f:I \to X$, $g:I \to X$ be paths such that $f(1)=g(0)$.

# Compositions

>[!def] Composition
>The composition of $f,g$ is the path $f \circ g:I \to X$ given by
>$$(f \circ g)(s) = \begin{cases}
f(2s) & s \in [0,1/2] \\[4pt] 
f(2s-1) & s \in [1/2,1]
\end{cases}$$
- Traverse $f$ at 2x speed, and then $g$ at 2x speed

**Exercise:** If $f_o \simeq f_1$ via $f_t$, and $g_0 \simeq g_1$ via $g_t$, and $f_t(1)=g_t(0)$ for all $t \in I$, then $f_0\circ g_0 \simeq f_1 \circ g_1$ via $f_t \circ g_t$.


