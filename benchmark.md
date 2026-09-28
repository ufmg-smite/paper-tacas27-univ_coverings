12154 QF_NRA problems in SMTLIB

5536 marked with ":status unsat"

Out of the 5536, 2844 got solved before reaching the coverings solver

The remaining 2692: 78 univariate, 2563 multivariate, 51 still timeout after 300s


TODO 1: do the 2844 early solved problems got full proofs, checkable in Lean?
TODO 2: Can the 78 be solved by incremental linearization and or cad? Does incremental linearization produce proofs checkable in lean?
TODO 3: Extract the univariate side conditions for solving the 2563

What happens with the 51? preprocessing for so long? Very big problems, also Brown's heuristic for variable ordering runs before your check
