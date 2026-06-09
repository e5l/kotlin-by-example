# 66. Building a Type-Safe DSL

A *lambda with receiver*, typed `T.() -> Unit`, lets you call a builder's methods directly inside a `{ }` block, as if you were writing in that object's scope. This is the foundation of Kotlin's type-safe DSLs, like the HTML builder below.

```kotlin
class Paragraph(val text: String) {
    override fun toString() = "<p>$text</p>"
}

class Body {
    private val paragraphs = mutableListOf<Paragraph>()
    fun p(text: String) {            // available inside body { }
        paragraphs += Paragraph(text)
    }
    override fun toString() = "<body>${paragraphs.joinToString("")}</body>"
}

class Html {
    private var body: Body? = null
    fun body(init: Body.() -> Unit) {   // receiver lambda
        body = Body().apply(init)       // run the block on a fresh Body
    }
    override fun toString() = "<html>${body ?: ""}</html>"
}

fun html(init: Html.() -> Unit): Html = Html().apply(init)
```

Each builder function takes a receiver lambda and runs it with `apply`, which returns the configured object. The result reads like markup, yet the compiler checks every call — `p` only resolves inside a `body { }` block.

```kotlin
fun main() {
    val page = html {
        body {
            p("Hello")
            p("World")
        }
    }
    println(page)
}
```

Running it:

```
$ kotlin run
<html><body><p>Hello</p><p>World</p></body></html>
```

[← Prev](65-command-line-args.md) | [Index](../README.md) | [Next →](67-testing.md)
