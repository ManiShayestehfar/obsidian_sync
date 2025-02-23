One can decompose a solid ball in three-dimensional space into a finite number of disjoint subsets and, by applying only rotations and translations (i.e., rigid motions), reassemble these pieces into two solid balls each congruent to the original.

There exists a finite partition of the ball into non-overlapping sets $A_1, A_2, \ldots, A_n$ such that, by appropriately choosing isometries (rotations and translations), one can form two copies of the original ball. Symbolically, if $B$ is the ball, there exist isometries $T_1, T_2, \ldots, T_k$ such that
$$
B = \bigcup_{i=1}^n A_i,
$$
and also
$$
B = \left(\bigcup_{i \in I} T_i(A_i)\right) \cup \left(\bigcup_{j \in J} T_j(A_j)\right),
$$
where $I$ and $J$ are two disjoint index sets partitioning $\{1, \ldots, n\}$.

## Use of the Axiom of Choice

The construction relies on the **axiom of choice** to select points from uncountably many subsets, yielding pieces that are not Lebesgue measurable. This non-measurability is crucial since it sidesteps the usual constraints of volume conservation in classical measure theory.