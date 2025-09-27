>[!def] CW Complex
>A cell complex for a **CW Complex** is a topological space $X$ constructed as follows:
>1. Start with a discrete set $X^0$, whose point are $0-$cells
>2. Inductively, form the **$n$-skeleton** $X^n$ from $X^{n-1}$ by attaching $n$-cells $e^n_\alpha$ via maps $\varphi_\alpha:S^{n-1} \to X^{n-1}$. This means that $X^n$ is the quotient space of the disjoint union $X^{n-1} \sqcup_\alpha D^n_\alpha$ of $X^{n-1}$ with a collection of $n$-discs $D^n_\alpha$ under the identifications $x \sim \varphi_\alpha(x)$ for $x \in \partial D_\alpha^n$. Thus as a set $X^n= X^{n-1} \sqcup_\alpha e_\alpha^n$ where each $e_\alpha^n$ is an open $n$-disc.
>3. Can either stop this inductive process at a finite stage, setting $X = X^n$ for some $n<\infty$, or one can continue indefinitely, setting $X=\cup _n X^n$. In the latter case $X$ is given the weak topology: A set $A \subset X$ is open (or closed) if and only if $A \cap X^n$ is open (or closed) in $X^n$ for each $n$.



