Monads
====================

- Monad is a **concept**
- Scala doesn’t come with a built-in monad type. But it uses the concept in `Option` (unit(x) = Some(x)), `List` (unit(x) = List(x)), `Set`, ...

- Monad is parametric type M[T] with two operations (you can think about monads as wrappers). Monad take a type parameter T. 
```scala
trait M[T] {
    def flatMap[U](f: t => M[U]): M[U]  // also called bind
}

def unit[T](f: T): M[T]  // also called identity
```
- The `unit` function performs the wrapping part.

- Three laws of Monad:
  - **associativity law:**: `m.flatMap(f).flatMap(g) == m.flatMap(x => f(x).flatMap(g))`
  - **left-identity law**: `unit(x).flatMap(f) == f(x)`
  - **right-identity law**: `m.flatMap(unit) == m`

note: (Integers are Monoid -> simpler version of Monad -> (x + y) + z == x + (y + z) )

Source: https://medium.com/@sinisalouc/demystifying-the-monad-in-scala-cc716bb6f534
