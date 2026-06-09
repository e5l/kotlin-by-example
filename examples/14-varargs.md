# 14. Varargs

A `vararg` parameter accepts any number of arguments. Inside the function it behaves like an array.

```kotlin
fun sum(vararg numbers: Int): Int {
    var total = 0
    for (n in numbers) total += n
    return total
}

fun main() {
    // pass several arguments directly
    println(sum(1, 2, 3))
    println(sum(10, 20, 30, 40))

    // spread an existing array into the vararg with *
    val arr = intArrayOf(5, 5, 5)
    println(sum(*arr))
}
```

Running it:

```
$ kotlin run
6
100
15
```

[← Prev](13-default-named-args.md) | [Index](../README.md) | [Next →](15-infix-functions.md)
