# 27. Properties & Accessors

Every Kotlin property has implicit accessors that you can override. Inside a custom `set(value)` you reach the stored value through the `field` keyword — the backing field.

```kotlin
class Rectangle(val width: Int, val height: Int) {
    // computed read-only property: no backing field
    val area: Int
        get() = width * height
}

class Temperature {
    var celsius: Double = 0.0
        set(value) {
            field = value          // 'field' is the backing field
            fahrenheit = value * 9 / 5 + 32
        }
    var fahrenheit: Double = 32.0
        private set
}

fun main() {
    val r = Rectangle(3, 4)
    println("area = ${r.area}")

    val t = Temperature()
    t.celsius = 100.0
    println("${t.celsius}C = ${t.fahrenheit}F")
}
```

A property whose value is derived from a `get()` — like `area` — has no backing field and is recomputed on each access. The `private set` modifier lets a property be read everywhere but written only inside the class.

Running it:

```
$ kotlin run
area = 12
100.0C = 212.0F
```

[← Prev](26-classes.md) | [Index](../README.md) | [Next →](28-inheritance.md)
