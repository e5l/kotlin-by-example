# 46. Destructuring Declarations

A destructuring declaration unpacks an object into several variables at once. Any type that provides `component1()`, `component2()`, and so on supports it — `data class` types and `Pair`/`Triple` get these for free.

```kotlin
data class User(val name: String, val age: Int, val city: String)

fun main() {
    // Destructure a data class into separate vals.
    val user = User("Ada", 36, "London")
    val (name, age, city) = user
    println("$name, $age, $city")

    // Skip a component you don't need with `_`.
    val (n, _, c) = user
    println("$n lives in $c")

    // Pair and Triple destructure too.
    val (x, y) = Pair(10, 20)
    println("x=$x y=$y")
    val (r, g, b) = Triple(255, 128, 0)
    println("rgb($r, $g, $b)")

    // Destructure map entries in a for-loop.
    val capitals = mapOf("France" to "Paris", "Japan" to "Tokyo")
    for ((country, capital) in capitals) {
        println("$country -> $capital")
    }
}
```

The names you choose are positional, not matched by field name — `component1()` always feeds the first variable. Use `_` to ignore a position you don't need.

Running it:

```
$ kotlin run
Ada, 36, London
Ada lives in London
x=10 y=20
rgb(255, 128, 0)
France -> Paris
Japan -> Tokyo
```

[← Prev](45-scope-functions.md) | [Index](../README.md) | [Next →](47-class-delegation.md)
