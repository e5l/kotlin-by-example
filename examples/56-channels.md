# 56. Channels

A `Channel` is a coroutine-friendly queue: one coroutine `send`s values and another `receive`s them, with suspension instead of blocking when the channel is empty or full. It is the streaming counterpart to a single `Deferred`. Note: requires the kotlinx-coroutines-core dependency.

```kotlin
import kotlinx.coroutines.*
import kotlinx.coroutines.channels.*

fun main() = runBlocking {
    val channel = Channel<Int>()

    // Producer: send a few squares, then close the channel.
    launch {
        for (x in 1..5) {
            channel.send(x * x)
        }
        channel.close()             // signals no more elements
    }

    // Consumer: iterate until the channel is closed.
    for (value in channel) {
        println(value)
    }
    println("done")
}
```

Each `send` suspends until the consumer is ready to `receive`, so values flow through in order. Calling `close()` marks the end of the stream; the `for` loop over the channel finishes cleanly once all sent values have been received.

Running it:

```
$ kotlin run
1
4
9
16
25
done
```

[← Prev](55-dispatchers-context.md) | [Index](../README.md) | [Next →](57-flows.md)
