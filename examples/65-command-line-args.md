# 65. Command-Line Arguments

When `main` declares an `args: Array<String>` parameter, the runtime fills it with the words you pass on the command line (after `--` when launching with `kotlin run`). Everything arrives as a `String`, so you convert and validate yourself.

```kotlin
fun main(args: Array<String>) {
    if (args.isEmpty()) {
        println("Usage: greet <name> [age] [--loud]")
        return
    }

    val loud = "--loud" in args                       // simple flag check
    val positional = args.filterNot { it.startsWith("--") }

    val name = positional[0]
    val age = positional.getOrNull(1)?.toIntOrNull()  // optional, safely parsed

    var greeting = "Hello, $name!"
    if (age != null) greeting += " You are $age."
    if (loud) greeting = greeting.uppercase()

    println(greeting)
    println("received ${args.size} argument(s)")
}
```

Separating flags from positional arguments keeps simple CLIs readable. For anything richer (subcommands, typed options) reach for a library such as `kotlinx-cli` or clikt.

Running it:

```
$ kotlin run -- Alice 42
Hello, Alice! You are 42.
received 2 argument(s)
```

[← Prev](64-random.md) | [Index](../README.md) | [Next →](66-dsl.md)
