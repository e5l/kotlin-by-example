# 20. Lists

A `List` is an ordered collection. `listOf` returns a read-only `List`, while `mutableListOf` gives you one you can modify.

```kotlin
fun main() {
    val colors = listOf("red", "green", "blue")
    println(colors[0])      // index access
    println(colors.first())
    println(colors.last())
    println(colors.size)

    val numbers = mutableListOf(1, 2, 3)
    numbers.add(4)
    numbers.remove(2)
    println(numbers)
}
```

The `List` returned by `listOf` is read-only: it exposes no `add` or `remove`, so the contents are stable. Choose `mutableListOf` only when you genuinely need to change the collection after creation.

Running it:

```
$ kotlin run
red
red
blue
3
[1, 3, 4]
```

[← Prev](19-arrays.md) | [Index](../README.md) | [Next →](21-sets.md)
