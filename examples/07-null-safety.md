# 07. Null Safety

A type like `String` can never hold `null`. To allow `null`, add a `?` to get a nullable type such as `String?`. Kotlin then forces you to handle the null case.

```kotlin
fun main() {
    val present: String? = "Kotlin"
    val absent: String? = null

    // Safe call: returns the property or null, never throws
    println(present?.length)
    println(absent?.length)

    // Elvis operator: provide a fallback when the left side is null
    val len = absent?.length ?: -1
    println("length or default: $len")

    // let runs the block only when the value is non-null
    present?.let { println("got a value: $it") }
    absent?.let { println("never printed") }

    // Not-null assertion !! throws NPE if the value is null; use sparingly
    println(present!!.uppercase())
}
```

Running it:

```
$ kotlin run
6
null
length or default: -1
got a value: Kotlin
KOTLIN
```

[← Prev](06-strings.md) | [Index](../README.md) | [Next →](08-equality.md)
