Functions
====================

- All functions are **objects**, in Scala.
- There is no need to use **return**. Scala is usually able to infer the return types of methods.
- It is possible to define **default value** for parameter of functions (no need to do overloading!)
  - `def log(message: String, level: String = "INFO") = println(s"$level: $message")`
- **Implicit parameters** are always in definitons of function as last seperate column.
- **Implicit function** quietly transform object to object of different type.
  - `implicit def convIntToMyObject(number: Int) = new MyObject(number)`
- Polymorphic function - (kind of parametric polymorphism) It is also called **generic function**.
  - `def isSorted[A](as: Array[A], ordered: (A,A) => Boolean): Boolean`
- **Closure** creates code blocks with variables that are not bound to function.

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
- Recursive function needs return type in scala. 
- **Tail Call Optimization**
  - Scala automatically compiles the recursion to iterative loops that don’t consume call stack frames for each iteration and avoids the stack-overflow. (@annotation.tailrec)
- `def loop: Boolean = loop`, is going to be evaluated always and only once
- `val loop: Boolean = loop`, is going to be evaluated immediately and **won’t terminate**  
