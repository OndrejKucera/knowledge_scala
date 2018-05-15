Generela information
====================
- 2004, Scala 1.1.1
- It is purely object-oriented
- It supports an imperative style and a functional style (it can be a blessing and a curse)
- Static typing and type inference (automatic type detection)
- Primitives in Java are objects in Scala (Int, Long, Boolean)
- Function parameter come with their type, after colon (number: Int)
- Source code is stored in text files with the extension .scala
- Typically Scala programmers create one source file for each class, or one source file for a class hierarchy
- has shell (REPL)
- Scala has the same compilation model (separate compilation, dynamic class loading) like Java and allows access to thousands of existing high-quality libraries.

## Syntax
- the left of the arrow (<-) defines a val
- the variables defined using val are immutable and can’t be changed after initialization. But! The immutability applies to the variable and not the instance to which the variable refers. Prefer val over var as much as possible since that promotes immutability, which leads to fewer errors, and functional style.