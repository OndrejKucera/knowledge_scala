Scala Syntax
==============

- Scala has **default values** for parameters (no need to do overloading)
`def log(message: String, level: String = "INFO") = println(s"$level: $message")`
- **Tuple** is an immutable object sequence created as comma-separated values. i.e. `(1,2,3)` tuple literal (Tuple3)
- **Implicit parameters** are always in definitons of function as last seperate column.
- **Polymorphic function** - (kind of parametric polymorphism) It is also called generic function. `def isSorted[A](as: Array[A], ordered: (A,A) => Boolean): Boolean`

## Pattern matching
- Works like fancy switch
- Each case in match consist of the pattern

## Variadic function
- Little syntactic sugar for creating and passing a `Seq` of elements explicitly
- It is possible passing more than one argument
- i.e. `func(s: String*)`
