Scala Syntax
==============

- When you call the method the parentheses and dots are optional
- The semicolons are optional 
- There is no need to use **return**. Scala is usually able to infer the return types of methods.
- Scala has **default values** for parameters (no need to do overloading)
`def log(message: String, level: String = "INFO") = println(s"$level: $message")`
- **Tuple** is an immutable object sequence created as comma-separated values. i.e. `(1,2,3)` tuple literal (Tuple3)
- **Implicit parameters** are always in definitons of function as last seperate column.
- **Implicit function** quietly transform object to object of different type. `implicit def convIntToMyObject(number: Int) = new MyObject(number)`
- **Implicit class** Instead of creating a regular class and a separate implicit conversion method you can use class as adapter or converter.  `implicit class MyObjectHelper(val offset: Int) { ... }`
- Polymorphic function - (kind of parametric polymorphism) It is also called **generic function**. `def isSorted[A](as: Array[A], ordered: (A,A) => Boolean): Boolean`
- **Access Modifier** 
  - **public** is default
  - the **protected** means that only derived classes can access it (different from Java)

### Loop
- `for ( i <- i to 3 ) { ... }`
- `( 1 to 3 ).foreach( ... )` We used the foreach method of the Range class

### Operator Overloading
- Scala has no operators, so operator overloading means overloading symbols like +, etc.

### Scala Classes for Java primitives:
- Classes like `RichInt`, `RichDouble`, `RichBoolean`, and so on are called rich wrapper classes. They provide convenience methods that can be used for classes in Scala that represent the Java primitive types and String.

### Type aliasing
- You can alias the given class `type MyAlias = OldClass`

### Pattern matching
- Works like fancy switch
- Each case in match consist of the pattern

### Comparing
- SCALA’S *==* represents value-based comparison, no matter what the type is (This is ensured by implementing == as final in the class Any)
- `eq` method provides identity-based comparison on references

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

### Parametrized functions
- The notation [T] signals to the compiler that the type T that follows is not some existing
- Scala will require that the arguments be of the same type, but there is type `Any` so the call echo("hi", 5) will unfortunately work.
```scala
def echo[T](input1: T, input2: T) =
  println(s"got $input1 (${input1.getClass}) $input2 (${input2.getClass})")
```

### String
- is simply `java.lang.String`
- The String is automatically converted to `scala.runtime.RichString`. This brings a few useful methods like `capitalize`, `lines`, and `reverse`.
- Three double quotes (`"""…"""`) for creation of String on more lines
- String literals with expresion `val message = s "A discount of $discount% has been applied"`


