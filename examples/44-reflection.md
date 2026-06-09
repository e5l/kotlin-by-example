# 44. Reflection

Reflection inspects classes and members at runtime. `::class` gives a `KClass`, whose `simpleName` and `isInstance` work out of the box.

```kotlin
import kotlin.reflect.full.memberProperties

class Point(val x: Int, val y: Int)

fun main() {
    val point = Point(1, 2)
    val kClass = point::class            // a KClass instance

    println("class: ${kClass.simpleName}")
    println("is Point: ${kClass.isInstance(point)}")

    // .memberProperties comes from kotlin-reflect (kotlin.reflect.full.*)
    val names = Point::class.memberProperties.map { it.name }
    println("properties: $names")
}
```

`simpleName` and `isInstance` are part of the standard library, but richer introspection like `memberProperties` (from `kotlin.reflect.full.*`) requires the **kotlin-reflect** dependency on the classpath. Add `org.jetbrains.kotlin:kotlin-reflect` to your `module.yaml` `dependencies` to run the snippet above.

Running it:

```
$ kotlin run
class: Point
is Point: true
properties: [x, y]
```

[← Prev](43-annotations.md) | [Index](../README.md) | [Next →](45-scope-functions.md)
