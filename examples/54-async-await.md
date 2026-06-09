# 54. async/await & Structured Concurrency

When you want results concurrently rather than sequentially, use `async`. It starts a coroutine and returns a `Deferred<T>` — a future-like handle whose `await()` suspends until the result is ready. Note: requires the kotlinx-coroutines-core dependency.

```kotlin
import kotlinx.coroutines.*

suspend fun loadPrice(item: String): Int {
    delay(100)              // pretend to query a service
    return item.length * 10
}

fun main() = runBlocking {
    // coroutineScope establishes structured concurrency:
    // it waits for all children before returning.
    val total = coroutineScope {
        val apples = async { loadPrice("apples") }   // starts concurrently
        val pears  = async { loadPrice("pears") }    // starts concurrently
        apples.await() + pears.await()               // combine the results
    }
    println("Total: $total")
}
```

Both `async` blocks start right away and run concurrently, so the two delays overlap instead of adding up. `await()` retrieves each result and the scope combines them.

`coroutineScope` is the heart of *structured concurrency*: every coroutine launched inside it is a child, the scope does not return until all children complete, and if one child fails the others are cancelled. This prevents leaked, orphaned coroutines.

Running it:

```
$ kotlin run
Total: 110
```

[← Prev](53-suspending-functions.md) | [Index](../README.md) | [Next →](55-dispatchers-context.md)
