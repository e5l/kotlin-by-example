# 23. Collection Operations

The standard library ships rich operations for transforming and querying collections. They all take lambdas and return new results, leaving the source untouched.

```kotlin
fun main() {
    val numbers = listOf(1, 2, 3, 4, 5, 6)

    println(numbers.map { it * it })        // transform each element
    println(numbers.filter { it % 2 == 0 }) // keep matching elements
    println(numbers.any { it > 5 })         // is any true?
    println(numbers.all { it > 0 })         // are all true?
    println(numbers.none { it < 0 })        // are none true?
    println(numbers.find { it > 3 })        // first match, or null
    println(numbers.count { it % 2 == 0 })  // how many match?
    println(numbers.sumOf { it })           // total

    // because each operation returns a collection, you can chain them
    val result = numbers.filter { it % 2 == 0 }.map { it * 10 }
    println(result)
}
```

Running it:

```
$ kotlin run
[1, 4, 9, 16, 25, 36]
[2, 4, 6]
true
true
true
4
3
21
[20, 40, 60]
```

[← Prev](22-maps.md) | [Index](../README.md) | [Next →](24-grouping-aggregation.md)
