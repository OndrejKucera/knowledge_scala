Scala Syntax
==============

- Parentheses and dots are optional
- Scala has **default values** for parameters (no need to do overloading)
`def log(message: String, level: String = "INFO") = println(s"$level: $message")`
- **Tuple** is an immutable object sequence created as comma-separated values. i.e. `(1,2,3)` tuple literal (Tuple3)
- **Implicit parameters** are always in definitons of function as last seperate column.
- **Polymorphic function** - (kind of parametric polymorphism) It is also called generic function. `def isSorted[A](as: Array[A], ordered: (A,A) => Boolean): Boolean`

### Loop
- `for ( i <- i to 3 ) { ... }`
- `( 1 to 3 ).foreach( ... )` We used the foreach method of the Range class

### Scala Classes for Java primitives:
- Classes like `RichInt`, `RichDouble`, `RichBoolean`, and so on are called rich wrapper classes. They provide convenience methods that can be used for classes in Scala that represent the Java primitive types and String.

### Pattern matching
- Works like fancy switch
- Each case in match consist of the pattern

### Variadic function
- Little syntactic sugar for creating and passing a `Seq` of elements explicitly
- It is possible passing more than one argument
- i.e. `func(s: String*)`

### String
- is simply `java.lang.String`
- The String is automatically converted to `scala.runtime.RichString`. This brings a few useful methods like `capitalize`, `lines`, and `reverse`.
- Three double quotes (`"""…"""`) for creation of String on more lines
- String literals with expresion `val message = s "A discount of $discount% has been applied"`

