# 57. Flows

A `Flow` represents an asynchronous stream of values produced over time. Unlike a channel, a flow is *cold*: the code inside `flow { }` does not run until you `collect` it, and it runs again for each collector. Note: requires the kotlinx-coroutines-core dependency.

```kotlin
import kotlinx.coroutines.*
import kotlinx.coroutines.flow.*

fun numbers(): Flow<Int> = flow {
    for (i in 1..5) {
        delay(50)               // emit values over time, suspending in between
        emit(i)                 // hand a value to the collector
    }
}

fun main() = runBlocking {
    numbers()
        .filter { it % 2 == 1 } // keep odd numbers
        .map { it * it }        // square them
        .collect { println(it) }  // terminal operator: starts the flow
}
```

Intermediate operators like `map` and `filter` build a new flow lazily and declare *what* to do; nothing happens until a terminal operator such as `collect` runs. Each emitted value passes through the operator chain in order, so `1, 3, 5` are squared into `1, 9, 25`.

Running it:

```
$ kotlin run
1
9
25
```

[← Prev](56-channels.md) | [Index](../README.md) | [Next →](58-files.md)
