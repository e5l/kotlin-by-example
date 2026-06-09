# 11. Loops & Labels

Kotlin offers `for`, `while`, and `do-while` loops. Labels let `break` and `continue` target an outer loop.

```kotlin
fun main() {
    // for over a range
    for (i in 1..3) print("$i ")
    println()

    // for over a list
    val fruits = listOf("apple", "pear", "plum")
    for (fruit in fruits) print("$fruit ")
    println()

    // for with index and value via withIndex()
    for ((index, fruit) in fruits.withIndex()) {
        println("$index: $fruit")
    }

    // while and do-while
    var n = 3
    while (n > 0) { print("$n "); n-- }
    println()
    do { print("go "); n++ } while (n < 2)
    println()
}
```

A label like `outer@` lets an inner `break` or `continue` jump out of the enclosing loop.

```kotlin
fun main() {
    outer@ for (i in 1..3) {
        for (j in 1..3) {
            if (i + j == 4) continue@outer
            if (i == 3) break@outer
            println("i=$i j=$j")
        }
    }
}
```

Running it:

```
$ kotlin run
1 2 3 
apple pear plum 
0: apple
1: pear
2: plum
3 2 1 
go go 
```

[← Prev](10-ranges.md) | [Index](../README.md) | [Next →](12-functions.md)
