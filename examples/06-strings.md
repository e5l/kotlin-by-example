# 06. Strings & Templates

String templates embed values directly: `$name` for a simple variable and `${expr}` for an expression. Strings also expose handy operations like `length`, `uppercase()`, and indexing.

```kotlin
fun main() {
    val name = "Kotlin"
    val version = 2

    // Templates
    println("Hello, $name!")
    println("Version $version.x has ${name.length} letters")

    // Common operations
    println(name.uppercase())
    println(name[0])           // first character

    // Triple-quoted multiline string; trimIndent() drops common indentation
    val poem = """
        Roses are red,
        Kotlin is keen,
        null is handled,
        code stays clean.
    """.trimIndent()
    println(poem)
}
```

Running it:

```
$ kotlin run
Hello, Kotlin!
Version 2.x has 6 letters
KOTLIN
K
Roses are red,
Kotlin is keen,
null is handled,
code stays clean.
```

[← Prev](05-type-checks-casts.md) | [Index](../README.md) | [Next →](07-null-safety.md)
