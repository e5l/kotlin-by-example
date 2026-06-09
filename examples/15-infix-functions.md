# 15. Infix Functions

A function marked `infix` can be called without the dot and parentheses, reading like a natural-language operator. It must be a member or an extension with a single parameter.

```kotlin
infix fun Int.pow(exponent: Int): Int {
    var result = 1
    repeat(exponent) { result *= this }
    return result
}

fun main() {
    // infix call: no dot, no parentheses
    println(2 pow 10)

    // equivalent ordinary call
    println(2.pow(10))

    // the standard library's `to` is an infix function building a Pair
    val pair = 1 to "one"
    println(pair)
}
```

Running it:

```
$ kotlin run
1024
1024
(1, one)
```

[← Prev](14-varargs.md) | [Index](../README.md) | [Next →](16-recursion.md)
