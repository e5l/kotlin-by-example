# 24. Grouping & Aggregation

Beyond simple mapping and filtering, the standard library can organize elements into groups and collapse them into a single value.

```kotlin
fun main() {
    val words = listOf("apple", "banana", "avocado", "blueberry", "cherry")

    // groupBy builds a Map from a key to the list of matching elements
    println(words.groupBy { it.first() })

    // associateBy builds a Map from a key to a single element (last wins on clash)
    println(words.associateBy { it.length })

    // partition splits into (matching, non-matching)
    val (long, short) = words.partition { it.length > 5 }
    println(long)
    println(short)

    // fold and reduce collapse a collection into a single value:
    // fold takes an explicit initial value, reduce starts from the first element
    val numbers = listOf(1, 2, 3, 4, 5)
    println(numbers.fold(100) { acc, n -> acc + n })   // 100 + 1 + 2 + ... + 5
    println(numbers.reduce { acc, n -> acc * n })      // 1 * 2 * ... * 5
}
```

Running it:

```
$ kotlin run
{a=[apple, avocado], b=[banana, blueberry], c=[cherry]}
{5=apple, 6=cherry, 7=avocado, 9=blueberry}
[banana, avocado, blueberry, cherry]
[apple]
115
120
```

[← Prev](23-collection-ops.md) | [Index](../README.md) | [Next →](25-sequences.md)
