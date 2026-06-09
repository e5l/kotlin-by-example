# 28. Inheritance & Overriding

Classes and members are `final` by default. Mark a class `open` to allow subclassing and a function `open` to allow overriding. A subclass calls its base constructor in the header and reaches the parent's implementation with `super.`.

```kotlin
open class Animal(val name: String) {
    open fun sound(): String = "..."
}

class Dog(name: String) : Animal(name) {
    override fun sound(): String = super.sound() + " Woof"
}

fun main() {
    val a: Animal = Dog("Rex")
    println("${a.name} says ${a.sound()}")
}
```

The `override` keyword is mandatory, and `Dog` passes `name` up to `Animal(name)`.

Running it:

```
$ kotlin run
Rex says ... Woof
```

[← Prev](27-properties.md) | [Index](../README.md) | [Next →](29-abstract-classes.md)
