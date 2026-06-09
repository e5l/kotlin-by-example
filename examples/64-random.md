# 64. Random

`kotlin.random.Random` is the multiplatform random generator. Seeding it with `Random(seed)` makes the sequence reproducible — every run with the same seed produces the same values, which is exactly what we want for a deterministic example (and for tests).

```kotlin
import kotlin.random.Random

fun main() {
    val rng = Random(42)

    println(rng.nextInt(100))        // 0 until 100
    println(rng.nextInt(10, 20))     // 10 until 20
    println(rng.nextDouble())        // 0.0 until 1.0

    val colors = listOf("red", "green", "blue", "yellow")
    println(colors.random(rng))      // pick one element
    println(colors.shuffled(rng))    // a new shuffled list
}
```

The collection helpers `random` and `shuffled` accept a `Random` instance, so they share the same seeded stream. Call them with no argument to use the global `Random.Default`, which is *not* reproducible.

Running it:

```
$ kotlin run
33
10
0.9049568172356872
green
[yellow, blue, green, red]
```

[← Prev](63-date-time.md) | [Index](../README.md) | [Next →](65-command-line-args.md)
