Error Handling
==============

### Exceptions
- Scala doesn't force you to check exception that you are not care about. Those you don’t handle are propagated automatically
- Scala treats all exceptions as if they’re unchecked! :-)
- You can use try-catch as in Java but the syntax of catch is quite different in Scala (patter-matching)
- You have to be careful with order of catching exceptions
- There is finally clause, which is typically used when you need to close a resource.
```scala
try {
  ....	
} catch {
  case ex: IllegalArgumentException => ...	
  case ex: RuntimeException => ...
} finally {
    // code for closing a database connection or file handle
}
```

### Option & Either
- **Option** The Option type is useful when the result of a function call may or may not exist. Instances of `Option` are either an instance of `scala.Some` or the object `scala.None`.
  - The idea in is that we can represent failures and exceptions with ordinary value.
  - It is good practice to avoid using `null`: because it silently propagates error, generates boilerplate code and it’s not applicable to polymorphic code
  - `Option` can be thought of like a `List` that can contain at most one element
  - A common pattern is to transform an `Option` via calls to `map`, `flatMap`, and/or `filter`, and then use `getOrElse` to do error handling at the end. `lookupByName("Joe").map(_.dept).filter(_ != "Accounting").getOrElse("Default Dept")`
  - A common idiom is to do o.getOrElse(throw new Exception("FAIL")) to convert the None case of an Option back to an exception.
  - for-comprehension (`for { ... } yield (...)`) is often use for striping the Options and get the values -> The compiler desugars the bindings to flatMap calls, with the final binding and yield being converted to a call to map.
- **Either** Option doesn’t tell us anything about what went wrong in the case of an exceptional condition. 
  - An instance of Either is an instance of either `scala.util.Left` (error) or `scala.util.Right` (right value).

### Try
- `Try` makes it very simple to catch exceptions.
- Instances of Try are `Success` that contains the number and `Failure` contains the exception message.
```
def toInt(s: String): Try[Int] = Try {
    Integer.parseInt(s.trim)
}

// using matching
toInt(x) match {
    case Success(i) => println(i)
    case Failure(s) => println(s"Failed. Reason: $s")
}

// using for-expression
val y = for {
    a <- toInt(stringA)
    b <- toInt(stringB)
    c <- toInt(stringC)
} yield a + b + c
```

