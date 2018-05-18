Scala Syntax
==============

- When you call the method the parentheses and dots are optional
- The semicolons are optional 
- There is no need to use **return**. Scala is usually able to infer the return types of methods.
- Scala has **default values** for parameters (no need to do overloading)
`def log(message: String, level: String = "INFO") = println(s"$level: $message")`
- **Tuple** is an immutable object sequence created as comma-separated values. i.e. `(1,2,3)` tuple literal (Tuple3)
- **Implicit parameters** are always in definitons of function as last seperate column.
- **Polymorphic function** - (kind of parametric polymorphism) It is also called generic function. `def isSorted[A](as: Array[A], ordered: (A,A) => Boolean): Boolean`
- SCALA’S *==* represents value-based comparison, no matter what the type is (This is ensured by implementing == as final in the class Any)
- `eq` method provides identity-based comparison on references
- **Access Modifier** - default is public, the protected means that only derived classes can access it

### Loop
- `for ( i <- i to 3 ) { ... }`
- `( 1 to 3 ).foreach( ... )` We used the foreach method of the Range class

### Operator Overloading
- Scala has no operators, so operator overloading means overloading symbols like +, etc.

### Scala Classes for Java primitives:
- Classes like `RichInt`, `RichDouble`, `RichBoolean`, and so on are called rich wrapper classes. They provide convenience methods that can be used for classes in Scala that represent the Java primitive types and String.

### Pattern matching
- Works like fancy switch
- Each case in match consist of the pattern

### Variadic function
- Little syntactic sugar for creating and passing a `Seq` of elements explicitly
- It is possible passing more than one argument
- i.e. `func(s: String*)`

### Partial functions
- it is defined with `case` blocks
```scala
scala> List(41, "cat") collect { case i: Int ⇒ i + 1 }
res1: List[Int] = List(42)
```
- Scala has built-in support for partial functions thanks to the `PartialFunction` trait
A PartialFunction must provides a method `isDefinedAt`, which allows the caller of the partial function to know, beforehand, whether the function can return a result for a given input value.

### String
- is simply `java.lang.String`
- The String is automatically converted to `scala.runtime.RichString`. This brings a few useful methods like `capitalize`, `lines`, and `reverse`.
- Three double quotes (`"""…"""`) for creation of String on more lines
- String literals with expresion `val message = s "A discount of $discount% has been applied"`

