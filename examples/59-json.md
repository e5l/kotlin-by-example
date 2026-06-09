# 59. JSON Serialization

The official `kotlinx.serialization` library turns Kotlin objects into JSON and back, with no reflection at runtime. It needs the `org.jetbrains.kotlinx:kotlinx-serialization-json` runtime dependency and the serialization compiler plugin (enable it under `settings: { kotlin: { serialization: enabled } }` in `module.yaml`), which generates serializers for classes you mark `@Serializable`.

```kotlin
import kotlinx.serialization.Serializable
import kotlinx.serialization.json.Json
import kotlinx.serialization.encodeToString

@Serializable
data class User(val name: String, val age: Int, val admin: Boolean)

fun main() {
    val user = User("Alice", 30, admin = true)

    val json = Json.encodeToString(user)   // object -> JSON text
    println(json)

    val decoded = Json.decodeFromString<User>(json)  // JSON text -> object
    println(decoded)
}
```

`encodeToString` relies on the generated serializer rather than reflection, so it works the same on the JVM, JS, and Native. The default `Json` instance emits compact output; configure formatting with `Json { prettyPrint = true }` if you want indentation.

Running it:

```
$ kotlin run
{"name":"Alice","age":30,"admin":true}
User(name=Alice, age=30, admin=true)
```

[← Prev](58-files.md) | [Index](../README.md) | [Next →](60-regex.md)
