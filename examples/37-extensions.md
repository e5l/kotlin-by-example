# 37. Extension Functions & Properties

Extensions let you add functions and properties to a type you don't own. Inside an extension, `this` refers to the receiver.

```kotlin
// extension function: adds behaviour without modifying String
fun String.shout() = uppercase() + "!"

// extension property: a custom getter, no backing field allowed
val String.firstChar: Char
    get() = this[0]

fun main() {
    val word = "hello"
    println(word.shout())
    println(word.firstChar)
    // the String class itself is unchanged; these resolve statically
}
```

Extensions don't actually modify the class — nothing is inserted into `String`. They are resolved statically at the call site, which is why an extension property cannot have a backing `field`.

Running it:

```
$ kotlin run
HELLO!
h
```

[← Prev](36-nested-inner-classes.md) | [Index](../README.md) | [Next →](38-generics.md)
