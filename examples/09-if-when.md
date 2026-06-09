# 09. If & When

In Kotlin `if` is an expression that returns a value, and `when` is a powerful, flexible replacement for the classic `switch`.

```kotlin
fun main() {
    val a = 7
    val b = 12

    // if as an expression: the chosen branch value is returned
    val max = if (a > b) a else b
    println("max = $max")

    // when matching a value, with multiple values per branch
    val grade = 84
    val letter = when (grade) {
        in 90..100 -> "A"
        in 80..89 -> "B"
        in 70..79 -> "C"
        else -> "F"
    }
    println("grade $grade -> $letter")
}
```

`when` can also be used without a subject, where each branch is a boolean condition. This replaces long `if`/`else if` chains, and like `if` it can return a value.

```kotlin
fun describe(n: Int): String = when {
    n < 0 -> "negative"
    n == 0 -> "zero"
    n % 2 == 0 -> "positive even"
    else -> "positive odd"
}

fun main() {
    for (n in listOf(-3, 0, 4, 7)) {
        println("$n is ${describe(n)}")
    }
}
```

Running it:

```
$ kotlin run
max = 12
grade 84 -> B
```

[← Prev](08-equality.md) | [Index](../README.md) | [Next →](10-ranges.md)
