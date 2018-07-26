Concurrency
=============

- **Concurency problems**: thread safety, race conditions, deadlocks, livelocks, and hard-to-read error prone code. <- Shared mutability
- How to remove a mutability? -> Actors help to turn shared mutability into isolated mutability.

## [Actor Model](https://en.wikipedia.org/wiki/Actor_model)
- In an actor-based system, everything is an actor (an actor is the smallest unit of functionality.), in much the same way that everything is an object in object-oriented design. 
- An actor is a long-running process that runs in parallel to the main application thread, and responds to messages that are sent to it.
- Actors are much easier to work with than threads; you program at a much higher level of abstraction.
- Only way how to comunicate with actor is throw messages.
- The message is immutable (typically as a case class or case object in Akka). These messages are queued in the actor’s mailbox.
- The senders are never blocked (fire-and-forget).
- An actor has one parent, known as a supervisor and it can have children.
- Delegation: Actor should delegate its work. Actors need to be able to respond to messages in their mailbox as fast as possible.

### Akka's actors
- **Akka** is a toolkit and runtime for building highly concurrent, distributed, and fault tolerant applications on the JVM.
- Scala uses actors from Akka, a **reactive library**. Akka strictly adheres to the [The Reactive Manifesto](https://www.reactivemanifesto.org/).
  - All the complexity of creating and scheduling threads, receiving and dispatching messages, and handling race conditions and synchronization, is relegated to the framework to handle transparently.
- Akka provides a huge number of facilities to configure the thread pool size, the message queue size, and many other parameters, including interacting with remote actors.
- **Actors** in Akka is essentially nothing more than an object that receives messages and takes actions to handle them. They have four options for handeling messages:
  - Execute some operations itself
  - Forward the message, or a derived message, to another actor
  - Instantiate a new actor and forward the message to it
  - Alternatively, the actor may choose to ignore message
- Each actor is provided with the following useful information:
  - `sender`: an `ActorRef` to the sender of the message currently being processed
  - `context`: information and methods relating to the context within which the actor is running (includes, for example, an actorOf method for instantiating a new actor)
  - `supervisionStrategy`: defines the strategy to be used for recovering from errors
  -`self`: the ActorRef for the actor itself
- The only way to communicate with an actor is through an `ActorRef`
- There are to ways how to send message to actor:
  - `!` (“tell”) – sends the message and returns immediately
  - `?` (“ask”) – sends the message and returns a [Future](https://github.com/OndrejKucera/knowledge_scala/blob/master/Concurrency.md#future) representing a possible reply

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
### Recommendations
  - Rely more on stateless actors instead of stateful actors.
  - Keep the processing in the receive method really fast, especially if the receiving actor is stateful
  - Ensure the messages passed between actors are immutable objects (i.e. case class, String, or Int)
  - As much as possible, avoid using ask (two-way communication)
  
## Future
- ???
