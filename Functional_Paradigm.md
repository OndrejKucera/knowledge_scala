Functional Paradigm
====================

## Imperative paradigm
mutable variables, assignments, control structure (ifs, loops, returns, breaks, …) -> von Neumann style (John Backus) -> bottleneck 

## Functional paradigm
- First functional language was Lisp in 1959
- Restricted: programming without mutable variables, assignments, loops and other imperatives structures (Pure Lisp, XPath)
- Wider sense: focusing on the functions. **Functions are first-class citizens**. Function can be defined anywhere, function can be passed and returned as a value, functions can be composed by set of operators.
- **Pure function** is without **side effects** (such as reading files or mutating memory). Pure functions are easier to test, reuse, parallelize, generalize, and reason about. Furthermore, pure functions are much less prone to bugs.
- **Side effect** means that function does more than just return value. (i.e. `i++`)
- Why is FP popular: simpler reasoning principles, better modularity, good for parallelism
- Functional programming honors **immutability** and favors **higher-order functions** and **function composition**



- **Higher order function** (HOF) - are functions that take other functions as arguments and may themselves return functions as their output
- **Currying** - function return function which is parameter other function def func(...)(...). One of the main reason using this is to assist with type inference.
- **Referential transparency** - in any program, the expression can be replaced by its result without changing the meaning of the program.
- **Substitution model** is scheme of expression -> idea: reduce an expression to a value (as long as they have no side effects) [Alonzo Church - lambda calculus]


