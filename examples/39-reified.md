# 39. Reified Type Parameters

On the JVM generic types are erased at runtime, so you normally can't write `T::class` or `is T`. Marking an `inline` function's parameter `reified` keeps the concrete type available at runtime.

```kotlin
// 'reified' keeps the type at runtime; normally generics are erased
inline fun <reified T> List<*>.filterByType(): List<T> =
    filterIsInstance<T>()

inline fun <reified T> typeName(): String = T::class.simpleName ?: "?"

fun main() {
    val mixed = listOf(1, "two", 3, "four", 5.0)
    println(mixed.filterByType<String>())
    println(mixed.filterByType<Int>())
    println("T is ${typeName<Double>()}")
}
```

Because the function is inlined at each call site, the compiler can substitute the real type — so `T::class` and `is T` checks (here via `filterIsInstance`) work. `reified` is only allowed on `inline` functions.

Running it:

```
$ kotlin run
[two, four]
[1, 3]
T is Double
```

[← Prev](38-generics.md) | [Index](../README.md) | [Next →](40-type-aliases.md)
