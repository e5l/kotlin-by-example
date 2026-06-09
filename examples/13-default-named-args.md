# 13. Default & Named Arguments

Parameters can have default values, so callers may omit them. Named arguments let you pass values by name, in any order, and make calls self-documenting.

```kotlin
fun connect(host: String = "localhost", port: Int = 8080, secure: Boolean = false): String =
    "${if (secure) "https" else "http"}://$host:$port"

fun main() {
    // all defaults
    println(connect())

    // override some positionally
    println(connect("example.com", 443))

    // named arguments, including out-of-order
    println(connect(secure = true, host = "example.com"))
}
```

Running it:

```
$ kotlin run
http://localhost:8080
http://example.com:443
https://example.com:8080
```

[← Prev](12-functions.md) | [Index](../README.md) | [Next →](14-varargs.md)
