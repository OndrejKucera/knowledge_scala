OOP in Scala
==============

### Class
- Definiton of class `class Car(val year: Int) { }`
- There is no need for curly braces `{ }` if the class definition has no body.
- Creating instance `new MyObject(parameter)` of class or if it is without any parameter it can be `new MyObject`.
- **Constructor parameters**:
  - with `val` defines `private final` field and access method for fetching that value.
  - with `var` creates `private` field and public getter and setter for it.
  - without either of those keywords defines `private final` field for only internal use.
- **Access modifiers**: 
  - `public` is default
  - the `protected` means that only derived classes can access it (different from Java)
  - `private` can be accessed only in scope of class
- Scala will execute as part of the primary constructor any expression or executable statement directly placed into the class definition.
- Primary constructor can be marked as private `class Marker private(val color: String)`
- **Abstract class** is non-createable `abstract class D { ... }`
  - You want to create a base class that requires constructor arguments -> However, be aware that a class can extend only one abstract class.
  - Your Scala code will be called from Java code
- **Extending Class** similarly as in Java. There are only two deferences. The keyword `override` is required and primary constructor can pass parameters to a base constructor.
  - `class Car(override val id: Int) extends Vehicle(id) { ... }`
- **Implicit class** Instead of creating a regular class and a separate implicit conversion method you can use class as adapter or converter.
  - `implicit class MyObjectHelper(val offset: Int) { ... }`
- **Case class** It is special type of class. It is immutable and compared by value. Instance of case class can be created without `new` keyword.
- **Parameterized (generic) class**
```scala
class Message[T](val content: T) {
  override def toString = s"message content is $content"
}
```

### Object
- It turned out that the **singleton pattern** is easy to understand but hard to implement in Java
- To create a singleton use the keyword `object`
- Singleton object can not be instantiate and therefor you can not pass parameters to the constructor.
- **Companion object**:
  - It is possible to associate a singleton to a class.
  - You have to create `class` with private constructor and the `object` with same name.
  - Companion object has ability to create instance of class without useing the `new` keyword
- **Static in Scala**
  - There is no `static` in Scala because it would break the pure OO mode.
  - You can write the static-like method in singleton object. The `apply` method does it.

### Traits
- Traits are like Java's interfaces with a partial implementation
- Traits provide a middle ground between single and multiple inheritance
- It contains certain fields and methods. Methods in trait can have default or overridden implementation.
- **Sealed trait** - all implementations of the trait must be declared in this file
- Trait's constructor cannot take any parameters
```scala
trait Friend {
  val name: String // abstract
  def listen() = println(s"Your friend $name is listening")	
}
```
- **Selective Mixins** : 
```scala
val angel = new Cat("Angel") with Friend 	
val friend : Friend = angel
```

### Enumerations
- An enumeration is an object that extends the Enumeration class
```scala
object Currency extends Enumeration {
  type Currency = Value
  val CNY, GBP, INR, JPY, NOK, PLN, SEK, USD = Value	
}
```
