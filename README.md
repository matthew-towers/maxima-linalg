# maxima-linalg

Some functions for working with matrices and subspaces in
[Maxima](http://maxima.sourceforge.net/) aimed at use with
[STACK](https://www.ed.ac.uk/maths/stack). For the row reduced echelon
form function, see [Rosetta
Code](https://rosettacode.org/wiki/Reduced_row_echelon_form#Maxima
).

 - `isrref(a)` is true iff `a` is in row reduced echelon form
 - `isdiag(a)` is true iff `a` is diagonal.
 - Row operations: `lij(a,l,i,j)` adds `l` times row `i` to row `j`,
   `sw(a,i,j)` swaps rows `i` and `j`, `mu(a,i,l)` multiplies row `i` by
   `l`.
 - `isLI(v1, v2, ...)` is true iff `v1, v2,...` are linearly
   independent.

Subspaces $U$ are represented by matrices whose column space is $U$.

 - `equal_subspaces(a,b)` is true iff `a` and `b` represent the same
   subspace
 - `proj(a)` is orthogonal projection onto the column space of `a`
 - `kerMX(a)` represents the kernel of the matrix `a`
 - `sum_subspaces(a,b)` represents the subspace sum
 - `intersect_subspaces(a,b)` represents $a \cap b$
 - `inn(v, a)` is true iff $v \in a$


