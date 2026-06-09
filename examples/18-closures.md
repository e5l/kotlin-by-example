# 18. Closures

A lambda can capture variables from the scope where it is defined. Unlike Java, Kotlin closures capture the variable itself, so a lambda can read and even mutate a `var` from the enclosing scope.

```kotlin
fun makeCounter(): () -> Int {
    var count = 0          // captured by the lambda below
    return {
        count++            // mutates the captured variable
        count
    }
}

fun main() {
    val next = makeCounter()
    // each call advances the same captured count
    println(next())
    println(next())
    println(next())

    // a separate counter has its own independent state
    val other = makeCounter()
    println(other())
}
```

Running it:

```
$ kotlin run
1
2
3
1
```

[← Prev](17-lambdas.md) | [Index](../README.md) | [Next →](19-arrays.md)
