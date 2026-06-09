# 55. Dispatchers & Context

A *dispatcher* decides which thread (or thread pool) a coroutine runs on. `Dispatchers.Default` is backed by a shared pool sized for CPU-intensive work, while `Dispatchers.IO` is optimized for blocking I/O like reading files or making network calls. Note: requires the kotlinx-coroutines-core dependency.

```kotlin
import kotlinx.coroutines.*

suspend fun loadData(): String =
    // withContext switches the dispatcher for this block,
    // then switches back when it returns.
    withContext(Dispatchers.IO) {
        delay(50)                       // pretend to read from disk/network
        "data"
    }

fun main() = runBlocking {
    println("start on main scope")

    // Run CPU work on the Default dispatcher.
    val computed = withContext(Dispatchers.Default) {
        (1..100).sum()
    }
    println("computed: $computed")

    // Run blocking I/O on the IO dispatcher.
    val data = loadData()
    println("loaded: $data")
}
```

`withContext` suspends the current coroutine, runs the block on the requested dispatcher, and resumes with its result — a clean way to move work onto the right pool. Because of this, a single coroutine can move between threads during its lifetime; the framework handles the hand-off for you.

Running it:

```
$ kotlin run
start on main scope
computed: 5050
loaded: data
```

[← Prev](54-async-await.md) | [Index](../README.md) | [Next →](56-channels.md)
