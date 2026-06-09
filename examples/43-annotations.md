# 43. Annotations

You declare an annotation with `annotation class`. Meta-annotations like `@Target` and `@Retention` control where it may be applied and whether it survives to runtime.

```kotlin
@Target(AnnotationTarget.PROPERTY, AnnotationTarget.CLASS)
@Retention(AnnotationRetention.RUNTIME)
annotation class Json(val name: String)

@Json("user")
data class User(
    @Json("full_name") val name: String,
    val age: Int
)

fun main() {
    val user = User("Alice", 30)
    println(user)
    // the @Json annotations describe how to serialize this class;
    // reading them at runtime is shown in the Reflection example
}
```

`@Target` restricts `Json` to classes and properties, and `@Retention(RUNTIME)` keeps it readable by reflection. Applying an annotation is just attaching metadata — it doesn't change behaviour on its own.

Running it:

```
$ kotlin run
User(name=Alice, age=30)
```

[← Prev](42-operator-overloading.md) | [Index](../README.md) | [Next →](44-reflection.md)
