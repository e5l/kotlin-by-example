# 42. Operator Overloading

Functions marked `operator` with conventional names let your types work with built-in operators. `plus` backs `+`, `times` backs `*`, and `get` backs the `[]` indexing syntax.

```kotlin
data class Vec(val x: Int, val y: Int) {
    operator fun plus(other: Vec) = Vec(x + other.x, y + other.y)
    operator fun times(scale: Int) = Vec(x * scale, y * scale)
    operator fun get(index: Int) = if (index == 0) x else y
}

fun main() {
    val a = Vec(1, 2)
    val b = Vec(3, 4)

    println(a + b)        // calls plus
    println(a * 3)        // calls times
    println(a[0])         // calls get
}
```

`a + b` compiles to `a.plus(b)`, `a * 3` to `a.times(3)`, and `a[0]` to `a.get(0)`. The operator names are fixed, so the compiler knows which symbol each one maps to.

Running it:

```
$ kotlin run
Vec(x=4, y=6)
Vec(x=3, y=6)
1
```

[← Prev](41-value-classes.md) | [Index](../README.md) | [Next →](43-annotations.md)
