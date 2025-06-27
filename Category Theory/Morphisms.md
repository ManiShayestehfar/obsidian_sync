# Isomorphisms
Let $(f:X\to Y) \in \bf C$.

$f$ is an **isomorphism** if there exists a $(g:Y\to X) \in \bf C$ such that
$$gf=\text{id}_X \quad,\quad fg=\text{id}_Y$$

>[!lemma] 
>If $f \in \bf C$ is an isomorphism, then $g$ (as defined above) is unique and both monic and epic. 

# Monomorphism (aka Monic)

$f$ is a **monomorphism** if it is *left-cancellative*, i.e. $$fh = fi \implies h=i \quad\quad \forall h,i \in \bf C$$
# Epimorphism (aka Epic)

$f$ is an **epimorphism** if it is *right-cancellative*, i.e. $$hf=if \implies h = i \quad\quad \forall h,i\in \bf{C}$$
# Subobject
$X,Y \in \bf C$. 
$X$ is the **subobject** of $Y$, denoted $X \hookrightarrow Y$ , if there exists a *monic* morphism $f: X\to Y$ 

# Quotient
$X,Y \in \bf C$. 
$X$ is the **quotient** of $Y$, denoted $X \twoheadrightarrow Y$, if there exists an *epic* morphism $f:X \to Y$ 

## Subquotient
$X,Y,Z \in \bf C$.
$X$ is the **subquotient** of $Z$ if there exists a sequence $X \twoheadleftarrow Y \hookrightarrow Z$.
- $X$ is a quotient of a subobject of $Z$. 


