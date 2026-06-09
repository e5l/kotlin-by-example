# 29. Abstract Classes

An `abstract class` cannot be instantiated and may declare `abstract` members that subclasses must implement. It can also provide concrete members that build on those abstract ones.

```kotlin
abstract class Shape(val name: String) {
    abstract fun area(): Double                   // must be implemented
    fun describe() = "$name has area ${area()}"   // concrete
}

class Circle(val radius: Double) : Shape("Circle") {
    override fun area() = Math.PI * radius * radius
}

fun main() {
    val shape: Shape = Circle(2.0)
    println(shape.describe())
}
```

`describe()` is fully defined in `Shape`, yet it calls the abstract `area()` — the concrete subclass supplies that piece.

Running it:

```
$ kotlin run
Circle has area 12.566370614359172
```

[← Prev](28-inheritance.md) | [Index](../README.md) | [Next →](30-interfaces.md)
