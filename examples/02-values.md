# 02. Values

Kotlin has literal values for numbers, booleans, characters, and strings, plus the usual operators that combine them.

```kotlin
fun main() {
    // Integer arithmetic
    println(1 + 1)

    // Float division keeps the fractional part
    println(7.0 / 2)

    // Boolean operators: && (and), || (or)
    println(true && false)
    println(true || false)

    // String concatenation with +
    println("Kotlin" + " " + "rocks")

    // A single character literal uses single quotes
    println('K')
}
```

Note that `7 / 2` (both `Int`) would truncate to `3`; using `7.0` makes it floating-point division.

Running it:

```
$ kotlin run
2
3.5
false
true
Kotlin rocks
K
```

[← Prev](01-hello-world.md) | [Index](../README.md) | [Next →](03-variables.md)
