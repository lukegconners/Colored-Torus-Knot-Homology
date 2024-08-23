# Colored Torus Knot Homology - v1.0
Luke Conners, published 8/14/2024

Last updated: 8/14/2024

## Project Description

This is a program that implements time-efficient computations of (various models of)
exterior-colored HOMFLYPT homology of positive torus knots. Our implementation
first uses the recursion in Theorem 1.7 from [Con23] to compute $$y$$-ified, finite
projector-colored homology, then uses the equivalence proven in Theorem 1.1 of [Con24]
to convert to unreduced, intrinsically-colored homology, then divides by the unknot
invariant to (conjecturally**, from [Wed19], Remark 3.43) convert to reduced homology.

We work in the Sage programming language. All writing and testing was performed in CoCalc.

## Documentation:
The four main functions available in this program are unreduced_hhy(m, n, k),
unreduced_hhh_intr(m, n, k), reduced_hhh_intr(m, n, k), and
hhh_rank(m, n, k). Each takes as input three positive integers $$m, n, k$$
with $$\mathrm{gcd}(m, n) = 1$$. The outputs are invariants of the $$k$$-colored torus
knot $$T(m, n)$$. The first three functions return the unreduced, $$y$$-ified,
finite column projector-colored homology (defined by cabling and insertion as in [Con23]);
the unreduced, intrinsically-colored homology (defined via Rickard complexes);
and the reduced, intrinsically-colored homology** (defined as in [Wed19]), respectively.
Each of these invariants is presented as a rational function in the variables $$a, q, t$$
which records the graded dimension of the given invariant with respect to the Hochschild,
quantum, and homological gradings, respectively, up to an overall normalization.
The function hhh_rank(m, n, k) returns the total rank of the reduced, intrinsically-
colored homology** of $$k$$-colored $$T(m, n)$$ as a positive integer.

**Our method for computing reduced homology proceeds by dividing the graded rank of
unreduced, intrinsic homology by the graded rank of unreduced, intrinsic homology
of the colored unknot. When $$k = 1$$ (i.e. for the trivial coloring), this is known
to produce the graded rank of reduced homology by work of Rasmussen [Ras15,
discussion after Definition 2.14]. The corresponding result in the colored case
is conjectured by Wedrich in [Wed19, Remark 3.43], but to our knowledge, this
conjecture remains open.

## Efficiency Notes:
Because of our implementation of the main recursion, the primary constraint
on large computations is RAM, not time. For example, calling hhh_rank(3, 4, 5)
computes the 5-colored homology of the 8-crossing knot $$T(3, 4)$$ in an
average of 2.8s using 378 MB of RAM; the rank is 161051.
Calling hhh_rank(5, 11, 2) computes the 2-colored homology of the 44-crossing
knot $$T(5, 11)$$ in an average of 18.8s using 716 MB of RAM; the rank is 4133089.
A version of this program with smaller RAM requirements in exchange for a (much)
longer runtime is available upon request.

## References:
- [Con23]: L. Conners, "Row-column mirror symmetry for colored torus knot homology". 2023. To appear in Selecta Mathematica. arXiv: 2303.16271.
- [Con24]: L. Conners, "Fray functors and equivalence of colored HOMFLYPT homologies". 2024. arXiv: 2405.00875.
- [Ras15]: J. Rasmussen, "Some differentials on Khovanov-Rozansky homology". Geometric Topology, 19(6):3031–3104, 2015. arXiv:0607544.
- [Wed19]: P. Wedrich, "Exponential growth of colored HOMFLY-PT homology". Advances in Mathematics, 2019. arXiv: 1602.02769.

If you find this program helpful or wish to report bugs or suggest improvements,
please email the author at lconners [at] live [dot] unc [dot] edu.
