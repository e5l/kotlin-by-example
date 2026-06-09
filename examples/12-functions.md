# 12. Functions

Functions are declared with `fun`. They can have a block body with an explicit return type, a concise single-expression body, or return `Unit` when there is no useful value.

```kotlin
// normal function with parameters and a return type
fun greet(name: String, times: Int): String {
    return "Hello, $name!".repeat(times)
}

// single-expression function: type is inferred, no braces or return
fun square(x: Int) = x * x

// a function that returns nothing useful returns Unit (implicitly)
fun logLine(message: String) {
    println("[log] $message")
}

fun main() {
    println(greet("Kotlin", 2))
    println("square(5) = ${square(5)}")
    logLine("done")
}
```

Running it:

```
$ kotlin run
Hello, Kotlin!Hello, Kotlin!
square(5) = 25
[log] done
```

[← Prev](11-loops.md) | [Index](../README.md) | [Next →](13-default-named-args.md)
