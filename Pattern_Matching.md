Pattern Matching
=======================

```scala
def activity(day: DayOfWeek.Value) {
  day match {
    case DayOfWeek.SUNDAY => println("Eat, sleep, repeat...")
    case DayOfWeek.SATURDAY => println("Hang out with friends")
    case _ => println("...code for fun...")
  }	
}
```
- You can directly match against literals and constants
- the wildcard, represented by an underscore `_`, handle the rest of the cases.
- If the value doesn't match with anything then the `MatchError` exception will be thrown.
- The order of multiple case expressions matters!

- **Matching tuples and list**:
  - use `case` expression to match against tuples and lists
  - `case (lat, long) => ... ` this matches any tuple with two values
  - `case List("red", "blue", _*) => ...` matches List with two and more elements
- **Matching types**:
  - `case (a: Int, b: Int) => ...`
  - `case msg : Int if (msg > 1000000) => ...` 
