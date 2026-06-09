# 04. Basic Types & Numbers

Kotlin's numeric types are `Byte`, `Short`, `Int`, `Long`, `Float`, and `Double`, plus `Boolean` and `Char`. Numbers have no implicit widening: you must convert explicitly.

```kotlin
fun main() {
    val b: Byte = 127
    val s: Short = 1000
    val i: Int = 1_000_000        // digit separator for readability
    val l: Long = 100L            // L suffix marks a Long literal
    val f: Float = 1.5f           // f suffix marks a Float literal
    val d: Double = 3.14159

    val active: Boolean = true
    val grade: Char = 'A'

    // No implicit widening: convert Int to Long explicitly
    val asLong: Long = i.toLong()

    println("$b $s $i $l $f $d")
    println("active=$active grade=$grade")
    println("asLong=$asLong")
}
```

Running it:

```
$ kotlin run
127 1000 1000000 100 1.5 3.14159
active=true grade=A
asLong=1000000
```

[← Prev](03-variables.md) | [Index](../README.md) | [Next →](05-type-checks-casts.md)
