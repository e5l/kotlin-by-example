# 22. Maps

A `Map` stores key/value pairs. Build one with `mapOf` and the `to` infix function, then look values up by key.

```kotlin
fun main() {
    val ages = mapOf("Alice" to 30, "Bob" to 25)

    println(ages["Alice"])                 // returns Int?, null if absent
    println(ages["Carol"])
    println(ages.getOrDefault("Carol", 0)) // fallback for a missing key
    println(ages.getValue("Bob"))          // non-null, throws if absent

    for ((name, age) in ages) {            // destructure each entry
        println("$name is $age")
    }

    val scores = mutableMapOf<String, Int>()
    scores["math"] = 90                    // index assignment
    scores.put("science", 85)
    println(scores)
}
```

Indexing with `map["key"]` returns a nullable value, so use it when a key might be missing. Prefer `getValue` when the key is guaranteed to exist and `getOrDefault` when you want a fallback.

Running it:

```
$ kotlin run
30
null
0
25
Alice is 30
Bob is 25
{math=90, science=85}
```

[← Prev](21-sets.md) | [Index](../README.md) | [Next →](23-collection-ops.md)
