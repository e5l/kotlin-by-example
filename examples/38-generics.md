# 38. Generics & Variance

Generics let functions and classes work over any type while staying type-safe. An upper bound like `<T : Comparable<T>>` constrains what `T` may be.

```kotlin
// generic function
fun <T> firstOf(items: List<T>): T = items[0]

// generic class
class Box<T>(val value: T)

// upper-bound constraint
fun <T : Comparable<T>> maxOf(a: T, b: T): T = if (a > b) a else b
```

Variance controls how generic types relate as their type arguments change. A producer that only **returns** `T` is declared `out` (covariant); a consumer that only **accepts** `T` is declared `in` (contravariant).

```kotlin
// 'out' = producer (covariant): can only return T
class Producer<out T>(private val value: T) {
    fun get(): T = value
}

// 'in' = consumer (contravariant): can only accept T
class Consumer<in T> {
    fun consume(item: T) = println("consumed $item")
}

fun main() {
    println(firstOf(listOf("a", "b")))
    println(Box(42).value)
    println(maxOf(3, 7))

    val producer: Producer<Any> = Producer<String>("hi")  // covariance
    println(producer.get())

    val consumer: Consumer<String> = Consumer<Any>()        // contravariance
    consumer.consume("ok")
}
```

The mnemonic is **producer-`out`, consumer-`in`**: a `Producer<String>` is safely a `Producer<Any>`, and a `Consumer<Any>` is safely a `Consumer<String>`.

Running it:

```
$ kotlin run
a
42
7
hi
consumed ok
```

[← Prev](37-extensions.md) | [Index](../README.md) | [Next →](39-reified.md)
