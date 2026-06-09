# 33. Enum Classes

An `enum class` defines a fixed set of constants. Each constant can carry constructor arguments, and the enum can declare methods shared by all of them.

```kotlin
enum class Planet(val gravity: Double) {
    EARTH(9.81),
    MARS(3.71),
    MOON(1.62);

    fun weightOf(massKg: Double) = massKg * gravity
}

fun main() {
    for (p in Planet.entries) {            // Kotlin 2.x: entries
        println("${p.name} #${p.ordinal} g=${p.gravity}")
    }
    val mars = Planet.valueOf("MARS")
    println("weight on Mars: ${mars.weightOf(80.0)}")

    val msg = when (mars) {
        Planet.EARTH -> "home"
        Planet.MARS, Planet.MOON -> "away"
    }
    println(msg)
}
```

`entries` (preferred in Kotlin 2.x over `values()`) lists all constants, `valueOf` looks one up by name, and each constant exposes `name` and `ordinal`. A `when` over an enum reads cleanly.

Running it:

```
$ kotlin run
EARTH #0 g=9.81
MARS #1 g=3.71
MOON #2 g=1.62
weight on Mars: 296.8
away
```

[← Prev](32-data-classes.md) | [Index](../README.md) | [Next →](34-sealed-classes.md)
