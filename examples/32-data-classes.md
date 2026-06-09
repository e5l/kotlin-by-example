# 32. Data Classes

A `data class` is meant to hold data. The compiler generates `toString`, `equals`/`hashCode`, `copy(...)`, and `componentN` functions from the properties in the primary constructor.

```kotlin
data class User(val name: String, val age: Int)

fun main() {
    val a = User("Alice", 30)
    val b = User("Alice", 30)

    println(a)                 // generated toString
    println(a == b)            // structural equality via equals

    val older = a.copy(age = 31)
    println(older)

    val (name, age) = a        // destructuring via componentN
    println("$name is $age")
}
```

`copy(...)` returns a new instance with selected properties changed, and the generated `component1`/`component2` functions enable destructuring declarations.

Running it:

```
$ kotlin run
User(name=Alice, age=30)
true
User(name=Alice, age=31)
Alice is 30
```

[← Prev](31-visibility.md) | [Index](../README.md) | [Next →](33-enum-classes.md)
