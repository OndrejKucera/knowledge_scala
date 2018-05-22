Scala Types
==============
Scala is statically typed language

- **Expressions** are computable statements.
- **Values** cannot be re-assigned (Scala compiler will complain). The immutability applies to the variable and not the instance to which the variable refers. Prefer val over var as much as possible since that promotes **immutability**, which leads to fewer errors, and functional style. Types of values can be inferred, but you can also explicitly state the type.
- **Variables** are like values, except you can re-assign them (mutability)
- **Blocks** are expressions by surrounding `{ }`. Last expression in the block is the result.
- **Functions** are expressions that take parameters. Anonymous function `(x: Int) => x + 1`. You can name it `val fun = ( ) => println(“hello”)`. It can have zero or multiple parameters. Recursive function needs return type in scala.
- When we define a function literal, what is actually being defined in Scala is an object with a method called apply
- **Methods** are defined with def. def is followed by a name, parameter lists, a return type, and a body. Methods can take multiple parameter lists.
- **Classes** define with the keyword `class` followed by its name and constructor parameters. The instance of class can be created with the new keyword. Classes in Scala cannot have static members. You can use objects to achieve similar functionality as with static members in Java.
- **Case class** is special type of class. It is immutable and compared by value. Instance of case class can be created without `new` keyword.
- **Object** is single instances of its own definition. It is singleton `object`, which simultaneously declares also class and it’s only instance. (like new instance of an anonymous class in Java)
- **Trait** contains certain fields and methods. Methods in `trait` can have default implementation or override implementation.
- **Sealed trait** - all implementations of the trait must be declared in this file

### Fundamental types
- **Unit** is similar as void in Java. Usually a return type of Unit is a hint that the method has a side effect.
- **Any** is the class from which all types in Scala derive (super class of all types). Is abstract class with these methods: `!=`, `==`, `asInstanceOf`, `equals`, `hashCode`, `isInstanceOf`, and `toString`.
  - AnyVal: base for all types in Scala—for example, Int, Double, ... (map over to the primitive types in Java)
  - AnyRef: base for all reference types. It has also the methods `notify`, `wait`, and `finalize`. It directly maps to the Java `Object`.
- **Nothing** (is everything) is a subtype of all classes in Scala. It will have no possible value.
- **Option** The Option type is useful when the result of a function call may or may not exist. Instances of Option are either an instance of `scala.Some` or the object `None`.
```scala
val nameMaybe = request.getParameter("name")
nameMaybe match {
  case Some(name) =>
    println(name.trim.toUppercase)
  case None =>
    println("No name value")
}
```
- **Either** 

### Type Inference
- `val greet: String = "Ahoy!"`
- the type information is the second becuase of the name of variable is more important and the type is optional.
- check the type of variable `greet.getClass`
- The type has to be specified when: fileds without innitial value, parameters for function/method, return type when there is no return 
- If there is no equal sign `=` then the type won't be inferred i.e. `def function1 { Math.sqrt(4) }`

### Conversion
- Scala will stop at compile time any conversions that may potentially lead to runtime failures
- **Supporting covariance**:
  - `T <: Pet` indicates that the class represented by `T` is derived from `Pet`. The upper bound is defined.
```scala
class Dog(override val name: String) extends Pet(name)

def workWithPets(pets: Array[Pet]) {}
val dogs = Array(new Dog("Rover"), new Dog("Comet"))
workWithPets(dogs) // Compilation ERROR

def playWithPets[T <: Pet](pets: Array[T]) {}
playWithPets(dogs) // Compilation OK
```

