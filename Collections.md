Scala-specific Collections
==============
(Of course you can still use the collections from the JDK such as ArrayList, HashSet, and simple arrays)

- All collection classes are found in the package `scala.collection` -> look at [the picture](https://docs.scala-lang.org/resources/images/collections.png) of all collections in package (abstract classes or traits)
- Scala favors immutable collection (`scala.collection.immutable.`) [image of tree](https://docs.scala-lang.org/resources/images/collections.immutable.png), even though mutable versions are avaliable too (`scala.collection.mutable`) [image of tree](https://docs.scala-lang.org/resources/images/collections.mutable.png)
- A mutable collection can be updated or extended in place. Change, add, or remove elements of a collection as a side effect.
- Immutable collections, by contrast, never change. Each operation returns a new collection and leave the old collection unchanged.
- If you don’t mention a package name, then, by default, Scala brings on board immutable collections. Because the object Predef (included by default) provides aliases for Set and Map to point to the immutable implementations.
- Immutable collections are thread safe, free from side effects, and help with program correctness.
- The ability to create an object without `new` is because of a special `apply` method, also called a factory method. `Set(1, 2, 4)`

### Main traits
 - **Traversable**
   - It has one abstract operation `def foreach[U](f: Elem => U)`, which has to be implemented.
   - [Operations in Class Traversable](https://docs.scala-lang.org/overviews/collections/trait-traversable.html#operations-in-class-traversable)
 - **Iterable** - ??? -> https://docs.scala-lang.org/overviews/collections/trait-iterable.html

### Seq
- traits IndexedSeq, LinearSeq
- **List**
  - Is subclass of `Seq` -> `LinearSeq` -> `List`
  - It is an ordered collection of objects
  - The most operations on the list are structured around operations on the `head` and `tail`.
  - The accesing the second element `val element = list(1)`
  - Add element on the begining `val prefixedList = "newElement" :: feeds`
  - There are also methods `filter`, `forall`, `exists`, `map`,
  - The method `/:` is equivalent to `foldLeft` and `\:` to `foldRight`
  - Concatenating `::`
- **Stream**
  - ???

### Set
- `HashSet`, `TreeSet`, `BitSet`, `ListSet`
- Set holds an element at most once and it is an unordered collection. 
- Scala optimizes the implementation of Set for smaller values, and creates an implementation of HashSet for values higher than 4.
- merging two Sets by `val mergedFeeds = feeds1 ++ feeds2`
- intersect operation `val commonFeeds = feeds1 & feeds2`
- there are also methods `map`, `filter`, `foreach`, ...

### Map
- `HashMap`, `TreeMap`, `ListMap`
- It is a dictionary of key-value pairs.
- To get a feed for a person, simply use the `get` method. The return type of `get` is `Option[T]`.
- To add a feed, use the `updated` method. It has no effect on the original Map.
- There are also methods `filterKey`, `filter`, ...

### Methods of Collections
- foldLeft - `val sum = array.foldLeft(0) { (sum, elem) => sum + elem }` or with operator `/:`
- foreach - `( 1 to 3 ).foreach( ... )` We used the foreach method of the Range class
- reduce - `(1 to 3).reduce((x, y) => x+ y)` reduceLeft is a special case of foldLeft
- ... Lets read: https://docs.scala-lang.org/overviews/collections/overview.html

## Parallel collections
  - Parallel collections are in `scala.collection.parallel.immutable` package can do parallel processing of elements in a collection
  - Low-level threads and locks can increase accidental complexity and concurrency-related errors. But it’s easy to parallelize operations on a collection of data, in Scala.
  - Immutable collections have method `par` that converts them into parallel ones.
  - If the operations, invoked on the collection, modify a global state then the overall result of the computation is unpredictable. Shared mutability is generally a bad idea.
