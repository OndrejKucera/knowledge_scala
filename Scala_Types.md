Scala Types
==============
Scala is statically typed language

- **Expressions** are computable statements.
- **Values** cannot be re-assigned (Scala compiler would complain). The immutability applies to the variable and not the instance to which the variable refers!
  - Prefer `val` over `var` as much as possible since that promotes **immutability**, which leads to fewer errors, and functional style. 
- **Variables** are like values, except you can re-assign them (mutabel)
- **Blocks** are expressions by surrounding `{ }`. Last expression in the block is the result.
- **Functions** are expressions that take parameters.
  - Anonymous function `(x: Int) => x + 1`.
  - You can name it `val fun = ( ) => println(“hello”)`.
  - It can have zero or multiple parameters.
  - When we define a function literal, what is actually being defined in Scala is an object with a method called apply
- **Methods** are defined with `def`. That is followed by a name, parameter lists, a return type, and a body. Methods can take multiple parameter lists.
- [**Class**](https://github.com/OndrejKucera/knowledge_scala/blob/master/OOP.md#class) defines with the keyword `class` followed by its name and constructor parameters. The instance of class can be created with the `new` keyword. Classes in Scala cannot have static members. You can use objects to achieve similar functionality as with static members in Java.
- [**Object**](https://github.com/OndrejKucera/knowledge_scala/blob/master/OOP.md#object) is single instances of its own definition. It is singleton `object`, which simultaneously declares also class and it’s only instance. (like instance of an anonymous class in Java)
- [**Trait**](https://github.com/OndrejKucera/knowledge_scala/blob/master/OOP.md#traits) contains certain fields and methods. Methods in `trait` can have default implementation or override implementation.

### Fundamental Types
- **Unit** is similar as void in Java. Usually a return type of `Unit` is a hint that the method has a side effect.
- **Any** is the class from which all types in Scala derive (super class of all types). Is abstract class with these methods: `!=`, `==`, `asInstanceOf`, `equals`, `hashCode`, `isInstanceOf`, and `toString`.
  - AnyVal: base for all types in Scala (Int, Long, Double, Float, Char, Short, Byte, Boolean, Unit). All primitives are objects.
  - AnyRef: base for all reference types. It has also the methods `notify`, `wait`, and `finalize`. It directly maps to the Java `Object`.
- **Nothing** (is everything) is a subtype of all classes in Scala. It has no possible value.
- [**Option**](https://github.com/OndrejKucera/knowledge_scala/blob/master/Error_Handling.md#option--either) The Option type is useful when the result of a function call may or may not exist.
- [**Either**](https://github.com/OndrejKucera/knowledge_scala/blob/master/Error_Handling.md#option--either)

### Data-Types
- `Byte`, `Int`, `Short`, `Long`, `Float`, `Double`
- `String`, `Char`
- For large numbers `BigInt` and `BigDecimal`

### Comparison
- Scala’s `==` represents value-based comparison, no matter what the type is (This is ensured by implementing `==` as final in the class `Any`)
- `eq` method provides identity-based comparison on references

### Type Inference
- Types of values can be inferred, but you can also explicitly state the type.
- `val greet: String = "Ahoy!"`
- The type information is the second -> becuase of the name of variable is more important and the type is optional.
- The type has to be specified when: fileds without innitial value, parameters for function/method, return type when there is no return
- Checking the type of variable `greet.getClass`
- If there is no equal sign `=` in definiton of method then the type won't be inferred, `def function1 { Math.sqrt(4) }`

### Conversion
- By default, the Scala compiler strictly enforces the variance.
- Scala will stop at compile time any conversions that may potentially lead to runtime failures.
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
- **Supporting contravariance**:
```scala
def copyPets[S, D >: S](fromPets: Array[S], toPets: Array[D]) = { //... }
val pets = new Array[Pet](10)
copyPets(dogs, pets)
```
- `+T` allow covariance, `-T` support contravariance


