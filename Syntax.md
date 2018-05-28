Scala Syntax
==============

- The semicolons `;` are optional
- When you call the method the parentheses and dots are optional
- Scala provides the notation `_`, the underscore, to represent parameters of a function value.
  - `val total = (0 /: arr) { _ + _ }`
- Scala provides the convenience of initializing `var` to its default value using the underscore (default value). (Scala requires variables to be initialized before use)
- The left of the arrow `<-` defines a val
- If a method name ends with a colon `:`, then the target of the call is the instance that follows the operator.
- Operator overloading - Scala has no operators, so an operator overloading means overloading a method etc. +, ...
- Short-circuit evaluation - Boolean expressions are same as a Java’s `&&` and `||`, do not always need their right operand to be evaluated.
- **Type** aliasing `type MyAlias = OldClass`
- load input from console `StdIn.readLine()`

### String
- is simply `java.lang.String`
- The String is automatically converted to `scala.runtime.RichString`. This brings a few useful methods like `capitalize`, `lines`, and `reverse`.
- Three double quotes (`"""…"""`) for creation of String on more lines
- String literals with expresion `val message = s "A discount of $discount% has been applied"`

### Tuple
- It is in `scala` package
- Tuple can hold multiple values with same or different types together.
- It is an immutable object sequence created as comma-separated values. i.e. `(1,2,3)` tuple literal (Tuple3)
- `var (x,y,z) = (1,2,3)` tuple unpacking via pattern matching.

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

### Files
- Write
```scala
val writer = new PrintWriter(new File("symbols.txt"))
writer write "AAPL"
writer.close()
```
- Read
  - read a lines: `Source.getLines())`
  - read from web: `Source.fromURL(new URL("http://localhost"))`
```scala
import scala.io.Source
println("*** The content of the file you read is:") 	
Source.fromFile("ReadingFile.scala").foreach { print }
```

