# 45. Scope Functions

The standard library offers five scope functions — `let`, `run`, `with`, `apply`, and `also` — that execute a block of code in the context of an object. They differ in two ways: how the object is referenced inside the block (as `this` or as `it`) and what the block returns (the lambda result or the object itself).

| Function | Object reference | Returns        |
|----------|------------------|----------------|
| `let`    | `it`             | lambda result  |
| `run`    | `this`           | lambda result  |
| `with`   | `this`           | lambda result  |
| `apply`  | `this`           | the object     |
| `also`   | `it`             | the object     |

```kotlin
class Config {
    var host: String = ""
    var port: Int = 0
}

fun main() {
    // let: receiver is `it`, returns lambda result. Great for null checks.
    val name: String? = "Kotlin"
    val length = name?.let {
        println("got: $it")
        it.length
    }
    println("length: $length")

    // run: receiver is `this`, returns lambda result.
    val area = run {
        val w = 4
        val h = 5
        w * h
    }
    println("area: $area")

    // with: receiver is `this` (passed as argument), returns lambda result.
    val cfg = Config()
    val summary = with(cfg) {
        host = "localhost"
        port = 8080
        "$host:$port"
    }
    println("summary: $summary")

    // apply: receiver is `this`, returns the object. Ideal for configuring.
    val server = Config().apply {
        host = "example.com"
        port = 443
    }
    println("server: ${server.host}:${server.port}")

    // also: receiver is `it`, returns the object. Ideal for side-effects.
    val numbers = mutableListOf(1, 2, 3).also {
        println("created list of size ${it.size}")
    }
    println("numbers: $numbers")
}
```

In practice: reach for `?.let { }` to run code only on a non-null value, `apply { }` to configure a freshly created object and get it back, and `also { }` to slip in a side-effect (logging, validation) without changing the value flowing through.

Running it:

```
$ kotlin run
got: Kotlin
length: 6
area: 20
summary: localhost:8080
server: example.com:443
created list of size 3
numbers: [1, 2, 3]
```

[← Prev](44-reflection.md) | [Index](../README.md) | [Next →](46-destructuring.md)
