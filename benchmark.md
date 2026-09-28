Benchmark families on the paper:
  - 78 purely univariate from SMTLIB
  - Intermediate univariate problems generated during multivariate coverings
    + TODO: the code that outputs the intermediate problems is done on ufmg-smite/cvc5:gen_univ_benchmarks. It needs to be run on SMTLIB problems.
  - 7 problems from Li's paper?

Modes:
  - Fine grained (Coverings, 5 rules: SGN_INV_INTRO, SGN_INV_ELIM, COVER, RAN_EVAl, IS_ROOT_INTRO)
  - Coarse grained (CAD, 1 rule: ARITH_COVERINGS_UNIV)
  - Descartes?

Which time we use?
  - Type checking (`set_option profiler true`) - just the time to check the proof produced by lean-smt
  - Proof production (custom timers around the code of the `smt` tactic) - just the time to produce the proof
    + We should not measure the time taken for proof rules alone because the fine grained version also relies on AND_ELIM and resolution. We should either measure the full time of the tactic or maybe the time of the tactic minus cvc5's time and maybe translation time...
