Functions
====================

### ??


### Evaluation strategy
- We can change the evaluating strategy: from call-by-value to call-by-name
- Both evaluations reduce to the same final values but only if the function is pure and evaluations terminate.
- **Call-by-value** has advantage that it evaluates every function argument only once
  - It is normally uses in Scala `def callByValue(x: Int) = { ... }`
- **Call-by-name** (only when it is used) has advantage that a function argument is not evaluated if the corresponding parameters is not used in the evaluation of the function body
  - You can force it, when you add arrow `=>` to parameter of function, in Scala `def callByName(x: => Int) = { ... }`

### Recursion
- It is solving a problem thanks to subproblems.
- The recursion can cause stack overflow for large input values.
- Function has to have specified return-type
- **Tail Call Optimization**
  - tail recursions - are converted into iterations as a way to avoid the stack overflow issue
- `def loop: Boolean = loop`, is going to be evaluated always and only once
- `val loop: Boolean = loop`, is going to be evaluated immediately and **won’t terminate**  
