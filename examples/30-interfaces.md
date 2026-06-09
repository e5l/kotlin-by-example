# 30. Interfaces

An `interface` can declare abstract methods, methods with a default body, and properties (without backing fields). A class can implement many interfaces.

```kotlin
interface Drivable {
    val wheels: Int            // property declaration
    fun drive(): String        // abstract
    fun honk() = "Beep!"       // default implementation
}

interface Trackable {
    fun location() = "0,0"
}

class Car : Drivable, Trackable {
    override val wheels = 4
    override fun drive() = "Driving on $wheels wheels"
}

fun main() {
    val car = Car()
    println(car.drive())
    println(car.honk())
    println(car.location())
}
```

`Car` overrides only what it must — the `wheels` property and `drive()`. The default `honk()` and `location()` are inherited as-is.

Running it:

```
$ kotlin run
Driving on 4 wheels
Beep!
0,0
```

[← Prev](29-abstract-classes.md) | [Index](../README.md) | [Next →](31-visibility.md)
