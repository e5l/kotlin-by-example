# 40. Type Aliases

A `typealias` gives an existing type a shorter or more meaningful name. It introduces no new type — just an alternative spelling — which is handy for function types and verbose generics.

```kotlin
typealias Handler = (String) -> Unit
typealias StringMap = Map<String, String>

fun onEvent(name: String, handler: Handler) = handler(name)

fun main() {
    val log: Handler = { event -> println("event: $event") }
    onEvent("click", log)

    val config: StringMap = mapOf("host" to "localhost", "port" to "8080")
    println(config["host"])
}
```

`Handler` reads better than `(String) -> Unit` in a signature, and `StringMap` keeps `Map<String, String>` from cluttering the code. At runtime they are exactly their underlying types.

Running it:

```
$ kotlin run
event: click
localhost
```

[← Prev](39-reified.md) | [Index](../README.md) | [Next →](41-value-classes.md)
