Pattern Matching
=======================
- Fancy (Java's) switch :-)
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
- The wildcard, represented by an underscore `_`, handle the rest of the cases.
- If the value doesn't match with anything then the `MatchError` exception will be thrown.
- The order of multiple case expressions matters!
- Any variable or constant with the same noncapitalized name in the scope will be ignored. Therefor use `case this.max => ...`
- You can pattern-match XML fragments as well

- **Matching tuples and list**:
  - use `case` expression to match against tuples and lists
  - `case (lat, long) => ... ` this matches any tuple with two values
  - `case List("red", "blue", _*) => ...` matches List with two and more elements
- **Matching types**:
  - `case (a: Int, b: Int) => ...`
  - `case msg : Int if (msg > 1000000) => ...` 
- **Matching using extractors**:
  - The extractor has one method named `unapply` (breaks down the object into pieces that match a pattern)
  - The extractor can also return one or more values
```scala
object StockService {
  def process(input : String) {
    input match {
      case Symbol() => println(s"Look up price for valid symbol $input")
      case _ => println(s"Invalid input $input")
    }
  }	
}

object Symbol {	
  def unapply(symbol : String) : Boolean = {
    symbol == "GOOG" || symbol == "IBM"
  }
}
```

### Regular Expression
- `Regex` class in `scala.util.matching` package
- creating the regex in Scala `val pattern = "(S|s)cala".r`
- To find a first match of the regular expression, simply call the `findFirstIn` method or all occurrences `findAllIn`
- Scala regular expressions are extractors, so you can use them in matchers
