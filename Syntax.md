Scala Syntax
==============

- When you call the method the parentheses and dots are optional
- The semicolons are optional 
- **Function** - In Scala, function values are really objects.
- There is no need to use **return**. Scala is usually able to infer the return types of methods.
- Scala has **default values** for parameters (no need to do overloading)
`def log(message: String, level: String = "INFO") = println(s"$level: $message")`
- Scala provides the notation `_`, the underscore, to represent parameters of a function value. `val total = (0 /: arr) { _ + _ }`
- **Implicit parameters** are always in definitons of function as last seperate column.
- **Implicit function** quietly transform object to object of different type. `implicit def convIntToMyObject(number: Int) = new MyObject(number)`
- **Implicit class** Instead of creating a regular class and a separate implicit conversion method you can use class as adapter or converter.  `implicit class MyObjectHelper(val offset: Int) { ... }`
- Polymorphic function - (kind of parametric polymorphism) It is also called **generic function**. `def isSorted[A](as: Array[A], ordered: (A,A) => Boolean): Boolean`
- **foldLeft** - i.e. `val sum = array.foldLeft(0) { (sum, elem) => sum + elem }` or with operator `/:`
- Closures: creates code blocks with variables that are not bound
- Scala provides the convenience of initializing `var` to its default value using the underscore (default value). (Scala requires variables to be initialized before use)
- If all **recursive calls** made by a function are in **tail position**, Scala automatically compiles the recursion to iterative loops that don’t consume call stack frames for each iteration. (@annotation.tailrec)
- The left of the arrow `<-` defines a val
- If a method name ends with a colon `:`, then the target of the call is the instance that follows the operator.


### Loops
- **for expression**:
  - basic for loop `for ( i <- i to 3 ) { ... }`
  - The `yield` keyword is optional and, if present, tells the expression to return a list of values instead of a `Unit`. i.e. `val result = for (i <- 1 to 10) yield i * 2`
  - applied the filter part: `val doubleEven = for (i <- 1 to 10; if i % 2 == 0) yield i * 2`
  - multiple generators: `for (i <- 1 to 3; j <- 4 to 6) { print(s"[$i,$j] ") }`
```scala
for([pattern <- generator; definition*]+; filter*)
  [yield] expression
```
- **while** loop `while (x < 5) {x += 1}`
- **do while** loop `do { println(x); x += 1} while (x < 5)`

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

### Partially Applied Functions
- The first bind a value to the date parameter. We use the `_` to leave the second parameter unbound.
```scala
val date = new Date(1420095600000L) 	
val logWithDateBound = log(date, _ : String)
logWithDateBound("message1")
logWithDateBound("message2")
```
- When you create a partially applied function, Scala internally creates a new class with a special apply method.

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

### Exceptions
- Scala doesn't force you to check exception that you are not care about. Those you don’t handle are propagated automatically
- Scala treats all exceptions as if they’re unchecked! :-)
- example of thrown `IllegalArgumentException`
- you can use try-catch as in Java but the syntax of catch is quite different in Scala
```scala
try {
  ....	
}
catch {
  case ex: IllegalArgumentException => ...	
  case ex: RuntimeException => ...
}
```
- You have to be careful wiht order of catching exceptions 
