# Kotlin by Example

Kotlin by Example is a hands-on introduction to Kotlin via annotated example programs. It is inspired by [Go by Example](https://gobyexample.com) and [zig-by-example](https://github.com/boringcollege/zig-by-example): read the code, read the notes, run it yourself.

Kotlin is a concise, statically-typed language for the JVM (also Native, JS, and Wasm). It emphasizes null safety, conciseness, and seamless Java interop, letting you write expressive code that runs anywhere the JVM does and beyond.

## Getting started

The examples are run with the [Kotlin toolchain](https://kotlin-toolchain.org) and its `kotlin` command-line tool.

### 0. Install the toolchain

macOS / Linux:

```
curl -fsSL https://kotl.in/install.sh | sh
```

Windows (PowerShell):

```
powershell -ExecutionPolicy ByPass -c "irm 'https://kotl.in/install.ps1' | iex"
```

You can also `sdk install kotlintoolchain` via [SDKMAN](https://sdkman.io). Check it works with `kotlin --version`.

### 1. Create a scratch project

The `kotlin` tool runs *projects*, not loose `.kt` files. Set up one small project and reuse it for every example:

```
my-kotlin/
├─ module.yaml
└─ src/
   └─ main.kt
```

`module.yaml`:

```yaml
product: jvm/app
```

### 2. Run an example

Paste an example's code into `src/main.kt`, then run it from the project root:

```
$ kotlin run
Hello, World!
```

`kotlin run` also prints a couple of `INFO` compiler lines as it builds; add `--log-level=warn` (`kotlin --log-level=warn run`) to show only your program's output, as the examples below do. Pass command-line arguments after `--`, e.g. `kotlin run -- Alice 42`.

### 3. Add dependencies when needed

A few examples (coroutines, serialization, reflection, testing) need extra libraries. Declare them in `module.yaml`:

```yaml
product: jvm/app

dependencies:
  - org.jetbrains.kotlinx:kotlinx-coroutines-core:1.10.2
```

Each example notes which dependency it requires. See the [Kotlin toolchain tutorial](https://kotlin-toolchain.org/latest/getting-started/tutorial/) for more.

## Examples

### Basics

1. [Hello World](examples/01-hello-world.md)
2. [Values](examples/02-values.md)
3. [Variables](examples/03-variables.md)
4. [Basic Types & Numbers](examples/04-basic-types.md)
5. [Type Checks & Casts](examples/05-type-checks-casts.md)
6. [Strings & Templates](examples/06-strings.md)
7. [Null Safety](examples/07-null-safety.md)
8. [Equality](examples/08-equality.md)

### Control Flow

9. [If & When](examples/09-if-when.md)
10. [Ranges & Progressions](examples/10-ranges.md)
11. [Loops & Labels](examples/11-loops.md)
12. [Functions](examples/12-functions.md)
13. [Default & Named Arguments](examples/13-default-named-args.md)
14. [Varargs](examples/14-varargs.md)
15. [Infix Functions](examples/15-infix-functions.md)
16. [Recursion & tailrec](examples/16-recursion.md)
17. [Lambdas & Higher-Order Functions](examples/17-lambdas.md)
18. [Closures](examples/18-closures.md)

### Collections

19. [Arrays](examples/19-arrays.md)
20. [Lists](examples/20-lists.md)
21. [Sets](examples/21-sets.md)
22. [Maps](examples/22-maps.md)
23. [Collection Operations](examples/23-collection-ops.md)
24. [Grouping & Aggregation](examples/24-grouping-aggregation.md)
25. [Sequences](examples/25-sequences.md)

### Types & OOP

26. [Classes & Constructors](examples/26-classes.md)
27. [Properties & Accessors](examples/27-properties.md)
28. [Inheritance & Overriding](examples/28-inheritance.md)
29. [Abstract Classes](examples/29-abstract-classes.md)
30. [Interfaces](examples/30-interfaces.md)
31. [Visibility Modifiers](examples/31-visibility.md)
32. [Data Classes](examples/32-data-classes.md)
33. [Enum Classes](examples/33-enum-classes.md)
34. [Sealed Classes & Interfaces](examples/34-sealed-classes.md)
35. [Objects & Companion Objects](examples/35-objects.md)
36. [Nested & Inner Classes](examples/36-nested-inner-classes.md)
37. [Extension Functions & Properties](examples/37-extensions.md)
38. [Generics & Variance](examples/38-generics.md)
39. [Reified Type Parameters](examples/39-reified.md)
40. [Type Aliases](examples/40-type-aliases.md)
41. [Inline Value Classes](examples/41-value-classes.md)
42. [Operator Overloading](examples/42-operator-overloading.md)
43. [Annotations](examples/43-annotations.md)
44. [Reflection](examples/44-reflection.md)

### Functional & Advanced

45. [Scope Functions](examples/45-scope-functions.md)
46. [Destructuring Declarations](examples/46-destructuring.md)
47. [Class Delegation](examples/47-class-delegation.md)
48. [Property Delegation](examples/48-property-delegation.md)
49. [Inline Functions](examples/49-inline-functions.md)
50. [Exceptions](examples/50-exceptions.md)
51. [Result & runCatching](examples/51-result-runcatching.md)

### Concurrency

52. [Coroutines Basics](examples/52-coroutines-basics.md)
53. [Suspending Functions](examples/53-suspending-functions.md)
54. [async/await & Structured Concurrency](examples/54-async-await.md)
55. [Dispatchers & Context](examples/55-dispatchers-context.md)
56. [Channels](examples/56-channels.md)
57. [Flows](examples/57-flows.md)

### Practicals

58. [Reading & Writing Files](examples/58-files.md)
59. [JSON Serialization](examples/59-json.md)
60. [Regular Expressions](examples/60-regex.md)
61. [String Formatting](examples/61-string-formatting.md)
62. [Sorting & Comparators](examples/62-sorting.md)
63. [Date & Time](examples/63-date-time.md)
64. [Random](examples/64-random.md)
65. [Command-Line Arguments](examples/65-command-line-args.md)
66. [Building a Type-Safe DSL](examples/66-dsl.md)
67. [Testing](examples/67-testing.md)

## Resources

- [Kotlin docs](https://kotlinlang.org/docs/home.html)
- [Kotlin Playground](https://play.kotlinlang.org)
- [Kotlin Koans](https://play.kotlinlang.org/koans)
- [Standard library reference](https://kotlinlang.org/api/latest/jvm/stdlib/)

## License

Released under [CC BY 4.0](LICENSE).
