# 60. Regular Expressions

Kotlin wraps Java's regex engine in the `Regex` class. Triple-quoted strings are handy for patterns because you don't have to escape backslashes twice.

```kotlin
fun main() {
    val phone = Regex("""\d{3}-\d{4}""")
    println(phone.matches("555-1234"))   // matches the whole input
    println(phone.matches("hello"))

    val text = "Contact: alice@example.com and bob@test.org"
    val email = Regex("""(\w+)@(\w+\.\w+)""")

    val first = email.find(text)         // first match, or null
    println(first?.value)

    for (m in email.findAll(text)) {     // every match, lazily
        val (user, domain) = m.destructured  // capture groups 1 and 2
        println("user=$user domain=$domain")
    }
}
```

`groupValues` and `destructured` expose capture groups; group `0` is the full match. `replace` can take a lambda so the replacement can depend on what matched.

```kotlin
val masked = email.replace(text) { "<${it.groupValues[2]}>" }
println(masked)
```

Running it:

```
$ kotlin run
true
false
alice@example.com
user=alice domain=example.com
user=bob domain=test.org
Contact: <example.com> and <test.org>
```

[← Prev](59-json.md) | [Index](../README.md) | [Next →](61-string-formatting.md)
