# 47. Class Delegation

Kotlin supports the delegation pattern as a first-class language feature. With `class Derived(b: Base) : Base by b`, the compiler generates forwarding methods that delegate every member of `Base` to `b` — no hand-written boilerplate.

```kotlin
interface Base {
    fun greet()
    fun describe()
}

class BaseImpl(private val value: Int) : Base {
    override fun greet() = println("Hello from BaseImpl")
    override fun describe() = println("value is $value")
}

// `by b` forwards every Base method to b — no boilerplate.
// We override just greet(); describe() is still delegated.
class Derived(b: Base) : Base by b {
    override fun greet() = println("Hello from Derived")
}

fun main() {
    val base = BaseImpl(42)
    val derived = Derived(base)
    derived.greet()     // overridden
    derived.describe()  // delegated to BaseImpl
}
```

Any member you declare in `Derived` takes precedence over the generated delegate, so you override only what you want to change. This composes behavior without inheritance and keeps the wrapped object's implementation intact.

Running it:

```
$ kotlin run
Hello from Derived
value is 42
```

[← Prev](46-destructuring.md) | [Index](../README.md) | [Next →](48-property-delegation.md)
