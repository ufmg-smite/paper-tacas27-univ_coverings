Extended abstract

Join 1 and 2?

\section{Introduction}

Paragraph 1
  - Present NRA and applications
  - Present CAD as the main complete method for solving problems in this theory.

Paragraph 2
  - Present SMT solvers and say that they use variants of CAD to solve NRA, such as CAlC and NLSAT. This work focuses on CAlC, which is the method used by cvc5

Paragraph 3
  - Say that these algorithms are intricate and their correctness argument rely on deep mathematical
  results. Errors have been found (link to cvc5 CAlC issues). So far no way to produce results
  verified in a foundational way (as in, inside a proof assistant) of the main algorithm. For the
  univariate case there is a work that reconstructs certificates produced by Mathematica in
  Isabelle/HOL, but it requires rerunning a significant part of the algorithm inside Isabelle
  (discuss Certified vs Certifying?). For the multivariate case, there have been attempts [Mahboubi,
  Vermande] of proving the correctness of an implementation of the algorithm in a proof assistant,
  but none of them is currently usable. More recently, Nalbach [reference] presented a proof calculus
  that is expressive enough to represent the reasoning made by CAD and its variants {but it was not implemented}.
  In this work we present an implementation of a simplified version of his rules, adapted to the univariate case of
  the Coverings algorithm, with proof reconstruction via lean-smt. In addition to being the first step towards
  an implementation of the complete calculus, this makes cvc5 the first SMT solver capable of emitting proofs
  for this theory.

\section{How it works?}

Paragraph 4
  - The problem we're dealing with is the following: given a set of constraints of the form $P \bowtie 0$, where P is a univariate polynomial,
  whose variable `x` range over the real numbers, decide whether there is a value for `x` satisfying all constraints simultaneously (mention
  that we can handle other logical structures automatically since we're on an SMT solver?). To solve such problems, the Cylindrical Algebraic
  Decomposition algorithm proceeds by computing all the roots of all the polynomials in the lists of constraints and sorts them. The algorithm
  can thus infer that between any pair of consecutive roots all the polynomials are sign invariant, and thus all the constraints are truth invariant.
  Therefore, it is sufficient to select a single point in each interval and computationally check the validity of the formula at such point.
  In contrast, the coverings algorithm considers each polynomial separately and computes, for its constraint, the set of intervals in the real
  line for which the constraint would be violated. Then, it checks if the union of the set of intervals of all the polynomials cover the whole line.

Paragraph 5
  - Explain how the Isabelle work (at some point we need to make clear that this is our main competitor here) was based on the original CAD algorithm,
  and how their monolithic certificate was checked. Explain that in our version we are based on the coverings algorithm, which is more efficient since
  don't need to do the quadratic thing of iterating through pairs of polynomials and intervals, and we tend to end up with less intervals, since we can
  rendundant intervals from the set computed by cvc5. We also need to rely on Sturm-Tarski only on very rare cases, as the endpoint is always a root,
  and usually the algebraic number representing the endpoint is formed by a tuple <p, l, r> and p is a factor of the polynomial in question (but this
  needs to come after the next paragraph, where we talk about sturm tarski and algebraic numbers).

\section{Evaluation}

\section{Future wor}
