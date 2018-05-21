OOP in Scala
==============

- Defining class
```scala
class Car(val year: Int) {
  private var milesDriven: Int = 0
	
  def miles = milesDriven

  def drive(distance: Int) {
    milesDriven += Math.abs(distance)
  }	
}

- Creating instance `new MyObject(parameter)` of Class or when there is no parameter it can be `new MyObject`.
- Constructor parameter with `val` defines `private final` field and access method for fetching that value.
- Constructor parameter with `var` creates `private` field and public getter and setter for it.
- Constructor parameter without either of those keywords defines `private final` field for only internal use.
- There is no need for curly braces ({}) if the class definition has no body.

```
- Scala will execute as part of the primary constructor any expression or executable statement directly placed into the class definition.
- Primary construct can be marked as private `class Marker private(val color: String)`
- Scala provides the convenience of initializing `var` to its default value using the underscore (default value). (Scala requires variables to be initialized before use)

### Exteding Class
- Same as in Java. Only two deferences, the keyword override is required and and primary constructor can pass parameters to a base constructor.
- `class Car(override val id: Int) extends Vehicle(id) { ... }`
