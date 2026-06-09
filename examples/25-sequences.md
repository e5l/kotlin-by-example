# 25. Sequences

Operations on a `List` are eager: each step builds a new list. A `Sequence` is lazy instead, processing elements one at a time and only as far as a terminal operation demands.

```kotlin
fun main() {
    val numbers = listOf(1, 2, 3, 4, 5)

    // intermediate map/filter are lazy; toList() is the terminal step
    val result = numbers.asSequence()
        .map { it * 2 }
        .filter { it > 4 }
        .toList()
    println(result)
}
```

Laziness means elements flow through the whole pipeline one by one, and processing stops as soon as the result is found. Here a `println` inside `map` reveals that only the first two elements are touched before `first` returns.

```kotlin
fun main() {
    val numbers = listOf(1, 2, 3, 4, 5)
    val firstEvenSquare = numbers.asSequence()
        .map {
            println("mapping $it")
            it * it
        }
        .first { it % 2 == 0 }
    println("result: $firstEvenSquare")

    // generateSequence produces values on demand, so it can be infinite
    val naturals = generateSequence(1) { it + 1 }
    println(naturals.take(5).toList())
}
```

Running it:

```
$ kotlin run
[6, 8, 10]
mapping 1
mapping 2
result: 4
[1, 2, 3, 4, 5]
```

[← Prev](24-grouping-aggregation.md) | [Index](../README.md) | [Next →](26-classes.md)
