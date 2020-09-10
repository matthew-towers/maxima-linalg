# maxima-linalg

Code for working with functions, relations, permutations, logic,
matrices and subspaces in [Maxima](http://maxima.sourceforge.net/). The
intended use is in [STACK](https://www.ed.ac.uk/maths/stack) questions,
so STACK random functions are used - these won't work in an ordinary
Maxima session. Either change the randomisation functions back to
standard Maxima ones or follow [the STACK Maxima sandbox
instructions](https://stack2.maths.ed.ac.uk/demo2018/question/type/stack/doc/doc.php/CAS/STACK-Maxima_sandbox.md).

## Methods

### Number theory

- `gcd_calc(a, b)` returns a LaTeX representation of a calculation of
  gcd(a, b) using Euclid's algorithm.

### Permutations
Methods for working with permutations of sets 1..N represented either as
lists `[s(1),...,s(N)]` (i.e. as the bottom row of two-row notation) or
as lists of cycles, where the cycle `(a1,... an)` is represented as a
list `[a1,...,an]`. There are built in maxima functions for working with
permutations in the combinatorics package, but they're not enabled by
default in a STACK maxima installation.

- `cyclesTo2Row(cycs, N)` converts from a list of *disjoint* cycles to the two-row
  rep
- `cyclesTo2Row2(cycs, N)` converts from a list of possibly non-disjoint cycles to the two-row rep
- `cycleTo2Row(cycle, N)` converts a cycle to its two-row rep as a
  permutation of 1..N
- `id_tworow(N)` returns the two-row rep of the identity permutation on
  1..N
- `foldr(list, fn, default)` is right fold
- `twoRowToCycles(tworow)` converts from two-row to disjoint-cycle reps
- `disjointCyclesp(cycs)` checks if the cycles in the list cycs are
  disjoint
- `cyclep(li, N)` checks if li is legitimate cycle on 1..N
- `permAsCycsp(li, N)` checks if li is a list of legitimate cycles on
  1..N
- `order_dj_cycs(cycs)` returns the order of the permutation represented
  by the list of *disjoint* cycles cycs
- `order_tworow(tworow)` returns the order of the permutation tworow
  given in two-row form
- `inverseCycles(cycs)` returns the inverse of the permutation
  represented by the list of possibly non-disjoint cycles cycs, again in
  cycle form
- `sgn_cycles(cycs)` returns the sign of the permutation represented by
  the list of possibly non-disjoint cycles cycs
- `sgn_tworow(tworow)` returns the sign of the permutation tworow given in
  two-row notation
- `compose_tworow(tr1, tr2)` composes the two permutations tr1 and tr2
  given in two-row form
- `compose_cycs(c1, c2, N)` composes the two permutations c1 and c2 of
  1..N given as lists of possibly non-disjoint cycles
- `power_tworow(tworow, n)` returns the nth power of the permutation
  tworow in two-row form, for integer n
- `cycles_to_transpositiosn(cycs)` converts a list of possibly
  non-disjoint cycles to a list of transpositions whose product is the
  same as the product of the original list
- `twoRowLaTeX(tworow)` produces a string consisting of a LaTeX
  representation of the two-row notation for `tworow`
- `cyclesLaTeX(cycs)` produces a string consisting of a LaTeX
  representation of the list of disjoint cycles `cycs`

### Functions and relations

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
- `partitions(n, k)` returns the list of all partitions of n into at
  most k parts.
- `rand_setpartition(n)` picks a set partition of 1..n at random.
- `set_pn_as_table(p, n)` returns an HTML table with `n` labelled rows and columns
  and an x in row i and column j iff i and j are related under the
  equivalence relation on 1..n corresponding to the set partition `p` of
  1..n.

### Matrices and vectors

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
 - `rand_mx_distinct(nrows, ncols)` returns a nrows by ncols matrix with
   randomly chosen distinct entries.
 - `rand_mx(nrows, ncols, a)` returns a nrows by ncols matrix with
   random integer entries between `-a` and `a`
 - `work_out_product_entry(A, B, i, j)` returns a LaTeX string showing
   the calculation of the i, j entry of AB.
 - `small_vector_in_image(A, maxi)` returns a vector in the column space
   of the matrix `A`, with `maxi` controlling how big its entries are.
 - `vector_not_in_image(A)` returns a vector not in the column space of
   `A`.
 - `clear_denoms(mx)` multiplies a rational matrix by the lcm of its
   entries.
 - `random_with_rank(m, n, r, maxi)` returns a random m by n integer matrix with
   rank r (assuming r is at most the minimum of m and n). `maxi` gives
   rough control over how big the elements of the matrix are.
 
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
 - `why_not_rref(mx)` returns a string consisting of an html `<p>`
   containing a `<ul>` whose items describe why `mx` is not in RREF.

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

### Logic

- `log_equiv(ex, fn, vars)` ex is assumed to be a logical expression in
  the variables in the list vars only, and fn is a boolean function with
  arity the length of vars. Returns a list `[is_equiv, counterexamples]`
  where `is_equiv` is a boolean which is true iff `ex` is logically
  equivalent to `fn` and `counterexamples` is a list of the truth
  assignments to `vars` that witness the failure of `ex` to be logically
  equivalent to `fn`
