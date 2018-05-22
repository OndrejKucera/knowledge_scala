OOP in Scala
==============

### Defining class
```scala
class Car(val year: Int) {
  private var milesDriven: Int = 0
	
  def miles = milesDriven

  def drive(distance: Int) {
    milesDriven += Math.abs(distance)
  }	
}
```
- Creating instance `new MyObject(parameter)` of Class or when there is no parameter it can be `new MyObject`.
- Constructor parameter with `val` defines `private final` field and access method for fetching that value.
- Constructor parameter with `var` creates `private` field and public getter and setter for it.
- Constructor parameter without either of those keywords defines `private final` field for only internal use.
- There is no need for curly braces ({}) if the class definition has no body.
- Scala will execute as part of the primary constructor any expression or executable statement directly placed into the class definition.
- Primary construct can be marked as private `class Marker private(val color: String)`
- Scala provides the convenience of initializing `var` to its default value using the underscore (default value). (Scala requires variables to be initialized before use)

### Exteding Class
- Same as in Java. Only two deferences, the keyword override is required and and primary constructor can pass parameters to a base constructor.
- `class Car(override val id: Int) extends Vehicle(id) { ... }`

### Parameterized Class
```scala
class Message[T](val content: T) {
  override def toString = s"message content is $content"
}
```

### Singletons
- It turned out that the singleton pattern is easy to understand but hard to implement in Java
- To create a singleton use the keyword `object`
- Singleton object can not be instantiate and therefor you can not pass parameters to the constructor.

### Companion object
- It is possible to associate a singleton to a class.
- You have to create `class` with private constructor and the `object` with same name.
- Companion object has ability to create instance of class without useing the `new` keyword

### Static in Scala
- There is no `static` in Scala because it would break the pure OO mode.
- You can write the static-like method in singleton object. The `apply` method does it.

### Traits
- Traits are like interfaces with a partial implementation
- Traits provide a middle ground between single and multiple inheritance
```scala
trait Friend {
  val name: String // abstract
  def listen() = println(s"Your friend $name is listening")	
}
```
- Trait's constructor cannot take any parameters
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
