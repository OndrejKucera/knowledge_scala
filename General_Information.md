Generela information
====================
- 2004, Scala 1.1.1; 2006 2.0
- It supports an **imperative and a functional style** (it could be a blessing and a curse)
- It is **purely object-oriented**. Scala code has to be in an object or a class.
- **Static typing** and **type inference** (automatic type detection)
- Source code is stored in text files with the extension .scala
- Scala is usually able to infer the return types of methods. There is no need to use return.
- Typically Scala programmers create one source file for each class, or one source file for a class hierarchy
- Java's primitives are objects in Scala (Int, Long, Boolean)
- There is no equivalent to Java’s static keyword, and an *object* is often used in Scala where you might use a class with static members in Java.
- Scala has the same compilation model (separate compilation, dynamic class loading) like Java and allows access to thousands of existing high-quality libraries.
- *scalac* - compiles Scala code into Java Bytecode
- *boolean expressions* are same as a Java’s. && and || do not always need their right operand to be evaluated.
- **method main** has to has specific signature. It has to take an Array of Strings as its argument, and its return type must be Unit. When you run a program, Scala will look for a method named main. Main method is entry point for program, which JVM requires.
- If all **recursive calls** made by a function are in **tail position**, Scala automatically compiles the recursion to iterative loops that don’t consume call stack frames for each iteration. (@annotation.tailrec)

## Definition:
- def loop: Boolean = loop, is going to be evaluated always
- val loop: Boolean = loop, is going to be evaluated immediately and won’t terminate

## Syntax, etc.
- *Polymorphic function* - (kind of parametric polymorphism) It is also called generic function.
    def isSorted[A](as: Array[A], ordered: (A,A) => Boolean): Boolean
- *procedures* (or impure functions) rather than functions, to emphasize the fact that they have side effects


