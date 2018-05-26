Concurrency
=============

- **Concurency problems**: thread safety, race conditions, deadlocks, livelocks, and hard-to-read error prone code. <- Shared mutability
- How to remove a mutability? -> Actors help to turn shared mutability into isolated mutability.

## Actors
  - Scala uses actors from **Akka**, a reactive library
  - Actor is object which never calls methods directly. Every actor recieve message for invoking the method.
  - **The messages** are queued and waiting. The senders are never blocked (fire-and-forget).
  - Akka provides a huge number of facilities to configure the thread pool size, the message queue size, and many other parameters, including interacting with remote actors.
### Definition of Actor
  - The body of the `receive` method looks familiar -> it’s the pattern matching syntax but witout match. The match is happening on an implicit message object. The body of the method is a partially applied function.
```scala
  import akka.actor._
	
  class MyActor() extends Actor {	
    def receive = {	
      case message => println(s"actore process $message")
    }
  }
```
### Create of Actor
  - `ActorSystem` manages threads, message queues, and actor lifetime.
  - The method `!` passes a message to the actor "myActore".
```scala
  object CreateActors extends App {
    val system = ActorSystem("sample")
    
    val myActore = system.actorOf(Props[MyActor])  
    nameForActor ! "important message"

    system.shutdown() 	
  }
```
### Rocommendations
  - Rely more on stateless actors instead of stateful actors.
  - Keep the processing in the receive method really fast, especially if the receiving actor is stateful
  - Ensure the messages passed between actors are immutable objects (i.e. case class, String, or Int)
  - As much as possible, avoid using ask (two-way communication)

## Laziness in programming
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
