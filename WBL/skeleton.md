Extended abstract

Join 1 and 2?

1 paragraph
  - Present NRA and applications
  - Present CAD as the main complete method for solving problems in this theory.

2 paragraph
  - Present SMT solvers and say that they use variants of CAD to solve NRA, such as CAlC and NLSAT. This work focuses on CAlC, which is the method used by cvc5

3 paragraph
  - Say that these algorithms are intricate and their correctness argument rely on deep mathematical
  results. Errors have been found (link to cvc5 CAlC issues). So far no way to produce results
  verified in a foundational way (as in, inside a proof assistant) of the main algorithm. For the
  univariate case there is a work that reconstructs certificates produced by Mathematica in
  Isabelle/HOL, but it requires rerunning a significant part of the algorithm inside Isabelle
  (discuss Certified vs Certifying?). For the multivariate case, there have been attempts [Mahboubi,
  Vermande] of proving the correctness of an implementation of the algorithm in a proof assistant,
  but none of them is currently usable. More recently, Nalbach [reference] presented a proof calculus
  that is expressive enough to represent the reasoning made by CAD and its variants {but it was not implemented}.
  In this work we present an implementation of the rules in his calculus for the univariate case and
  the Coverings algorithm, with proof reconstruction via lean-smt.
