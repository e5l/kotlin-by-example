# 05. Type Checks & Casts

Use `is` and `!is` to test a value's type. After a successful `is` check, Kotlin smart-casts the value, so you can use it as that type without an explicit cast.

```kotlin
fun describe(x: Any): String {
    if (x is String) {
        // smart cast: x is treated as String here
        return "String of length ${x.length}"
    }
    if (x !is Int) {
        return "not an Int"
    }
    return "Int: $x"
}

fun main() {
    println(describe("hello"))
    println(describe(42))
    println(describe(3.14))

    val any: Any = "world"

    // Unsafe cast with as (throws if the type is wrong)
    val str: String = any as String
    println("forced length: ${str.length}")

    // Safe cast with as? returns null instead of throwing
    val n: Int? = any as? Int
    println("as? Int -> $n")
}
```

Running it:

```
$ kotlin run
String of length 5
Int: 42
not an Int
forced length: 5
as? Int -> null
```

[← Prev](04-basic-types.md) | [Index](../README.md) | [Next →](06-strings.md)
