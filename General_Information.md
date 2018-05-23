Generela information
====================
- 2004, Scala 1.1.1; 2006 2.0
- It supports an **imperative and a functional style** (it could be a blessing and a curse)
- It is **purely object-oriented**. Scala code has to be in an object or a class.
- **Static typing** and **type inference** (automatic type detection)
- Typically Scala programmers create one source file for each class, or one source file for a class hierarchy. Source code is stored in text files with the extension .scala
- There is no equivalent to Java’s static keyword, and an `object` is often used in Scala where you might use a class with static members in Java.
- **method main** has to has specific signature. It has to take an Array of Strings as its argument, and its return type must be Unit. When you run a program, Scala will look for a method named main. Main method is entry point for program, which JVM requires.
- Classes and methods are **public** by default, so you don’t explicitly use the keyword public.
- Scala, by default, imports `java.lang`, `scala`, `scala.Predef`
- Scala has the same compilation model (separate compilation, dynamic class loading) like Java and allows access to thousands of existing high-quality libraries.

### Imperative paradigm
- You tell not only what to do, but also how to do it. That’s dictating a low level of details.
- mutable variables, assignments, control structure (ifs, loops, returns, breaks, …) -> von Neumann style (John Backus) -> bottleneck -> poor extensibility

### Functional paradigm
- First functional language was Lisp in 1959
- Functional programming honors **immutability** and favors **higher-order functions** and **function composition**
- Two way of FP:
  - Restricted: without mutable variables, assignments, loops and other imperatives structures (Pure Lisp, XPath)
  - Wider sense: focusing on the functions. **Functions are first-class citizens**. Function can be defined anywhere, function can be passed and returned as a value, functions can be composed by set of operators.
- Why is FP popular: simpler reasoning principles, better modularity, good for parallelism
- **Higher order function** (HOF)
  - are functions that take other functions as arguments and may themselves return functions as their output
  - reduce code duplication, increase reuse, and make code concise
- **Pure function** is without **side effects** (such as reading files or mutating memory). Pure functions are easier to test, reuse, parallelize, generalize, and reason about. Furthermore, pure functions are much less prone to bugs.
  - **Side effect** means that function does more than just return value. (i.e. `i++`)
- **Currying**
  - Transforms a function that takes more than one parameter into a function that takes multiple parameter lists.
  - function return function which is parameter other function `def func(...)(...)`. One of the main reason using this is to assist with type inference.
- **Referential transparency** - in any program, the expression can be replaced by its result without changing the meaning of the program.
- **Substitution model** is scheme of expression -> idea: reduce an expression to a value (as long as they have no side effects) [Alonzo Church - lambda calculus]

### Scala on the Command Line
- Even though we don’t explicitly invoke the compiler when using the scala command, the code goes through rigorous compilation and type checking. The scala tool compiles the given script into bytecode in memory and then executes it.
- However, Scala does not force us to implement the main method
- hello.sh
```
#!/usr/bin/env scala
println("Hello " + args(0))
```

### Compiling Scala:
- **scalac** - compiles Scala code into Java Bytecode
- `scalac Sample.scala`
- run it using either the `scala` tool or the `java` command
