# 61. String Formatting

Kotlin exposes Java's `printf`-style formatting through the `format` extension on `String`, plus padding and joining helpers that cover most everyday needs.

```kotlin
fun main() {
    val pi = 3.14159
    println("%.2f".format(pi))          // two decimal places
    println(String.format("%05d", 42))   // zero-padded width 5
    println("%-8s|".format("left"))      // left-justified in width 8
    println("%8s|".format("right"))      // right-justified in width 8
}
```

For non-numeric alignment, `padStart` and `padEnd` pad a string to a target length with a chosen character. `joinToString` builds a single string from a collection with a `separator`, `prefix`, and `postfix`.

```kotlin
println("7".padStart(3, '0'))
println("hi".padEnd(5, '.') + "|")

val nums = listOf(1, 2, 3)
println(nums.joinToString(separator = ", ", prefix = "[", postfix = "]"))
```

Running it:

```
$ kotlin run
3.14
00042
left    |
   right|
007
hi...|
[1, 2, 3]
```

[← Prev](60-regex.md) | [Index](../README.md) | [Next →](62-sorting.md)
