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

### Comparison
- Scala’s `==` represents value-based comparison, no matter what the type is (This is ensured by implementing `==` as final in the class `Any`)
- `eq` method provides identity-based comparison on references

### Loops
- **while** loop `while (x < 5) {x += 1}`
- **do while** loop `do { println(x); x += 1} while (x < 5)`
- **for-loop** `for ( i <- i to 3 ) { ... }` which has side effects.
- **for-expression** is used to create new collections from existing collections
  - The `yield` keyword is optional and, if present, tells the expression to return a list of values instead of a `Unit`. i.e. `val result = for (i <- 1 to 10) yield i * 2`
  - applied the filter part: `val doubleEven = for (i <- 1 to 10; if i % 2 == 0) yield i * 2`
  - multiple generators: `for (i <- 1 to 3; j <- 4 to 6) { print(s"[$i,$j] ") }`
```scala
for([pattern <- generator; definition*]+; filter*)
  [yield] expression
```

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

