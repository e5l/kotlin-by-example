# 41. Inline Value Classes

A `@JvmInline value class` wraps a single value to gain a distinct type without the allocation cost of a normal wrapper — the compiler inlines the underlying value where it can.

```kotlin
@JvmInline
value class Password(val value: String)

@JvmInline
value class Email(val value: String)

fun register(email: Email, password: Password) {
    println("Registering ${email.value}")
}

fun main() {
    val email = Email("alice@example.com")
    val password = Password("s3cret")

    register(email, password)
    // register(password, email) would not compile: types can't be mixed up
    println(password.value)
}
```

Both classes wrap a `String`, yet `Email` and `Password` are distinct types — swapping their order in the call is a compile error. You get the safety of a wrapper type with (in most cases) no runtime overhead.

Running it:

```
$ kotlin run
Registering alice@example.com
s3cret
```

[← Prev](40-type-aliases.md) | [Index](../README.md) | [Next →](42-operator-overloading.md)
