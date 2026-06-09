# 35. Objects & Companion Objects

The `object` keyword declares a singleton. A `companion object` belongs to a class and is the place for factory functions. An object expression creates an anonymous one-off instance.

```kotlin
object Counter {
    var count = 0
    fun increment() { count++ }
}

class Logger private constructor(val tag: String) {
    companion object {
        fun create(tag: String) = Logger(tag)   // factory function
    }
    fun log(msg: String) = "[$tag] $msg"
}

interface Greeter {
    fun greet(): String
}

fun main() {
    Counter.increment()
    Counter.increment()
    println("count = ${Counter.count}")

    val logger = Logger.create("APP")
    println(logger.log("started"))

    // object expression: an anonymous object implementing Greeter
    val french = object : Greeter {
        override fun greet() = "Bonjour"
    }
    println(french.greet())
}
```

`Counter` is created lazily on first use and shared everywhere. The companion's `create` can reach the `private` constructor, and the object expression implements `Greeter` inline without naming a class.

Running it:

```
$ kotlin run
count = 2
[APP] started
Bonjour
```

[← Prev](34-sealed-classes.md) | [Index](../README.md) | [Next →](36-nested-inner-classes.md)
