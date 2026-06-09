# 51. Result & runCatching

Instead of propagating an exception, `runCatching { }` runs a block and captures the outcome in a `Result<T>` — either a success holding a value or a failure holding the thrown exception. You then inspect or transform it without a `try`/`catch`.

```kotlin
fun parse(text: String): Int = text.toInt()  // throws on bad input

fun main() {
    // runCatching wraps success or failure into a Result<T>.
    val ok: Result<Int> = runCatching { parse("21") }
    val bad: Result<Int> = runCatching { parse("nope") }

    // map transforms a success; getOrElse supplies a fallback.
    println(ok.map { it * 2 }.getOrElse { -1 })   // 42
    println(bad.map { it * 2 }.getOrElse { -1 })   // -1

    // getOrNull returns null on failure.
    println(ok.getOrNull())    // 21
    println(bad.getOrNull())   // null

    // onSuccess / onFailure run side-effects and return the Result.
    bad
        .onSuccess { println("got $it") }
        .onFailure { println("failed: ${it.message}") }
}
```

`map` applies only on success and leaves a failure untouched, while `getOrElse`, `getOrNull`, and `getOrThrow` extract the value. `onSuccess` and `onFailure` return the same `Result`, so they chain naturally for logging or recovery.

Running it:

```
$ kotlin run
42
-1
21
null
failed: For input string: "nope"
```

[← Prev](50-exceptions.md) | [Index](../README.md) | [Next →](52-coroutines-basics.md)
