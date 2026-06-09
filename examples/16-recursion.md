# 16. Recursion & tailrec

A recursive function calls itself. Deep recursion can overflow the call stack, so Kotlin offers the `tailrec` modifier: when the recursive call is the last operation, the compiler rewrites it into a loop.

```kotlin
// plain recursion: each call waits for the next, using stack frames
fun factorial(n: Int): Long =
    if (n <= 1) 1 else n * factorial(n - 1)

// tailrec: the recursive call is the final action, so it compiles to a loop
// and will not overflow the stack even for large inputs
tailrec fun factorialAcc(n: Int, acc: Long = 1): Long =
    if (n <= 1) acc else factorialAcc(n - 1, acc * n)

fun main() {
    println(factorial(5))
    println(factorialAcc(5))
    // safe for large n thanks to tailrec
    println(factorialAcc(20))
}
```

Running it:

```
$ kotlin run
120
120
2432902008176640000
```

[← Prev](15-infix-functions.md) | [Index](../README.md) | [Next →](17-lambdas.md)
