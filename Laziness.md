Laziness in programming
=============

- **Lazy Evaluation**
  - Scala can postpone evaluating the value until it’s really needed.
  - `lazy val perform = expensiveComputation()`
  - You can mark any variable as lazy and the binding to its value will be postponed until the first use of that variable.
  - Carefuly with lazy variables -> the order of evaluation can be unknown -> the problem with sides effects
- **Lazy Collection**
  - Strict Collection can be turn into lazy collection -> `view` method
  - Lazy view on a strict collection doesn’t change the collection; it helps delay executing operations to the last possible moment.
  - `people.view.filter {isOlderThan17}.filter {isNameStartsWithJ}.head` The every item will go one be one through pipline
- **Lazy Stream**
  - A Stream is lazy to the bone — it produces values only on demand.
  - It postpones the execution until the final result is requested (by method `force`, `toList`, ...)
  - concatenate a stream `1 #:: Stream(2)`
  - `take` or `takeWhile` methods can take just few items from the Stream
