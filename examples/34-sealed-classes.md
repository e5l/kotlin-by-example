# 34. Sealed Classes & Interfaces

A `sealed` type has a closed set of subtypes known at compile time. Because the compiler knows them all, a `when` that covers every case is exhaustive — no `else` branch required.

```kotlin
sealed interface Result

data class Success(val data: String) : Result
data class Failure(val error: String) : Result
data object Loading : Result

fun render(result: Result): String = when (result) {   // no else needed
    is Success -> "Data: ${result.data}"
    is Failure -> "Error: ${result.error}"
    Loading -> "Loading..."
}

fun main() {
    println(render(Success("hello")))
    println(render(Failure("oops")))
    println(render(Loading))
}
```

If you later add a new subtype, the `when` stops compiling until you handle it — a safety net that plain class hierarchies lack. A `sealed class` works the same way when you need shared state.

Running it:

```
$ kotlin run
Data: hello
Error: oops
Loading...
```

[← Prev](33-enum-classes.md) | [Index](../README.md) | [Next →](35-objects.md)
