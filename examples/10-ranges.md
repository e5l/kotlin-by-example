# 10. Ranges & Progressions

Ranges describe a sequence of values with a start and an end. They power `for` loops, membership checks, and more.

```kotlin
fun main() {
    // closed range: 1, 2, ..., 5
    println((1..5).joinToString())

    // half-open range with until: stops before 5
    println((1 until 5).joinToString())

    // counting down
    println((10 downTo 1).joinToString())

    // a step changes the increment
    println((0..10 step 2).joinToString())

    // membership test
    val x = 7
    println("$x in 1..10 -> ${x in 1..10}")

    // ranges also work on Char
    println(('a'..'e').joinToString(""))
}
```

Running it:

```
$ kotlin run
1, 2, 3, 4, 5
1, 2, 3, 4
10, 9, 8, 7, 6, 5, 4, 3, 2, 1
0, 2, 4, 6, 8, 10
7 in 1..10 -> true
abcde
```

[← Prev](09-if-when.md) | [Index](../README.md) | [Next →](11-loops.md)
