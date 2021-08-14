# Fail-Fast

A fail-fast iterator does not allow modifications to the Collection it traverses; this means, that it will throw out ConcurrentModificationException
when such a Collection is modified while being traversed by its iterator. It is not necessary to modify and traverse the
Collection using different threads to throw this exception; it will occur even if the modification and traversal are done in the same thread.

However, there is a difference between the iterator’s remove() function and the Collection’s remove() function. 
When the iterator’s remove() is invoked, no exception is thrown. The Collection’s remove(), on the other hand, throws this exception in case of concurrent modification.

# Fail-Safe

A fail-safe iterator creates a copy of the Collection and then traverses it; this allows modification in the original Collection, 
but the changes may not be reflected during traversal. Moreover, creating a copy of a Collection is considered a waste of time and space. 
Therefore, when traversing a large Collection, fail-safe iterators can be a disadvantage.

https://www.geeksforgeeks.org/fail-fast-fail-safe-iterators-java/


# Weakhasmap

You can use a WeakHashmap to reduce the chance of a memory leak as a result of caching some object. The WeakHashMap will automatically remove
entries whenever all references to the key are removed

# Java object References types

In Java; order from strongest to weakest, there are: Strong, Soft, Weak and Phantom

- A Strong reference is a normal reference that protects the referred object from collection by GC. i.e. Never garbage collects.
- A Soft reference is eligible for collection by garbage collector, but probably won't be collected until its memory is needed. i.e. 
  garbage collects before OutOfMemoryError.
- A Weak reference is a reference that does not protect a referenced object from collection by GC. i.e. garbage collects when no Strong or Soft refs.
- A Phantom reference is a reference to an object is phantomly referenced after it has been finalized, but before its allocated memory has been reclaimed.

Source

Analogy: Assume a JVM is a kingdom, Object is a king of the kingdom, and GC is an attacker of the kingdom who tries to kill the king(object).

- When King is Strong, GC can not kill him.
- When King is Soft, GC attacks him but King rule the kingdom with protection until resource are available.
- When King is Weak, GC attacks him but rule the kingdom without protection.
- When king is Phantom, GC already killed him but king is available via his soul.

# BigDecimal
  https://www.geeksforgeeks.org/bigdecimal-class-java/

# Need of wrapper class
  https://www.geeksforgeeks.org/need-of-wrapper-classes-in-java/
 
