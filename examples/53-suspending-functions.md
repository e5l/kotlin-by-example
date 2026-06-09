# 53. Suspending Functions

A function marked `suspend` can call other suspending functions (like `delay`) and be paused and resumed. Suspending functions can only be called from a coroutine or another suspending function. Note: requires the kotlinx-coroutines-core dependency.

```kotlin
import kotlinx.coroutines.*

suspend fun fetchUser(): String {
    delay(100)              // pretend to do I/O
    return "Alice"
}

suspend fun fetchGreeting(name: String): String {
    delay(100)              // pretend to do more I/O
    return "Hello, $name!"
}

fun main() = runBlocking {
    // By default the two suspend calls run sequentially:
    // fetchGreeting starts only after fetchUser returns.
    val user = fetchUser()
    val greeting = fetchGreeting(user)
    println(greeting)
}
```

Each call suspends until it completes before the next begins, so the total work is the sum of the two delays. This sequential ordering is the default and keeps code easy to read — like ordinary function calls, just non-blocking.

Running it:

```
$ kotlin run
Hello, Alice!
```

[← Prev](52-coroutines-basics.md) | [Index](../README.md) | [Next →](54-async-await.md)
