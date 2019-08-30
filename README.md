# maxima-linalg

Some functions for working with matrices and subspaces in
[Maxima](http://maxima.sourceforge.net/). The intended use is in 
[STACK](https://www.ed.ac.uk/maths/stack) questions, so each 
multiline function is followed by a comment containing a version with no formatting whitespace suitable for pasting into the STACK editor.

## Functions

 - `leadingEntry(a, i)` returns the column of `a` in which the left-most
   nonzero entry of row `i` appears if this exists, otherwise -1.
 - `rref(a)` returns the row reduced echelon form of `a`.
 - `isrref(a)` is true iff `a` is in row reduced echelon form.
 - `isdiag(a)` is true iff `a` is diagonal.
 - Row operations: `lij(a,l,i,j)` adds `l` times row `i` to row `j`,
   `sw(a,i,j)` swaps rows `i` and `j`, `mu(a,i,l)` multiplies row `i` by
   `l`.
 - `isLI(v1, v2, ...)` is true iff `v1, v2,...` are linearly
   independent.
 - `iszeromx(a)` is true iff `a` has all entries zero.
 - `isevec(v,a)` is true iff `v` is an eigenvector of `a`. Assumes `a.v`
   makes sense and has the same size as `v`.

Subspaces U are represented by matrices whose column space is U. A good
convention is that matrices named with capitals represent subspaces and
matrices named in lower case are just matrices.

 - `dim` is an alias for the maxima command `rank`.
 - `equal_subspaces(A,B)` is true iff `A` and `B` represent the same
   subspace.
 - `proj(a)` is orthogonal projection onto the column space of `a`.
 - `kerMX(a)` represents the kernel of the matrix `a`.
 - `sum_subspaces(A,B)` represents the subspace sum.
 - `intersect_subspaces(A,B)` represents `A ∩ B`.
 - `inn(v, A)` is true iff `v` is in (the subspace rep by) `A`.

