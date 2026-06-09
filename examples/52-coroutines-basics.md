# 52. Coroutines Basics

A coroutine is a suspendable computation: it can pause without blocking a thread and resume later. `runBlocking` bridges normal code into the coroutine world, `launch` starts a new coroutine, and `delay` suspends it without blocking the underlying thread. Note: requires the kotlinx-coroutines-core dependency.

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    // launch starts a coroutine that runs concurrently with the rest.
    launch {
        delay(100)              // suspends this coroutine, not the thread
        println("World!")
    }
    println("Hello,")           // runs while the launched coroutine is delayed
}
```

Because `delay` only suspends the launched coroutine, `main` continues and prints `Hello,` first; once the delay elapses, the coroutine resumes and prints `World!`. `runBlocking` waits for its children to finish before returning.

Coroutines are lightweight — far cheaper than threads — so you can launch thousands of them at once.

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    // Launch 50_000 coroutines; each just prints a dot after a short delay.
    repeat(50_000) {
        launch {
            delay(10)
            print(".")
        }
    }
}
```

Running it:

```
$ kotlin run
Hello,
World!
```

[← Prev](51-result-runcatching.md) | [Index](../README.md) | [Next →](53-suspending-functions.md)
