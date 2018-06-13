Functions
====================

- All functions are **objects**, in Scala.
- There is no need to use **return**. Scala is usually able to infer the return types of methods.
- It is possible to define **default value** for parameter of functions (no need to do overloading!)
  - `def log(message: String, level: String = "INFO") = println(s"$level: $message")`
- **Implicit parameters** are always in definitons of function as last seperate column.
- **Implicit function** quietly transform object to object of different type.
  - `implicit def convIntToMyObject(number: Int) = new MyObject(number)`
- **Closure** creates code blocks with variables that are not bound to function.

### Evaluation Strategy
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
- **Trampoline Calls**
  - Scala compiler only detects direct recursions. If two functions call each other, Scala doesn't detec anything.
  - In cases like this where the recursion involves functions calling each other, we can use the `TailRec` class and the functions available in the `scala.util.control.TailCalls` package.
- `def loop: Boolean = loop`, is going to be evaluated always and only once
- `val loop: Boolean = loop`, is going to be evaluated immediately and **won’t terminate**

## Partially Applied Function
- The first bind a value to the date parameter. We use the `_` to leave the second parameter unbound.
```scala
val date = new Date(1420095600000L) 	
val logWithDateBound = log(date, _ : String)
logWithDateBound("message1")
logWithDateBound("message2")
```
- When you create a partially applied function, Scala internally creates a new class with a special apply method.

### Parametrized (Generic) Functions
- The notation `[T]` signals to the compiler that the type `T` that follows is not some existing
- Scala will require that the arguments be of the same type, but there is type `Any` so the call `echo("hi", 5)` will unfortunately work.
  - `def echo[T](input1: T, input2: T) = println(s"got $input1 (${input1.getClass}) $input2 (${input2.getClass})")`
  - `def isSorted[A](as: Array[A], ordered: (A,A) => Boolean): Boolean`

### Partial Function
- It is defined with `case` blocks
```scala
scala> List(41, "cat") collect { case i: Int ⇒ i + 1 }
res1: List[Int] = List(42)
```
- Scala has built-in support for partial functions thanks to the `PartialFunction` trait. A `PartialFunction` must provides a method `isDefinedAt`, which allows the caller of the partial function to know, beforehand, whether the function can return a result for a given input value.

### Variadic Function
- Little syntactic sugar for creating and passing a Seq of elements explicitly
- It is possible passing zero or more than one argument
- i.e. func(s: String*)
