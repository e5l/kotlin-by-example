# 58. Reading & Writing Files

Kotlin's standard library adds convenient extensions to `java.io.File` for whole-file I/O. We use a temporary file here so the example is self-contained.

```kotlin
import java.io.File

fun main() {
    val file = File.createTempFile("notes", ".txt")
    file.deleteOnExit()

    file.writeText("first line\nsecond line\nthird line\n")  // overwrites contents

    val content = file.readText()      // whole file as one String
    print(content)

    val lines = file.readLines()       // file as a List<String>
    println("line count: ${lines.size}")

    file.forEachLine { line ->         // stream line-by-line, no full buffering
        println("> $line")
    }
}
```

For large files or when you need fine control, open a reader and wrap it in `use { }`. The `use` function closes the resource automatically, even if an exception is thrown — Kotlin's equivalent of try-with-resources.

```kotlin
file.bufferedReader().use { reader ->
    println("first via buffered: ${reader.readLine()}")
}
```

Running it:

```
$ kotlin run
first line
second line
third line
line count: 3
> first line
> second line
> third line
first via buffered: first line
```

[← Prev](57-flows.md) | [Index](../README.md) | [Next →](59-json.md)
