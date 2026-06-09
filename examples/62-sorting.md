# 62. Sorting & Comparators

The collection extensions `sorted` and `sortedDescending` work on anything `Comparable`. The result is a new list; the original is left untouched.

```kotlin
fun main() {
    val nums = listOf(3, 1, 4, 1, 5, 9, 2)
    println(nums.sorted())
    println(nums.sortedDescending())
}
```

To sort objects, pick a key with `sortedBy` / `sortedByDescending`. For multi-level ordering, build a `Comparator` with `compareBy { }.thenBy { }`, then pass it to `sortedWith`. You can also write a `Comparator` by hand for fully custom logic.

```kotlin
data class Person(val name: String, val age: Int)

fun main() {
    val people = listOf(
        Person("Bob", 30),
        Person("Alice", 30),
        Person("Carol", 25),
    )

    println(people.sortedBy { it.age })            // youngest first
    println(people.sortedByDescending { it.age })  // oldest first

    // age ascending, ties broken by name ascending
    val byAgeThenName = people.sortedWith(compareBy<Person> { it.age }.thenBy { it.name })
    println(byAgeThenName)

    // custom comparator: by name length
    val byNameLength = Comparator<Person> { a, b -> a.name.length - b.name.length }
    println(people.sortedWith(byNameLength))
}
```

Running it:

```
$ kotlin run
[1, 1, 2, 3, 4, 5, 9]
[9, 5, 4, 3, 2, 1, 1]
[Person(name=Carol, age=25), Person(name=Bob, age=30), Person(name=Alice, age=30)]
[Person(name=Bob, age=30), Person(name=Alice, age=30), Person(name=Carol, age=25)]
[Person(name=Carol, age=25), Person(name=Alice, age=30), Person(name=Bob, age=30)]
[Person(name=Bob, age=30), Person(name=Alice, age=30), Person(name=Carol, age=25)]
```

[← Prev](61-string-formatting.md) | [Index](../README.md) | [Next →](63-date-time.md)
