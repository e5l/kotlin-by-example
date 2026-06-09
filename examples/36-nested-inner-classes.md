# 36. Nested & Inner Classes

A class declared inside another is nested and has no link to the outer instance. Add the `inner` keyword and it carries a reference to the outer object, reachable via `this@Outer`.

```kotlin
class Outer {
    private val secret = "outer-data"

    // nested: NO access to Outer's members
    class Nested {
        fun describe() = "I'm nested and cannot see Outer's state"
    }

    // inner: holds a reference to the outer instance
    inner class Inner {
        fun describe() = "I can see: $secret (via this@Outer)"
    }
}

fun main() {
    println(Outer.Nested().describe())   // no Outer instance needed
    println(Outer().Inner().describe())  // needs an Outer instance
}
```

`Nested` is created straight from the class, while `Inner` must be created from an existing `Outer` instance — that is what gives it access to `secret`.

Running it:

```
$ kotlin run
I'm nested and cannot see Outer's state
I can see: outer-data (via this@Outer)
```

[← Prev](35-objects.md) | [Index](../README.md) | [Next →](37-extensions.md)
