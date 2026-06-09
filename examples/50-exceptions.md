# 50. Exceptions

Kotlin handles errors with `try`/`catch`/`finally`. There are no checked exceptions, and `try` is an expression — it can produce a value. You raise an error with `throw`, and you can define your own exception by extending `Exception`.

```kotlin
class MyError(message: String) : Exception(message)

fun parsePositive(text: String): Int {
    val n = text.toIntOrNull() ?: throw MyError("not a number: $text")
    if (n < 0) throw MyError("negative: $n")
    return n
}

fun main() {
    // try/catch/finally
    try {
        val n = parsePositive("oops")
        println("parsed $n")
    } catch (e: MyError) {
        println("caught: ${e.message}")
    } finally {
        println("done parsing")
    }

    // try as an expression: it evaluates to a value.
    val value = try {
        parsePositive("42")
    } catch (e: MyError) {
        -1
    }
    println("value = $value")
}
```

The `finally` block always runs — after a successful `try`, after a caught exception, or while one propagates. When used as an expression, the value of `try` is the last expression of the block that completes (the `try` body, or the matching `catch`).

Running it:

```
$ kotlin run
caught: not a number: oops
done parsing
value = 42
```

[← Prev](49-inline-functions.md) | [Index](../README.md) | [Next →](51-result-runcatching.md)
