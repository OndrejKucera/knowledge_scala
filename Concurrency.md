Concurrency
=============

- **Lazy Evaluation**
  - Scala can postpone evaluating the value until it’s really needed.
  - `lazy val perform = expensiveComputation()`
  - You can mark any variable as lazy and the binding to its value will be postponed until the first use of that variable.
  - Carefuly with lazy variables -> the order of evaluation can be unknown -> the problem with sides effects
  
- **Lazy Collection**
  - Strict Collection can be turn into lazy collection -> `view` method
  - `people.view.filter {isOlderThan17}.filter {isNameStartsWithJ}.head` The every item will go one be one through pipline 
