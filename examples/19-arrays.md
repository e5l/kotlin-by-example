# 19. Arrays

An array holds a fixed number of values of the same type. Use `arrayOf` for object arrays and the specialized builders like `intArrayOf` for primitives, which avoid boxing.

```kotlin
fun main() {
    val fruits = arrayOf("apple", "banana", "cherry")
    val numbers = intArrayOf(1, 2, 3)
    val squares = IntArray(5) { it * it }   // built from an index lambda

    println(fruits[0])              // index access
    println(numbers.size)
    println(squares.joinToString())

    for (fruit in fruits) {
        println(fruit)
    }
}
```

Arrays have a fixed size: once created you can change elements via `array[i] = ...`, but you cannot grow or shrink them. When you need a resizable collection, reach for a `List` instead.

Running it:

```
$ kotlin run
apple
3
0, 1, 4, 9, 16
apple
banana
cherry
```

[← Prev](18-closures.md) | [Index](../README.md) | [Next →](20-lists.md)
