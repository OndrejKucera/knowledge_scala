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
- [Performance characteristics](https://docs.scala-lang.org/overviews/collections/performance-characteristics.html)

### Main Collection Traits
 - **Traversable Trait**
   - It has one abstract operation `def foreach[U](f: Elem => U)`, which has to be implemented.
   - [Operations in Class Traversable](https://docs.scala-lang.org/overviews/collections/trait-traversable.html#operations-in-class-traversable)
   - **Operations**
     - `++` - appends two collections together
     - `map` - apply function on each elemnt in the collection and return the collection
     - `flatMap` - apply function on each elemnt in the collection and concatenate the return items
     - `foldLeft` - `val sum = list.foldLeft(0) { (sum, elem) => sum + elem }` or with operator `/:`, 
     - `reduce` - reduceLeft is a special case of foldLeft `(1 to 3).reduce((x, y) => x+ y)` 
     - `foreach` - `( 1 to 3 ).foreach( ... )` We used the foreach method of the Range class
     - **Conversions**: `toArray`, `toList`, `toIterable`, `toSeq`, `toIndexedSeq`, `toStream`, `toSet`, `toMap`
     - **Size of**: `isEmpty`, `nonEmpty`, `size`, and `hasDefiniteSize`
     - **Element retrieval**: `head`, `last`, `find`
     - **Sub-collection retrieval**: `tail`, `init`, `slice`, `take`, `drop`, `takeWhile`, `filter`
     - **Subdivision**: `splitAt`, `span`, `partition`, `groupBy`
     - **Element tests**: `exists`, `forall`, `count`
     - **Specific folds**: `sum`, `product`, `min`, `max`
 - **Iterable Trait**
   - It implements funtion `foreach`
   - It has three function which return iterator `iterator`, `grouped(size)` and `sliding(size)` 

### Seq
- The `Seq` trait represents sequences. A sequence is a kind of iterable that has a `length` and whose elements have fixed index positions, starting from 0.
- traits `IndexedSeq`, `LinearSeq`: they do not add any new operations, but each offers different performance characteristics
  - **Linear sequence** (List, Stream, Queue, Stack) has efficient head and tail
  - **Indexed sequence** (Range, Vector, ...) has efficient apply and length (if mutable seq then update operation)
- **Operations** 
  - **Index search**: `indexOf`, ...
  - **Addition**: `+:`, `:+`, `padTo`
  - **Update**: `updated`
  - **Sorting**: `sorted`, `sortWith`, `sortBy`
  - **Reversal**: `reverse`, ...
  - **Comparisons**: `contains`, ...
  - **Multiset**: `intersect`, `diff`, `union`, `distinct`
- **List**
  - Is subclass of `LinearSeq`
  - The most operations on the list are structured around operations on the `head` and `tail`.
  - It is an ordered collection of objects
  - Constatnt time to get `head`, `tail` and add item on the begining of list. Other operation has linear time.
  - The accesing the second element `val element = list(1)`
  - Concatenating `::` => adding element on the begining `val prefixedList = "newElement" :: feeds`
- **Stream**
  - It is like List (same performace characteristic) but computed lazily => tail is evaluated only on demand
  - Stream can be infinitely long
  - creating Stream `(1 to 1000).toStream`
  - Concatenating `#::`
- **Vector**
  - Represents by shallow tree with a high branching factor => every tree node contains up to 32 elements of the vector or contains up to 32 other tree nodes.
  - It has more evenly balanced access to the items than List => almost constant
  - More efficient for bulk operation (map, filter, ...) than List
- **Stack**
  - last-in-first-out sequence
  - `push`, `pop`, `top` are in constant time
  - Immutable stacks are used rarely
- **Queue**
  - last-in-first-out sequence
  - `enqueue`, `dequeue`,
- **Range**
  - ordered sequence
  - `1 until 5` => 1,2,3,4 ; `1 to 5` => 1,2,3,4,5 ; `1 to 10 by 3`
 
### Set
- Set is an unordered collection and contains no duplications
- Operations:
  - **Tests**: `contains`, `subsetOf`
  - **Additions**: `+`, `++`
  - **Removals**: `-`, `--`
  - **Set op.**: `intersect`, `union`, and `diff`
- merging two Sets by `val mergedFeeds = feeds1 ++ feeds2`
- intersect operation `val commonFeeds = feeds1 & feeds2`
- Scala optimizes the implementation of Set for smaller values, and creates an implementation of HashSet for values higher than 4.
- **ListSet**
- **TreeSet**
  - It is ordered binary tree (red-black tree). All elements in the left subtree of a node are smaller than all elements in the right subtree
  - `immutable.TreeSet` uses a red-black tree to maintain ordering and balance (paths from the root of the tree to a leaf have lengths that differ only by at most one element).
  ```scala
    val myOrdering = Ordering.fromLessThan[String](_ > _)
    TreeSet.empty(myOrdering)
  ```
- **BitSet**
  - Sets of non-negative integer. It uses for representation an array of Longs
  - Advantage is that operations such as membership test with contains, or element addition and removal are extremely efficient.
- **HashSet**

### Map
- Map consists of key-value pairs.
- Operations:
  - **lookup**: `apply`, `get`, `getOrElse`
  - **updates**: `+`, `++`, `update`
  - **removal**: `-`, `--`
  - **subcollection**: `keys`, `keySet`, `values`, ...
  - **Transformations**: `mapValues`, `filterKeys`
- **HashMap**
- **TreeMap** - red-black tree
- **ListMap** - linked list of key-value pairs. It has little usage
- Hash Tree: every node has 32 elements (or 32 subtrees). The selection of key is based on hashcode
- method `get` get a value of pair in map. The return type of `get` is `Option[T]`.
- method `updated` adds a feed. It has no effect on the original Map.

### Array
- It is same as Java array, but it has some enhacements
- Scala Array can be generic Array[T]
- Scala Array is compatibile with sequences -> you can pass an Array[T] where a Seq[T]
- It supports all sequence operations thanks to implicit conversions

## Parallel collections
  - Parallel collections are in `scala.collection.parallel.immutable` package can do parallel processing of elements in a collection
  - Low-level threads and locks can increase accidental complexity and concurrency-related errors. But it’s easy to parallelize operations on a collection of data, in Scala.
  - Immutable collections have method `par` that converts them into parallel ones.
  - If the operations, invoked on the collection, modify a global state then the overall result of the computation is unpredictable. Shared mutability is generally a bad idea.
