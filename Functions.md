Functions
====================

### ??


### Evaluation strategy
- We can change the evaluating strategy: from call-by-value to call-by-name
- **Call-by-value** has advantage that it evaluates every function argument only once (Scala normally uses)
- **Call-by-name** has advantage that a function argument is not evaluated if the corresponding parameters is not used in the evaluation of the function body
- Both evaluations reduce to the same final values but only if the function is pure and evaluations terminate.
- You can force it, when you add arrow ( `=>` ) to parameter of function, in Scala
- `def loop: Boolean = loop`, is going to be evaluated always
- `val loop: Boolean = loop`, is going to be evaluated immediately and won’t terminate

