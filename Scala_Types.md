Scala Types
==============

- **Expressions** are computable statements.
- **Values** cannot be re-assigned (Scala compiler will complain). The immutability applies to the variable and not the instance to which the variable refers. Prefer val over var as much as possible since that promotes **immutability**, which leads to fewer errors, and functional style. Types of values can be inferred, but you can also explicitly state the type.
- **Variables** are like values, except you can re-assign them (mutability)
- **Blocks** are expressions by surrounding { }. Last expression in the block is the result.
- **Functions** are expressions that take parameters. Anonymous function (x: Int) => x + 1. You can name it val fun = ( ) => println(“hello”). It can have zero or multiple parameters. Recursive function needs return type in scala.
- When we define a function literal, what is actually being defined in Scala is an object with a method called apply
- **Methods** are defined with def. def is followed by a name, parameter lists, a return type, and a body. Methods can take multiple parameter lists.
- **Classes** define with the keyword class followed by its name and constructor parameters. The instance of class can be created with the new keyword. Classes in Scala cannot have static members. You can use objects to achieve similar functionality as with static members in Java.
- **Case class** is special type of class. It is immutable and compared by value. Instance of case class can be created without new keyword.
- **Object** is single instances of its own definition. It is singleton object, which simultaneously declares also class and it’s only instance. (like new instance of an anonymous class in Java)
- **Trait** contains certain fields and methods. Methods in trait can have default implementation or override implementation.
- **Sealed trait** - all implementations of the trait must be declared in this file
- **Unit** is similar as void in Java. Usually a return type of Unit is a hint that the method has a side effect.
