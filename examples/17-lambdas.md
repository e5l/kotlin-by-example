# 17. Lambdas & Higher-Order Functions

A lambda is a function written as an expression: `{ x -> x + 1 }`. A higher-order function takes a function as a parameter (or returns one), so lambdas can be passed around like values.

```kotlin
// higher-order function: f is a function from Int to Int
fun apply(x: Int, f: (Int) -> Int): Int = f(x)

fun isEven(n: Int): Boolean = n % 2 == 0

fun main() {
    // explicit lambda with a named parameter
    println(apply(4) { x -> x * x })

    // a single-parameter lambda can use the implicit name `it`
    println(apply(5) { it + 1 })

    // trailing-lambda syntax: the lambda above sits outside the parentheses
    val doubled = listOf(1, 2, 3).map { it * 2 }
    println(doubled)

    // function references with :: pass an existing function as a value
    println(listOf(1, 2, 3, 4).filter(::isEven))
    println(listOf("a", "b").map(String::uppercase))
}
```

Running it:

```
$ kotlin run
16
6
[2, 4, 6]
[2, 4]
[A, B]
```

[← Prev](16-recursion.md) | [Index](../README.md) | [Next →](18-closures.md)
