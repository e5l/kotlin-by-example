# 31. Visibility Modifiers

Kotlin has four visibility modifiers: `public` (the default), `private`, `protected`, and `internal` (visible within the same module). Use them to expose a small public API while hiding internal state.

```kotlin
class BankAccount(private var balance: Int) {
    fun deposit(amount: Int) {       // public by default
        balance += amount
    }
    fun balance(): Int = balance
}

internal fun helper() = "module-internal"

fun main() {
    val account = BankAccount(100)
    account.deposit(50)
    // account.balance is private: this would not compile:
    // println(account.balance)
    println(account.balance())
    println(helper())
}
```

The `balance` field is `private`, so the only way in is through the public `deposit()` and `balance()`. `protected` works like `private` but is also visible to subclasses, and `internal` limits visibility to the current module.

Running it:

```
$ kotlin run
150
module-internal
```

[← Prev](30-interfaces.md) | [Index](../README.md) | [Next →](32-data-classes.md)
