# 48. Property Delegation

A property can hand off its `get`/`set` logic to a delegate object with the `by` keyword. The standard library ships several ready-made delegates: `lazy` for deferred initialization, `Delegates.observable` for change notifications, and even a `Map` for dynamic lookups.

```kotlin
import kotlin.properties.Delegates

class Settings(map: Map<String, Any?>) {
    // Delegate properties to a map: lookups go through map["name"].
    val theme: String by map
    val fontSize: Int by map
}

fun main() {
    // lazy: the initializer runs once, on first access.
    val config: String by lazy {
        println("computing config...")
        "loaded"
    }
    println("before first access")
    println(config)   // triggers the initializer
    println(config)   // cached, no recompute

    // observable: a callback fires on every assignment.
    var status: String by Delegates.observable("idle") { _, old, new ->
        println("status: $old -> $new")
    }
    status = "running"
    status = "done"

    // delegating to a map.
    val settings = Settings(mapOf("theme" to "dark", "fontSize" to 14))
    println("${settings.theme}, ${settings.fontSize}")
}
```

Note the order in the output: `"computing config..."` appears only after `"before first access"` and prints just once, even though `config` is read twice — `lazy` computes on first access and caches the result.

Running it:

```
$ kotlin run
before first access
computing config...
loaded
loaded
status: idle -> running
status: running -> done
dark, 14
```

[← Prev](47-class-delegation.md) | [Index](../README.md) | [Next →](49-inline-functions.md)
