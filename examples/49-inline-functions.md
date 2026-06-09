# 49. Inline Functions

Marking a higher-order function `inline` tells the compiler to copy its body — and the bodies of its lambda arguments — directly into each call site. This avoids allocating a function object for the lambda and, as a bonus, allows **non-local returns** from inside the lambda.

```kotlin
inline fun measure(label: String, block: () -> Unit) {
    val start = System.nanoTime()
    block()
    val elapsed = System.nanoTime() - start
    println("$label finished (elapsed ${if (elapsed >= 0) ">= 0" else "?"} ns)")
}

inline fun firstEven(numbers: List<Int>): Int? {
    numbers.forEach {
        if (it % 2 == 0) return it   // non-local return, enabled by inlining
    }
    return null
}

fun main() {
    measure("sum") {
        var sum = 0
        for (i in 1..1000) sum += i
        println("sum = $sum")
    }

    println("first even: ${firstEven(listOf(1, 3, 4, 7))}")
}
```

Because the lambda is inlined, the `return it` inside `forEach` returns from `firstEven` itself, not just from the lambda. Two modifiers tune this behavior: mark a lambda parameter `noinline` to keep it as a real function object (for example, to store or pass it on), and `crossinline` to forbid non-local returns when the lambda will be invoked from another execution context.

Running it:

```
$ kotlin run
sum = 500500
sum finished (elapsed >= 0 ns)
first even: 4
```

[← Prev](48-property-delegation.md) | [Index](../README.md) | [Next →](50-exceptions.md)
