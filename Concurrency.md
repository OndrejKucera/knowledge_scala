Concurrency
=============

- **Concurency problems**: thread safety, race conditions, deadlocks, livelocks, and hard-to-read error prone code. <- Shared mutability
- How to remove a mutability? -> Actors help to turn shared mutability into isolated mutability.

## Actor Model
- Scala uses actors from **Akka**, a reactive library
- An actor is a long-running process that runs in parallel to the main application thread, and responds to messages that are sent to it.
- Actors are much easier to work with than threads; you program at a much higher level of abstraction.
- An actor is the smallest unit of functionality when building an actor-based system
- Only way how to comunicate with actor is throw messages.
- The message is immutable (typically as a case class or case object in Akka). These messages are queued in the actor’s mailbox.
- The senders are never blocked (fire-and-forget).
- An actor has one parent, known as a supervisor and it can have children.
- Delegation: Actor should delegate its work. Actors need to be able to respond to messages in their mailbox as fast as possible.
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
