Objects
==============

- creating instance `new MyObject(parameter)` or when there is no parameter it can be `new MyObject`.
- creating class
```scala
class Car(val year: Int) {
  private var milesDriven: Int = 0
	
  def miles = milesDriven

  def drive(distance: Int) {
    milesDriven += Math.abs(distance)
  }	
}
```
