# 26. Classes & Constructors

A class declares its primary constructor right in the header, so parameters and properties live in one place. There is no `new` keyword — you call the class like a function.

```kotlin
class Person(val name: String, var age: Int) {
    val isAdult: Boolean

    init {
        isAdult = age >= 18
        println("Created $name")
    }

    // secondary constructor delegates to the primary one
    constructor(name: String) : this(name, 0)
}

fun main() {
    val alice = Person("Alice", 30)
    val baby = Person("Bob")
    println("${alice.name}, ${alice.age}, adult=${alice.isAdult}")
    println("${baby.name}, ${baby.age}, adult=${baby.isAdult}")
}
```

The `init {}` block runs as part of the primary constructor, so it sees the constructor parameters. A secondary `constructor` must delegate to the primary one with `this(...)`.

Running it:

```
$ kotlin run
Created Alice
Created Bob
Alice, 30, adult=true
Bob, 0, adult=false
```

[← Prev](25-sequences.md) | [Index](../README.md) | [Next →](27-properties.md)
