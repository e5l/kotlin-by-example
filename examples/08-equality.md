# 08. Equality

Kotlin distinguishes two kinds of equality. Structural equality `==` calls `equals` and compares content. Referential equality `===` checks whether two references point to the same instance.

```kotlin
data class Point(val x: Int, val y: Int)

fun main() {
    val a = Point(1, 2)
    val b = Point(1, 2)   // different instance, same content
    val c = a             // same instance as a

    // == compares content (data classes generate equals)
    println(a == b)       // true
    // === compares identity
    println(a === b)      // false

    // c refers to the very same object as a
    println(a === c)      // true

    // Strings work the same way
    val s1 = StringBuilder("hi").toString()
    val s2 = StringBuilder("hi").toString()
    println(s1 == s2)     // true: same characters
    println(s1 === s2)    // false: distinct String objects
}
```

Running it:

```
$ kotlin run
true
false
true
true
false
```

[← Prev](07-null-safety.md) | [Index](../README.md) | [Next →](09-if-when.md)
