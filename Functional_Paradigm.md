Functional Paradigm
====================

### Imperative paradigm
- You tell not only what to do, but also how to do it. That’s dictating a low level of details.
- mutable variables, assignments, control structure (ifs, loops, returns, breaks, …) -> von Neumann style (John Backus) -> bottleneck -> extensibility

### Functional paradigm
- First functional language was Lisp in 1959
- Restricted fp: without mutable variables, assignments, loops and other imperatives structures (Pure Lisp, XPath)
- Wider sense: focusing on the functions. **Functions are first-class citizens**. Function can be defined anywhere, function can be passed and returned as a value, functions can be composed by set of operators.
- Why is FP popular: simpler reasoning principles, better modularity, good for parallelism
- Functional programming honors **immutability** and favors **higher-order functions** and **function composition**
- **Higher order function** (HOF)
  - are functions that take other functions as arguments and may themselves return functions as their output
  - reduce code duplication, increase reuse, and make code concise
- **Pure function** is without **side effects** (such as reading files or mutating memory). Pure functions are easier to test, reuse, parallelize, generalize, and reason about. Furthermore, pure functions are much less prone to bugs.
  - **Side effect** means that function does more than just return value. (i.e. `i++`)
- **Currying**
  - Transforms a function that takes more than one parameter into a function that takes multiple parameter lists.
  - function return function which is parameter other function def func(...)(...). One of the main reason using this is to assist with type inference.
- **Referential transparency** - in any program, the expression can be replaced by its result without changing the meaning of the program.
- **Substitution model** is scheme of expression -> idea: reduce an expression to a value (as long as they have no side effects) [Alonzo Church - lambda calculus]

### Evaluation strategy
- We can change the evaluating strategy: from call-by-value to call-by-name
- **Call-by-value** has advantage that it evaluates every function argument only once (Scala normally uses)
- **Call-by-name** has advantage that a function argument is not evaluated if the corresponding parameters is not used in the evaluation of the function body
- Both evaluations reduce to the same final values but only if the function is pure and evaluations terminate.
- You can force it, when you add arrow ( `=>` ) to parameter of function, in Scala
- `def loop: Boolean = loop`, is going to be evaluated always
- `val loop: Boolean = loop`, is going to be evaluated immediately and won’t terminate

