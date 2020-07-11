# maxima-linalg

Some functions for working with functions, matrices and subspaces in
[Maxima](http://maxima.sourceforge.net/). The intended use is in 
[STACK](https://www.ed.ac.uk/maths/stack) questions, so each 
multiline function is followed by a comment containing a version on a single line suitable for pasting into the STACK editor.

Randomisation is not done the STACK way, you may want to change this if
you're using these functions with STACK.

## Methods

### Functions

There are some methods for working with functions from 1..M to 1..N for
some M and N. These are represented as lists of their values, so f
corresponds to `[f(1), f(2), ..., f(M)]`.
- `leftInv(f, N)` returns a left-inverse to the function f with codomain
  `1, 2, ..., N`. Assumes f is one-to-one.
- `differentLeftInv(f, N)` returns a different left-inverse to the one
  found by `leftInv`, assuming that N is larger than M
- `whyNotLinv(f, g, N)` returns a number such that g(f(i)) is not i, or 0 if no such number exists.
- `allInCod(g, cod)` returns true if the image of g is contained in the
  list cod, otherwise false
- `allInCod2(g, cod)` returns a number i such that g(i) is not an
  element of cod if such an i exists, otherwise 0.

### Matrix and vector functions

 - `columnOfLeadingEntry(a, i)` returns the column of `a` in which the left-most nonzero entry of row `i` appears if this exists, otherwise -1.
 - `rref(a)` returns the row reduced echelon form of `a`.
 - `isrref(a)` is true iff `a` is in row reduced echelon form.
 - `isdiag(a)` is true iff `a` is diagonal.
 - Row operations: `lij(a, l, i, j)` adds `l` times row `i` to row `j`, `sw(a, i, j)` swaps rows `i` and `j`, `mu(a, i, l)` multiplies row `i` by `l`.
 - `isLI(v1, v2, ...)` is true iff `v1, v2,...` are linearly independent.
 - `iszeromx(a)` is true iff `a` has all entries zero.
 - `isevec(v, a)` is true iff `v` is an eigenvector of `a`. Assumes `a . v` makes sense and has the same size as `v`.
 - `rpm(n)` returns a random permutation matrix of size n
 - `random_lut_mx(n, maxi)` returns a lower unitriangular matrix with
   entries randomly chosen between `-maxi` and `maxi` inclusive
 - `random_slnz(n, maxi)` returns a random integer nxn matrix with
   determinant 1 formed by `random_lut_mx(n, maxi) . rpm(n) . random_lut_mx(n, maxi)`

There are functions for determining why a matrix is not in RREF:
 - `zeroRowsNotAllAtBottom(a)` returns `true` if there is a zero row
   with a nonzero row below it, otherwise `false`.
 - `nonOneLeadingEntry(a)` returns the coordinates of a leading entry
   which isn't equal to 1 if such an entry exists, otherwise `[-1, -1]`.
 - `nonZeroEntryInColumnOfLeadingEntry(a)` returns the coordinates of a
   leading entry which has a nonzero entry elsewhere in its column if
   such a leading entry exists, otherwise returns `[-1, -1]`.
 - `badLeadingEntryPositions(a)` returns `[i, j]` such that `i < j` but
   the leading entry in row `j` is not to the right of that in row `i`,
   if such a pair exists, otherwise returns `[-1, -1]`.

### Vector space functions

Subspaces U are represented by matrices whose column space is U. A good
convention is that matrices named with capitals represent subspaces and
matrices named in lower case are just matrices.

 - `dim` is an alias for the maxima command `rank`.
 - `equal_subspaces(A, B)` is true iff `A` and `B` represent the same
   subspace.
 - `proj(a)` is orthogonal projection onto the column space of `a`.
 - `kerMX(a)` represents the kernel of the matrix `a`.
 - `sum_subspaces(A, B)` represents the subspace sum.
 - `intersect_subspaces(A, B)` represents `A ∩ B`.
 - `inn(v, A)` is true iff `v` is in (the subspace rep by) `A`.
