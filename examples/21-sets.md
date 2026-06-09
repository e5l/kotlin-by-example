# 21. Sets

A `Set` is an unordered collection that holds no duplicates. `setOf` builds a read-only set and silently drops repeated elements.

```kotlin
fun main() {
    val primes = setOf(2, 3, 5, 3, 2)   // duplicates removed
    println(primes)
    println(5 in primes)                // membership test

    val evens = mutableSetOf(2, 4)
    evens.add(6)
    evens.add(4)                        // already present, ignored
    println(evens)

    // sets support the usual mathematical operations
    val a = setOf(1, 2, 3)
    val b = setOf(3, 4, 5)
    println(a union b)                  // infix syntax
    println(a intersect b)
}
```

Running it:

```
$ kotlin run
[2, 3, 5]
true
[2, 4, 6]
[1, 2, 3, 4, 5]
[3]
```

[← Prev](20-lists.md) | [Index](../README.md) | [Next →](22-maps.md)
