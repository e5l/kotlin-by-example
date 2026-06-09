# 03. Variables

Kotlin has two kinds of variable declarations: `val` for read-only (assign once) and `var` for mutable. Prefer `val` whenever you can.

```kotlin
fun main() {
    // Read-only: type inferred as String
    val greeting = "Hello"

    // Explicit type annotation
    val n: Int = 5

    // Mutable: can be reassigned
    var count = 0
    println("count before: $count")
    count = n
    println("count after: $count")

    // Reassigning a val is a compile error:
    // greeting = "Hi"  // error: val cannot be reassigned

    println("$greeting, you have $count messages")
}
```

Running it:

```
$ kotlin run
count before: 0
count after: 5
Hello, you have 5 messages
```

[← Prev](02-values.md) | [Index](../README.md) | [Next →](04-basic-types.md)
